# Cloud Platform Core

**Cloud Platform Core** is a foundational multi-cloud library that provides standardized naming, conventions, and reusable building blocks for infrastructure across AWS and Azure.

The project aims to improve consistency, governance, and developer experience in cloud platform development, supporting both **AWS CDK (TypeScript)** and **Terraform (Azure)**.

---

## 🚀 Overview

Cloud Platform Core defines a unified approach to:

* Resource naming conventions
* Infrastructure patterns
* Cross-cloud consistency
* Platform-level governance

It is designed for:

* Platform engineering teams
* Multi-cloud environments
* SaaS architectures (single-tenant and multi-tenant)
* Enterprise-scale infrastructure

---

## 🧱 Repository Structure

```text
cloud-platform-core/
  packages/
    aws-cdk/            # AWS CDK (TypeScript) constructs (@lksnext/aws-cdk)
    azure-terraform/    # Terraform modules for Azure (@lksnext/azure-terraform)

  .changeset/           # Changesets for versioning and changelog generation
  .github/              # Templates, workflows, and automation
```

---

## 🔑 Key Concepts

### Naming Specification

The project defines a consistent naming model across cloud providers, covering:

* Environment (`dev`, `prod`, etc.)
* Scope (`shared`, `wl`, etc.)
* Application / domain
* Region
* Resource type
* Purpose

---

### Multi-Cloud Support

| Cloud | Technology       |
| ----- | ---------------- |
| AWS   | CDK (TypeScript) |
| Azure | Terraform        |

The goal is to provide a **consistent developer experience across both ecosystems**.

---

### Governance

Certain parts of the project are governed more strictly:

* Cloud implementations → **moderate governance**

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the full governance model.

---

## 📦 Usage

### AWS CDK

```bash
npm install @lksnext/aws-cdk
```

```ts
import { AwsNamer } from '@lksnext/aws-cdk';
```

---

### Terraform (Azure)

```hcl
module "naming" {
  source = "git::https://github.com/lksnext/cloud-platform-core.git//packages/azure-terraform/modules/naming?ref=v1.0.0"
}
```

---

## 🧪 Status

⚠️ This project is in an early stage.

* APIs may change
* Feedback and contributions are welcome

---

## 🤝 Contributing

We welcome contributions from the community.

Please read:

* [CONTRIBUTING.md](./CONTRIBUTING.md)
* [Code of Conduct](./CODE_OF_CONDUCT.md)

For significant changes (especially naming), please open an issue first.

---

## 🔄 Versioning

This project follows:

* [Semantic Versioning (SemVer)](https://semver.org/)
* [Changesets](https://github.com/changesets/changesets) for versioning and changelogs

---

## 🔐 Security

If you discover a security issue, please report it according to:

* [SECURITY.md](./SECURITY.md)

---

## 📄 License

This project is licensed under the **Apache License 2.0**.

See [LICENSE](./LICENSE) for details.

---

## 🏢 Maintained by

LKS Next

---

## 🌍 Why This Project

Cloud Platform Core was created to address common challenges in cloud environments:

* Inconsistent naming across teams and platforms
* Lack of standardization in infrastructure
* Difficulty managing multi-cloud architectures
* Poor developer experience in IaC

This project provides a **shared foundation** to solve these problems.

---

## 🙌 Acknowledgements

Thanks to all contributors and teams helping to improve cloud platform consistency.
