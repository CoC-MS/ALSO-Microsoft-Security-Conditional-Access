# 🛡️ ALSO Microsoft Security - Conditional Access

> Microsoft Entra Conditional Access policy exports and supporting groups, named locations, and authentication context, helping organizations accelerate secure deployments and apply Zero Trust principles.

> [!NOTE]
> **Documentation preview:** The main `README.md` is unchanged. This page and `docs/public` demonstrate the Windows repository's documentation layout using Conditional Access content. See [Viewing and adopting the preview](docs/public/README.md#viewing-and-adopting-the-preview) for manual adoption instructions.

> [!IMPORTANT]
> These exports are starting points, not ready-made tenant configurations. Review licensing, settings, tenant-specific references, dependencies, and exclusions. **Import Conditional Access policies in OFF state** and pilot reviewed policies before expanding deployment.

| Resource | Description |
| --- | --- |
| 🔐 **[Policy guide](docs/public/conditional-access-policies.md)** | Review the 41 policies by persona and their deployment caveats. |
| 🚀 **[General prerequisites](docs/public/general-prerequisites.md)** | Check licensing, permissions, and deployment preparation. |
| 🛡️ **[Conditional Access prerequisites](docs/public/conditional-access-prerequisites.md)** | Prepare exclusions, locations, compliance, authentication, and agent dependencies. |
| 📖 **[Policy naming](docs/public/policy-naming.md)** | Understand licence tags, policy numbers, and personas. |
| 🏷️ **[Naming exceptions](docs/public/naming-exceptions.md)** | Review existing filename and setting mismatches without renaming exports. |
| 📂 **[File structure](docs/public/file-structure.md)** | Find policy exports and supporting resources. |
| 📥 **[How to import](docs/public/how-to-import.md)** | Import reviewed dependencies and policies, then validate in Entra. |
| 🐛 **[Reporting issues](docs/public/reporting-issues.md)** | Report problems without disclosing tenant information. |
| 🛡️ **[Security information](Security.md)** | Read deployment responsibilities and the usage notice. |
| 📜 **[License](LICENSE)** | Read the repository license. |

---

## 📦 Conditional Access resources

The exports live in a single [`ALSO_CA`](ALSO_CA) folder. Unlike the Windows repository, there are no Basic/Adv packages or build manifests. Select policies and their dependencies for your tenant rather than importing everything.

| Resource | JSON files | Purpose |
| --- | ---: | --- |
| [ConditionalAccess](ALSO_CA/ConditionalAccess) | 41 | 33 BP, 3 E5, and 5 A365 policies. |
| [Groups](ALSO_CA/Groups) | 40 | Persona groups and policy exclusions; review membership and duplicate-looking names. |
| [NamedLocations](ALSO_CA/NamedLocations) | 3 | Country locations and a compliant network location. |
| [AuthenticationContext](ALSO_CA/AuthenticationContext) | 1 | Tier 0 authentication context for CA106. |
| [MigrationTable.json](ALSO_CA/MigrationTable.json) | 1 | Source object mapping metadata, not a policy or a destination tenant configuration. |

Counts describe the current export snapshot, not licensed deployment bundles. Licence tags indicate the source classification; confirm entitlement for each selected feature.

## 🌐 Conditional Access coverage

| Persona | Policies | Included scenarios |
| --- | --- | --- |
| 🌐 **Global** | CA000-CA006 | MFA, country restrictions, legacy authentication, device registration, authentication flows, and unmanaged Microsoft 365 access. |
| 👑 **Admins / Tier 0** | CA100-CA110 | MFA, phishing-resistant authentication, session controls, device compliance, platform restrictions, and authentication context. |
| 👤 **Internals** | CA200-CA210 | MFA, risk-based blocking, session controls, enrollment, platform restrictions, device compliance, and application restrictions. |
| ⚙️ **Service accounts** | CA300-CA301 | MFA and country restrictions for user-based service accounts, not service principals. |
| 🤝 **Guest users** | CA400-CA404 | MFA, application restrictions, sign-in frequency, and browser persistence. |
| 🤖 **Agents** | CA501-CA505 | Agent identity risk, agent resource restrictions, compliant devices, and compliant network access. |

### ✨ Notable capabilities

- **Stronger administrator authentication:** Phishing-resistant MFA and a Tier 0 authentication context; prepare authentication methods and PIM configuration separately.
- **Risk-based access:** E5-tagged user/sign-in risk policies and A365-tagged agent risk policies; confirm licensing and service readiness.
- **Managed and unmanaged access:** Device-compliance requirements and application-enforced restrictions; configure the corresponding Intune and application-side controls first.
- **Location and session controls:** Country restrictions, strict-location Continuous Access Evaluation (CAE), sign-in frequency, and browser persistence.

> [!WARNING]
> Policy names describe intent, but settings determine behavior. For example, CA104 currently targets `None`, CA203 targets Microsoft Intune rather than Intune Enrollment, and the global country location includes more than Norway. Read the [policy guide](docs/public/conditional-access-policies.md) before use. CA104 and CA209 require a controlled ON/OFF pilot rather than report-only evaluation for strict-location CAE.

---

## 🚀 Getting started

1. Review [General prerequisites](docs/public/general-prerequisites.md), [Conditional Access prerequisites](docs/public/conditional-access-prerequisites.md), and [Security information](Security.md).
2. Select policies using the [Policy guide](docs/public/conditional-access-policies.md) and identify dependencies using [File structure](docs/public/file-structure.md).
3. Follow [How to import](docs/public/how-to-import.md), keeping policies OFF until reviewed and ready for a controlled pilot.
