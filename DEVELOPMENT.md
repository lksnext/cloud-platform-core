# Development Guide

This guide covers everything you need to set up your local development environment for Cloud
Platform Core.

---

## Prerequisites

Before you start, make sure you have the following installed:

| Tool          | Purpose                                | Install                                                                                |
| ------------- | -------------------------------------- | -------------------------------------------------------------------------------------- |
| **nvm**       | Node.js version manager                | [github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)                                 |
| **Node.js**   | Runtime (via nvm, see below)           | Managed by nvm                                                                         |
| **Git**       | Version control                        | [git-scm.com](https://git-scm.com)                                                     |
| **Terraform** | Required for `azure-terraform` package | [developer.hashicorp.com/terraform](https://developer.hashicorp.com/terraform/install) |

---

## 1. Install Node.js via nvm

This project uses **Node.js 22 LTS**. A `.nvmrc` file is included to pin the version automatically.

```bash
# Install nvm (if not already installed)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash

# Restart your shell or source your profile
source ~/.bashrc  # or ~/.zshrc

# Install and use the project's Node version
nvm install
nvm use
```

Running `nvm use` in the project directory will automatically pick up the version from `.nvmrc`.

---

## 2. Clone and Install

```bash
git clone git@github.com:lksnext/cloud-platform-core.git
cd cloud-platform-core

npm install
```

`npm install` will also run `husky` via the `prepare` script, setting up the git hooks
automatically.

---

## 3. Configure Commit Signing

All commits to this project must be **signed**. We use SSH signing (recommended) as it works with
your existing GitHub SSH key.

### SSH Signing (recommended)

```bash
# Configure git to use SSH for signing
git config --global gpg.format ssh

# Point to your SSH public key (adjust path if using ed25519)
git config --global user.signingkey ~/.ssh/id_rsa.pub
# or for ed25519:
# git config --global user.signingkey ~/.ssh/id_ed25519.pub

# Enable automatic signing on every commit
git config --global commit.gpgsign true
```

Then add the same public key to GitHub as a **signing key**:

1. Go to **GitHub → Settings → SSH and GPG keys**
2. Click **New signing key**
3. Paste the output of `cat ~/.ssh/id_rsa.pub` (or your key path)
4. Save

> Note: This is separate from your authentication SSH key — both can coexist in GitHub.

### GPG Signing (alternative)

```bash
# Generate a GPG key (if you don't have one)
gpg --full-generate-key

# List your keys to get the key ID
gpg --list-secret-keys --keyid-format=long

# Configure git
git config --global user.signingkey <YOUR_KEY_ID>
git config --global commit.gpgsign true

# Export and add to GitHub → Settings → SSH and GPG keys → New GPG key
gpg --armor --export <YOUR_KEY_ID>
```

---

## 4. Available Scripts

| Script       | Command                | Description                                   |
| ------------ | ---------------------- | --------------------------------------------- |
| Format       | `npm run format`       | Format all files with Prettier                |
| Format check | `npm run format:check` | Check formatting without modifying files (CI) |
| Spellcheck   | `npm run spellcheck`   | Run cspell across all source files            |

---

## 5. Git Hooks

The following hooks run automatically via [Husky](https://typicode.github.io/husky):

| Hook         | Trigger            | What it does                                                         |
| ------------ | ------------------ | -------------------------------------------------------------------- |
| `commit-msg` | Every `git commit` | Validates commit message format via `commitlint`                     |
| `pre-commit` | Every `git commit` | Formats staged files with Prettier and spell-checks them with cspell |

### Commit Message Format

This project enforces [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>: <description>

Examples:
  feat: add Azure naming module
  fix: correct S3 bucket normalization
  docs: update development guide
  chore: update dependencies
  refactor: simplify naming renderer
```

Allowed types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `build`, `ci`, `chore`, `perf`,
`revert`.

---

## 6. Adding Custom Words to Spell Check

If cspell flags a valid project-specific term, add it to:

```
.cspell/project-words.txt
```

One word per line. Commit the change alongside the file that introduced the word.

---

## 7. Versioning and Changesets

This project uses [Changesets](https://github.com/changesets/changesets) for versioning.

When your change affects a package's public behavior, add a changeset before opening a PR:

```bash
npx changeset
```

Follow the prompts to select the affected packages and bump type (`patch`, `minor`, `major`).

---

## Questions?

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the full contribution process, or open a
[GitHub Discussion](https://github.com/lksnext/cloud-platform-core/discussions).
