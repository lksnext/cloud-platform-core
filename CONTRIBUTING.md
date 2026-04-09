# Contributing to Cloud Platform Core

First of all, thank you for your interest in contributing! 🎉 Cloud Platform Core is an open-source
project aimed at standardizing naming, conventions, and reusable infrastructure patterns across AWS
and Azure.

We welcome contributions from everyone.

---

## 📌 Ways to Contribute

You can contribute in several ways:

- 🐛 Reporting bugs
- 💡 Proposing new features or improvements
- 📖 Improving documentation
- 🧱 Adding or improving modules (CDK / Terraform)
- 🔍 Reviewing pull requests

---

## 🧭 Before You Start

Before opening a PR, please:

1. Check existing issues and discussions
2. Open an issue if the change is significant
3. Align with the current naming model and conventions
4. Ensure your proposal fits the project scope

---

## 🏗️ Project Structure

```text
packages/
  aws-cdk/          # AWS CDK constructs (@lksnext/aws-cdk, npm)
  azure-terraform/  # Azure Terraform modules (@lksnext/azure-terraform, private)

.github/
.changeset/
```

- `packages/aws-cdk/` → reusable AWS CDK constructs, published to npm
- `packages/azure-terraform/` → reusable Azure Terraform modules, not published to npm

---

## 🔑 Naming Changes (Important)

Changes to the naming model are **high impact** and must follow a stricter process.

If your contribution affects naming:

1. Open an issue describing the change
2. Provide rationale and examples
3. Consider backward compatibility
4. Expect additional review from maintainers

---

## 🔄 Development Workflow

1. Fork the repository
2. Create a branch:

```bash
git checkout -b feature/my-change
```

3. Make your changes
4. Add tests if applicable
5. Commit using [Conventional Commits](https://www.conventionalcommits.org/) (enforced by
   `commitlint`)
6. Create a changeset:

```bash
npx changeset
```

7. Push and open a Pull Request

---

## 🧪 Testing & Quality

- Ensure existing tests pass
- Add new tests when introducing logic changes
- Keep changes minimal and focused

---

## 📝 Commit Guidelines

This project **enforces** [Conventional Commits](https://www.conventionalcommits.org/) via
`commitlint`. Non-conforming commits will be rejected by the `commit-msg` hook.

```text
feat: add tenant-aware naming
fix: correct S3 bucket normalization
docs: update naming RFC examples
chore: update dependencies
```

---

## 📦 Versioning & Releases

This project uses:

- **Semantic Versioning (SemVer)**
- **Changesets** for versioning and changelog generation

Every PR affecting behavior should include a changeset.

---

## 🔍 Pull Request Process

- Ensure your PR is focused and well described
- Link related issues
- Include examples where relevant
- Update documentation if needed
- Pass all CI checks

PRs will be reviewed by code owners.

---

## 🧑‍⚖️ Governance

Some areas of the project require stricter governance:

| Area            | Governance Level |
| --------------- | ---------------- |
| aws-cdk         | Medium           |
| azure-terraform | Medium           |

Maintainers may request changes or reject proposals that do not align with the project direction.

---

## 🤝 Code of Conduct

By participating in this project, you agree to abide by our [Code of Conduct](./CODE_OF_CONDUCT.md).

---

## ❓ Questions & Discussions

If you’re unsure about something:

- Open a GitHub Discussion
- Or create an issue

We prefer early alignment over rework.

---

## 🚀 Thank You

Your contributions help improve consistency and quality across cloud platforms.

We appreciate your time and effort 🙌
