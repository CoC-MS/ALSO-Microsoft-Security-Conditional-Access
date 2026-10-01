# 🛡️ ALSO Microsoft Security Conditional Access Policy Templates

> A collection of Microsoft Entra Conditional Access policy templates, named locations, security groups and authentication context designed to help organizations accelerate secure deployments and implement Microsoft Security best practices with Zero trust principles.
>
> **Works with Business Premium and up.**

---


> [!IMPORTANT]
> **⚠️ IMPORTANT: Read this before importing any policies.**  

| Resource | Description |
|-----------|-------------|
| 🛡️ **Security Information** | [View Security Policy](https://github.com/CoC-MS/ALSO-Microsoft-Security-Conditional-Access/tree/main?tab=security-ov-file) |
| 📖 **Policy Descriptions** | [View Policy Description ](https://github.com/CoC-MS/ALSO-Microsoft-Security-Conditional-Access/tree/main#-conditional-access-policies) |
| 🚀 **Before Importing** | [Read Before Importing Policies](https://github.com/CoC-MS/ALSO-Microsoft-Security-Conditional-Access/tree/main#before-importing) |

---


## 📂 File Structure

All files are organized into categories

```text
/
├── CA ALSO/
├── AuthenticationContext
└── ConditionalAccess
└── Groups
└── NamedLocations
└── MigrationTable.json
```

### License Tag Description

| Tag | Minimum Required License |
|:---:|--------------------------|
| **BP** | Microsoft 365 Business Premium or Microsoft Entra ID P1 |
| **E5** | Microsoft Defender Suite (for Business Premium, Microsoft 365 E3, or Microsoft 365 E5) |
| **A365** | Agent 365 Standalone license combined with Microsoft Defender Suite for Business Premium, Microsoft 365 E3/E5, or Microsoft 365 E7 |

---

## 📖 Naming Convention

All policy templates follow the naming format below:

```text
<MinimumLicense>-ALSO-CA###-<Persona>-<Apps>-<Platforms>-<AccessControls>-<SessionControls>
```

### Example

```text
BP-ALSO-CA001-Admins-AllApps-AllPlatforms-Grant-RequirePhishingResistantMFA
```

---

## 🧩 Naming Components

| Component | Description |
|-----------|-------------|
| **MinimumLicense** | Minimum Microsoft license required to use the policy |
| **ALSO** | Company providing the policy template to have a better control |
| **CA###** | Unique Conditional Access policy number |
| **Persona** | Target user persona |
| **Apps** | Applications targeted by the policy |
| **Platforms** | Platforms targeted by the policy |
| **AccessControls** | Determines whether access is granted or blocked |
| **SessionControls** | Controls enforced by the policy |

---

## 👥 Personas

### Global

Policies that apply broadly to all personas or cover scenarios that are not specific to another persona.

### Admins

Non-guest cloud or synchronized identities assigned Microsoft Entra ID or Microsoft 365 administrative roles.

### Internals

Employees with accounts in the tenant who work in standard end-user roles.

### Guests

External users invited to the tenant using Microsoft Entra B2B guest accounts.

### Agents

Agent identities and agent-related resources governed through Conditional Access.

---

## 📱 Application Scope

Defines which applications the Conditional Access policy targets.

### Examples

```text
AllApps
SelectedApps
ExchangeOnline
MicrosoftAdminPortals
SharepointOnline
Microsoft Intune Enrollment etc
```

---

## 💻 Platform Scope

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

## 🚦 Access controls

Determines whether access is granted or blocked.

| Value | Description |
|:-----:|-------------|
| **Grant** | Allows access when policy requirements are satisfied |
| **Block** | Denies access when policy requirements are satisfied |

---

## ⚙️ Session controls

Actions define which controls are applied when the Conditional Access policy is triggered.

---

# 🔐 Conditional Access Policies

## 🤖 Agent Policies

> [!IMPORTANT]
> **All Agent policies (CA501-CA505) require an Agent 365 license to be assigned and Agent 365 portal onboarding to be completed before import. Otherwise, the policies will fail during import and display the following error message.**

```text
"Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df32d38d-3943-4a55-bfbc-e1e892358ebb). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request."
```

---

### A365-ALSO-CA501-Agents-AllApps-AnyPlatform-Block-HighRiskAgent

Prevents agent identities from accessing tenant resources when Microsoft identifies the agent as having a high risk level

---

### A365-ALSO-CA502-Agents-AllAgentIdentities-AllAgentResources-Block-AllExceptSelected

Denies access for all agent identities by default. Only explicitly approved or excluded agents are permitted. Agent approval can also be managed through the Agent 365 portal 

---

### A365-ALSO-CA503-Agents-AllAgentUsers-Grant-RequireCompliantDevice

Restricts agent user access to devices that meet organizational compliance requirements.

---

### A365-ALSO-CA504-Agents-AllAgentUsers-AllResources-Block-RiskyAgents

Blocks agent users when Microsoft Entra ID Protection classifies the identity as medium or high risk.

---

### A365-ALSO-CA505-Agents-AllAgentUsers-AllResources-Grant-RequireCompliantNetWork

Allows agent user access only from locations connected through the Global Secure Access compliant network.

---

## 🌐 Global Policies

### BP-ALSO-CA000-Global-AllApps-AnyPlatform-Grant-RequireMFA

Enforces multifactor authentication across all cloud applications and device platforms. Acts as a baseline MFA policy for sign-ins not covered by more specific policies.

---

### BP-ALSO-CA001-Global-AllApps-AnyPlatform-Block-ExceptWhitelListedCountries

Restricts access from all countries except those defined in the ALSO-Whitelisted Countries (NO) named location. By default, only Norway is included and should be adjusted according to business requirements PS: Named location needs to be imported, otherwise policy will fail on import with following message:

```text
"Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: 289aa93d-2f7e-4d67-8b31-ed63349446d7). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request."
```

---

### BP-ALSO-CA002-Global-AllApps-AnyPlatform-Block-LegacyAuthentication

Protects the environment by blocking legacy authentication protocols across all cloud applications

---

### BP-ALSO-CA003-Global-RegisterOrJoinDevice-AnyPlatform-Grant-RequireMFA

Requires multifactor authentication when users register or join devices to the Microsoft Entra environment

> [!IMPORTANT]
> PS: Remember to disable Require Multifactor Authentication to register or join devices with Microsoft Entra first before turning on this policy.

---

### BP-ALSO-CA004-Globa-AllApps-AnyPlatform-Block-AuthenticationFlowsAndDeviceCodeFlow

Blocks Device Code Flow and Authentication Transfer sign-ins to help reduce exposure to device code phishing attacks.

---

### BP-ALSO-CA005-Global-Office365-iOSAndAndroid-ClientApps-Unmanaged-Grant-RequireAppEnforcedRestrictions

Applies App Enforced Restrictions when unmanaged Android or iOS/iPadOS devices access Microsoft 365 resources.

---

### BP-ALSO-CA006-Global-Office365-AnyPlatform-Browser-Unmanaged-Grant-RequireAppEnforceRestrictions

Requires application protection controls for unmanaged devices accessing Microsoft 365 data.

---

## 👑 Admin Policies

### BP-ALSO-CA100-Admins-AdminPortals-AnyPlatform-Grant-RequireMFA

Requires MFA for selected privileged administrative roles when accessing Microsoft administrative portals. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA101-Admins-AllApps-AnyPlatform-Grant-RequireMFA

Ensures privileged administrators perform MFA before accessing any cloud application. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA102-Admins-AllApps-AnyPlatform-Grant-RequireSigninFrequency8H

Limits administrator sessions to a maximum sign-in duration of 8 hours before reauthentication is required. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA103-Admins-AllApps-AnyPlatform-Grant-DisablePersistentBrowser

Disables persistent browser sessions for administrators to reduce the risk of unauthorized access from shared or unmanaged devices. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA104-Admins-AllApps-AnyPlatform-Grant-CAEEnforceLocation

Enables Continuous Access Evaluation (CAE), allowing Microsoft Entra ID to reassess access decisions in near real time based on security events and location changes. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

> [!WARNING]
> PS: This policy only support ON or OFF mode, report mode are not supported.

---

### BP-ALSO-CA105-Admins-AllApps-AnyPlatform-Grant-PhishingResistantMFA

Highly recommended. Requires phishing-resistant multifactor authentication for privileged administrators, supporting a stronger Zero Trust security posture.. Check your authentication methods in Entra ID first (FIDO2) or create custom authentication method. It does exclude Microsoft Graph Command Line Tools for own needs It's slightly different from the Microsoft Template policy. Global Reader and Intune Administrators are also included here. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA107-Admins-AllApps-Windows-Grant-RequireCompliantDevice

Allows administrator sign-ins from Windows devices only when the device meets defined compliance requirements. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it. And set your compliance policies in Windows first of all. Check Intune policy repo to find compliance templates for Windows devices.

---

### BP-ALSO-CA108-Admins-AllApps-MacOS-Grant-RequireCompliantDevice

Allows administrator sign-ins from macOS devices only when the device satisfies compliance policies.PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it. And set your compliance policies for MacOS first of all. Check Intune policy repo to find compliance templates for MacOS devices.

---

### BP-ALSO-CA109-Admins-AllApps-AnyPlatform-Block-UnknownPlatforms

Prevents administrator access from unsupported device platforms, allowing only approved operating systems Windows, MacOS, Android, iOS/IpadOS.  PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA110-Admins-AllApps-iOSandAndroid-Grant-RequireCompliantDevice

Requires compliant Android and iOS/iPadOS devices before administrators can access cloud resources. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it. And set your compliance policies for iOS/IpadOS and Android first of all. Check Intune policy repo to find compliance templates for these devices. PS: Consider to block sign in from mobile devices for administrators if absolutely not needed!

---

## 👤 Internal User Policies

### BP-ALSO-CA200-Internals-AllApps-AnyPlatform-Grant-RequireMFA

Requires multifactor authentication for internal users when accessing cloud applications from any supported platform.

Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. PS: This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA202-Internals-AllApps-UnmanagedWindowsAndMacOs-Grant-RequireSigninFrequency12H

Limits user sessions on unmanaged Windows and macOS devices by requiring reauthentication every 12 hours. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA203-Internals-IntuneEnrollment-AnyPlatform-Grant-RequireMFA

Requires MFA before users can enroll devices into Microsoft Intune. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

> [!IMPORTANT]
> And one another important thing: Policy have Microsoft Intune application assigned, needs to be replaced with Microsoft Intune Enrollment- Service principal needs to be registered if it doesn't exist on the tenant so import will fail here with following message

```powershell
Connect-MgGraph
New-MgServicePrincipal -AppId d4ebce55-015a-49b5-a083-c84d1797ae8c
```

---

### BP-ALSO-CA204-Internals-AllApps-AnyPlatform-Block-UnknownPlatforms

Blocks internal users from signing in using unsupported or unrecognized device platforms. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA205-Internals-AllApps-Windows-Grant-RequireCompliantDevice

Requires Windows devices to be compliant before internal users can access cloud applications. Remember to set compliance requirements in Intune for Windows first. Check Windows repo to find compliance templates for Windows. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA206-Internals-AllApps-AnyPlatform-Grant-DisablePersistentBrowser

Prevents persistent browser sessions on unmanaged devices while excluding compliant and managed devices. Managed and compliant devices are excluded from the policy. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA207-Internals-SelectedApps-AnyPlatform-Block-SelectedApps

Denies internal users access to specific applications defined within the policy scope. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA208-Internals-AllApps-MacOs-RequireCompliantDevice

Requires macOS devices to meet compliance standards before granting access to internal users. Remember to set compliance requirements in Intune for MacOS first. Check MacOS repo to find compliance templates for MacOS.

---

### BP-ALSO-CA209-Internals-AllApps-AnyPlatform-EnforceLocationCAE

Requires macOS devices to meet compliance standards before granting access to internal users.

PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

> [!WARNING]
> This policy can only be in ON or OFF mode. Report mode are not supported.

---

## ⚙️ Service Account Policies

### BP-ALSO-CA300-ServiceAccounts-AllApps-AnyPlatform-RequireMFA

Enforces multifactor authentication for service account identities interacting with cloud applications.

PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA301-ServiceAccounts-AllApps-AnyPlatform-Block-UntrustedLocations

Restricts service account sign-ins to trusted countries and blocks authentication attempts from other locations.

PS: Verify the Named Location ALSO-Allowed countries for Service Accounts (NO) are imported to Entra ID, otherwise olicy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request. Only Norway are in the scope of the named location, so please add/remove at your specific needs.
```

---

## 🤝 Guest User Policies

### BP-ALSO-CA400-GuestUsers-AllApps-AnyPlatform-Grant-RequireMFA

Requires guest users to complete MFA before accessing cloud resources.

---

### BP-ALSO-CA401-GuestUsers-AllApps-AnyPlatform-Block-NonGuestAppAccess

Limits guest access by restricting which cloud applications can be accessed.

---

### BP-ALSO-CA402-GuestUsers-AllApps-AnyPlatform-Grant-SigninFrequency12H

Forces guest users to reauthenticate at least every 12 hours.

---

### BP-ALSO-CA403-GuestUsers-AllApps-AnyPlatform-Grant-DisablePersistentBrowser

Disables persistent browser sessions for guest users to reduce session exposure.

---

### BP-ALSO-CA404-GuestUsers-SelectedApps-AnyPlatform-Block-SelectedApps

Blocks guest access to applications explicitly defined within the policy scope.
---

## 🛡️ E5 Policies

### E5-ALSO-CA106-Tier0Admins-AllApps-AnyPlatform-Grant-RequirePhishingResistantMFAOnRoleActivation

Requires phishing-resistant authentication when privileged Tier 0 roles are activated through Privileged Identity Management. PS: Authentication context ALSO- Tier 0 Admins needs to imported to Entra ID first, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request. Only Norway are in the scope of the named location, so please add/remove at your specific needs.
```

---

### E5-ALSO-CA201-Internals-AllApps-AnyPlatform-Block-HighRiskUser

Blocks access for users identified as high risk by Microsoft Entra ID Protection.

PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### E5-ALSO-CA210-Internals-AllApps-AnyPlatform-Block-HighRiskSignIn

Blocks authentication attempts that Microsoft Entra ID Protection classifies as high sign-in risk. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

## Before importing 

> [!IMPORTANT]
> **PLEASE ENSURE THAT YOU HAVE COMPLETED THESE STEPS, BEFORE YOU START IMPORTING. AND THAT YOU HAVE READ POLICY DESCIRPTION HERE**: https://github.com/CoC-MS/ALSO-Microsoft-Security-Conditional-Access/tree/main#-conditional-access-policies


1. Verify that your tenant have at least Entra ID P1 license. 

https://entra.microsoft.com/ -> Overview -> License


2. Verify that security defaults are OFF. It can be checked here 


https://entra.microsoft.com/ -> Properties -> Security defaults


3. You have at least Conditional Access Administrator role assigned to your user 


## How to import

1. Download Micke M Intune Management Tool from here:  https://github.com/Micke-K/IntuneManagement
2. Extract folder and Start with start.cmd in the folder (works without local administrator rights on Windows and MacOS)   
   <img width="635" height="247" alt="image" src="https://github.com/user-attachments/assets/ae7405c2-17cb-43a1-a96e-cd60181a2619" />

3. Command window and UI will open
4. Press on icon in upper right corner to sign in
   <img width="1311" height="965" alt="image" src="https://github.com/user-attachments/assets/2e835f79-5e07-4c7d-bd7c-5bd4976fde50" />

5. You may need a Global Administrator to consent to required API permissions first time if have not used these tool before. This can be done after sign-in by pressing same icon in upper right corner once more and press "Request Consent". Command Graph Command Line Tools application will be registered in Entra. Feel free to remove it after import or remove at least admin consent.

   <img width="294" height="145" alt="image" src="https://github.com/user-attachments/assets/675ebdc9-dc87-4633-bfa5-fbb92f7ba53d" />


6. After sign in and admin consent navigate to Bulk button in the left upper corner and press Import

   <img width="273" height="202" alt="image" src="https://github.com/user-attachments/assets/9e8b32ce-93fe-4ef8-9c19-325d138add8c" />

7. Download project and unzip folder

<img width="401" height="373" alt="image" src="https://github.com/user-attachments/assets/b4005205-abc8-4e9b-a8b0-d6f919f99c06" />

   
9. Choose Conditional Access, Named Locations and Authentication context in menu, remove everything else.

> [!IMPORTANT]
> **11. On Conditional Access state- SELECT OFF. Very important.**
 
Uncheck import assignments if you don't want to to import groups, named locations and authentication context. PS: Many policies will fail on import here.

14. Check results on your tenant and if something is missing in CMD window. 


## Issues?

Open issue here: https://github.com/CoC-MS/ALSO-Microsoft-Security-Conditional-Access/issues/new/choose






