# ALSO Microsoft Security Conditional Access Policy Templates
 
A collection of Microsoft Entra Conditional Access policy templates designed by ALSO to help organizations accelerate secure deployments and implement Microsoft Security best practices.
 
---
 
## 📂 Repository Structure
 
Conditional Access templates are organized by the **minimum required license**.
 
```text
/
├── BP/
├── E5/
├── E7/
└── A365/
```
 
| Folder | Description |
|----------|-------------|
| BP | Microsoft 365 Business Premium |
| E5 | Microsoft Defender Suite or Microsoft 365 E5 |
| E7 | Microsoft 365 E7 |
| A365 | Agent 365 Standalone |
 
---
 
## 📖 Naming Convention
 
All policy templates follow the naming format below:
 
```text
<MinimumLicense>-ALSO-CA###-<Persona>-<TypeOfProtection>-<Apps>-<Platforms>-<AccessControls>-<SessionControls>
```
 
### Example
 
```text
E5-ALSO-CA001-Admins-IdentityProtection-AllApps-AllPlatforms-Grant-RequirePhishingResistantMFA
```
 
---
 
## 🧩 Naming Components
 
| Component | Description |
|------------|------------|
| MinimumLicense | Minimum Microsoft license required to use the policy |
| ALSO | Company providing the policy template |
| CA### | Unique Conditional Access policy number |
| Persona | Target user persona |
| TypeOfProtection | Security category of the policy |
| Apps | Applications targeted by the policy |
| Platforms | Platforms targeted by the policy |
| AccessControls | Determines whether access is granted or blocked |
| SessionControls | Controls enforced by the policy |
 
---
 
# 🎫 License Types
 
| Code | License |
|------|----------|
| BP | Microsoft 365 Business Premium |
| E5 | Microsoft Defender Suite or Microsoft 365 E5 |
| E7 | Microsoft 365 E7 |
| A365 | Agent 365 Standalone |
 
---
 
# 👥 Personas
 
## Global
 
Policies that apply broadly to all personas or cover scenarios that are not specific to another persona.
 
## Admins
 
Non-guest cloud or synchronized identities assigned Microsoft Entra ID or Microsoft 365 administrative roles.
 
## Internals
 
Employees with accounts in the tenant who work in standard end-user roles.
 
## Guests
 
External users invited to the tenant using Microsoft Entra B2B guest accounts.
 
## Agents
 
Agent identities and agent-related resources governed through Conditional Access.


 
---
 
# 🛡️ Protection Types
 
| Type | Description |
|--------|------------|
| Base Protection | Foundational security controls |
| Identity Protection | Protection against identity-based threats |
| App Protection | Protection of cloud applications and access |
| Attack Surface Reduction | Reduction of exposed attack vectors and risky behavior |
 
---
 
# 📱 Application Scope
 
Defines which applications the Conditional Access policy targets.
 
### Examples
 
```text
AllApps
SelectedApps
ExchangeOnline
MicrosoftAdminPortals
AzureManagement
Microsoft365
```
 
---
 
# 💻 Platform Scope
 
Defines which device platforms the Conditional Access policy targets.
 
### Examples
 
```text
AllPlatforms
Windows
macOS
iOS
Android
Linux
```
 
---
 
# 🚦 Access controls
 
Determines whether access is granted or blocked.
 
| Value | Description |
|---------|-------------|
| Grant | Allows access when policy requirements are satisfied |
| Block | Denies access when policy requirements are satisfied |
 
---
 
# ⚙️ Session controls
 
Actions define which controls are applied when the Conditional Access policy is triggered.




