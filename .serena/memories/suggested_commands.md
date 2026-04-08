# Suggested Commands

## Install dependencies
```bash
npm install
```

## Add a changeset (before committing a releasable change)
```bash
npx changeset
```

## Apply changesets (bump versions + write CHANGELOGs)
```bash
npx changeset version
```

## Publish (npm packages only; private packages skipped automatically)
```bash
npx changeset publish
```

## Verify commitlint manually
```bash
echo "feat: my message" | npx commitlint
```

## Git hooks
- `commit-msg` → runs commitlint automatically via husky
- Hooks are installed on `npm install` via the `prepare` script
