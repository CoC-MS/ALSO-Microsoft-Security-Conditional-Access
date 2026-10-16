# 🛡️ ALSO Microsoft Security - Conditional Access

> Microsoft Entra Conditional Access policy exports and supporting groups and named locations, helping organizations accelerate secure deployments and apply Zero Trust principles.

> [!IMPORTANT]
> These exports are starting points, not ready-made tenant configurations. Review licensing, settings, tenant-specific references, dependencies, assignments, and exclusions. **Import Conditional Access policies in OFF state** and pilot reviewed policies before enabling them.

<a id="getting-started"></a>
## 🚀 Getting started

1. Review [General prerequisites](docs/public/general-prerequisites.md), [Conditional Access prerequisites](docs/public/conditional-access-prerequisites.md), [Dependencies and import errors](docs/public/dependencies-and-import-errors.md), and [Security information](https://github.com/CoC-MS/ALSO-Microsoft-Security-Conditional-Access/security). Choose exactly one package using the licensing guide below: [`ALSO_CA_BP`](ALSO_CA_BP), [`ALSO_CA_E5`](ALSO_CA_E5), or [`ALSO_CA_E7`](ALSO_CA_E7).
2. Follow [How to import](docs/public/how-to-import.md) for extraction and import guidance.

### Quick navigation

| Section | What you will find |
| --- | --- |
| [Getting started](#getting-started) | Prerequisites, package selection, and import guidance. |
| [Conditional Access licensing guide](#conditional-access-licensing-guide) | License compatibility and limitations. |
| [Conditional Access packages](#conditional-access-packages) | Compare package contents. |
| [Conditional Access coverage](#conditional-access-coverage) | Policy coverage and capabilities. |
| [Documentation](#documentation) | Links to supporting guides and the repository licence. |

---

<a id="conditional-access-licensing-guide"></a>
## Conditional Access licensing guide

Choose the single package that matches the tenant's licensing. The packages are cumulative: E5 includes BP policies, and E7 includes BP, E5, and Agent 365 policies.

### ✅ `ALSO_CA_E7` — full experience

Use [`ALSO_CA_E7`](ALSO_CA_E7) when the tenant is licensed for all policies, including Agent 365.

| License | Experience |
| --- | --- |
| Microsoft 365 E7 | ✅ Full support |
| Microsoft 365 E5 + Agent 365 | ✅ Full support |
| Microsoft 365 E3 + Defender Suite + Purview Suite + Agent 365 | ✅ Full support |
| Business Premium + Defender Suite + Purview Suite + Agent 365 | ✅ Full support |
| Microsoft 365 F3 + Defender Suite + Purview Suite + Agent 365 | ✅ Full support |
| Microsoft 365 F1 + Defender Suite + Purview Suite + Agent 365 | ✅ Full support |

### ⚠️ `ALSO_CA_E5` — Limited experience- without Agent 365 policies

Use [`ALSO_CA_E5`](ALSO_CA_E5) for all standard BP and E5 Conditional Access policies, excluding policies tagged `A365`.

| License | Experience |
| --- | --- |
| Microsoft 365 E5 | ⚠️ Supports all policies except A365 |
| Microsoft 365 E3 + Defender Suite and/or Purview Suite | ⚠️ Supports all policies except A365 |
| Business Premium + Defender Suite and/or Purview Suite | ⚠️ Supports all policies except A365 |
| Microsoft 365 F3 + Defender Suite and/or Purview Suite | ⚠️ Supports all policies except A365 |
| Microsoft 365 F1 + Defender Suite and/or Purview Suite | ⚠️ Supports all policies except A365 |

### ⚠️ `ALSO_CA_BP` — Limited experience- excludes A365 and E5 policies

Use [`ALSO_CA_BP`](ALSO_CA_BP) for baseline Conditional Access policies. This package excludes policies tagged `E5` and `A365`.

| License | Experience |
| --- | --- |
| Microsoft 365 E3 | ⚠️ Limited experience Excludes A365 and E5 policies |
| Microsoft 365 Business Premium | ⚠️ Limited experience Excludes A365 and E5 policies |
| Microsoft 365 F3 | ⚠️ Limited experience Excludes A365 and E5 policies |
| Microsoft 365 F1 | ⚠️ Limited experience Excludes A365 and E5 policies |

<a id="conditional-access-packages"></a>
## 📦 Conditional Access packages  

Each folder is a complete export package with Conditional Access policies, supporting groups, named locations, and `MigrationTable.json`. The E5 and E7 packages also include the `ALSO-Tier0 Admins` authentication context required by CA106.

| Package | Policy scope | Policies | Groups | Named locations | Authentication contexts | Total JSON files |
| --- | --- | ---: | ---: | ---: | ---: | ---: |
| [`ALSO_CA_BP`](ALSO_CA_BP) | 34 BP | 34 | 36 | 3 | 0 | 74 |
| [`ALSO_CA_E5`](ALSO_CA_E5) | 34 BP + 3 E5 | 37 | 40 | 3 | 1 | 82 |
| [`ALSO_CA_E7`](ALSO_CA_E7) | 34 BP + 3 E5 + 5 A365 | 42 | 40 | 3 | 1 | 87 |

> [!WARNING]
> Choose **one** package per tenant. Do not combine packages; cumulative packages contain the lower-tier policies and supporting resources. Review every selected object and dependency before import.

<a id="conditional-access-coverage"></a>
## 🌐 Conditional Access coverage

| Persona | Policy series | Included scenarios |
| --- | --- | --- |
| 🌐 **Global** | CA000-CA006 | MFA, country restrictions, legacy authentication, device registration, authentication flows, and unmanaged Microsoft 365 access. |
| 👑 **Admins / Tier 0** | CA100-CA110 | MFA, phishing-resistant authentication, session controls, device compliance, platform restrictions, and authentication context. |
| 👤 **Internals** | CA200-CA211 | MFA, risk-based blocking, session controls, enrollment, platform restrictions, device compliance, and application restrictions. |
| ⚙️ **Service accounts** | CA300-CA301 | MFA and country restrictions for user-based service accounts, not service principals. |
| 🤝 **Guest users** | CA400-CA404 | MFA, application restrictions, sign-in frequency, and browser persistence. |
| 🤖 **Agents** | CA501-CA505 | Agent identity risk, agent resource restrictions, compliant devices, and compliant network access. |

### ✨ Notable capabilities

- **Stronger administrator authentication:** Phishing-resistant MFA and Tier 0 controls; prepare authentication methods and PIM configuration separately.
- **Risk-based access:** E5-tagged user/sign-in risk policies and A365-tagged agent risk policies; confirm licensing and service readiness.
- **Managed and unmanaged access:** Device-compliance requirements and application-enforced restrictions; configure the corresponding Intune and application-side controls first.
- **Location and session controls:** Country restrictions, strict-location Continuous Access Evaluation (CAE), sign-in frequency, and browser persistence.

> [!WARNING]
> Policy names describe intent, but settings determine behavior. Read the [policy guide](docs/public/conditional-access-policies.md) and inspect the JSON before use.

---

<a id="documentation"></a>
## 📚 Documentation

| Resource | Description |
| --- | --- |
| 🔐 **[Policy guide](docs/public/conditional-access-policies.md)** | Review policies by persona and their deployment caveats. |
| 🚀 **[General prerequisites](docs/public/general-prerequisites.md)** | Check licensing, permissions, and deployment preparation. |
| 🛡️ **[Conditional Access prerequisites](docs/public/conditional-access-prerequisites.md)** | Prepare exclusions, locations, compliance, authentication, and agent dependencies. |
| 🧩 **[Dependencies and import errors](docs/public/dependencies-and-import-errors.md)** | Review required tenant objects, representative Graph errors, and CA203 service-principal registration. |
| 📖 **[Policy naming](docs/public/policy-naming.md)** | Understand licence tags, policy numbers, and personas. |
| 📂 **[File structure](docs/public/file-structure.md)** | Compare packages and find policy exports and supporting resources. |
| 📥 **[How to import](docs/public/how-to-import.md)** | Import one reviewed package, then validate in Entra. |
| 🐛 **[Reporting issues](docs/public/reporting-issues.md)** | Report problems without disclosing tenant information. |
| 🛡️ **[Security information](Security.md)** | Read deployment responsibilities and the usage notice. |
| 📜 **[License](LICENSE)** | Read the repository licence. |
