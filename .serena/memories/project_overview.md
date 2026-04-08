# cloud-platform-core — Project Overview

## Purpose
Foundational monorepo providing standardized naming, conventions, and reusable building blocks for multi-cloud infrastructure across AWS and Azure.

## Packages
- `packages/aws-cdk` → npm/TypeScript CDK constructs (`@lksnext/aws-cdk`, public)
- `packages/azure-terraform` → Terraform modules (`@lksnext/azure-terraform`, private — not published to npm)

## Tech Stack
- Node.js monorepo (npm workspaces)
- TypeScript (aws-cdk package)
- Terraform (azure-terraform package)
- `@changesets/cli` for versioning and CHANGELOG generation per package
- SDD (Spec Driven Development) via `.sdd/` + `.github/prompts/`

## Key Config Files
- Root `package.json`: workspace root (private), defines `workspaces: ["packages/*"]`
- `.changeset/config.json`: changesets config, writes changelogs to `packages/*/CHANGELOG.md`
- Root `CHANGELOG.md`: maintained manually

## Repository
https://github.com/lksnext/cloud-platform-core
