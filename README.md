# 🛡️ ALSO Microsoft Security Conditional Access Policy Templates

> A collection of Microsoft Entra Conditional Access policy templates, named locations, security groups and authentication context designed to help organizations accelerate secure deployments and implement Microsoft Security best practices with Zero trust principles.
>
> **Works with Business Premium and up.**

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
| **E5** | Microsoft Defender Suite (for Business Premium, Microsoft 365 E3, or Microsoft 365 E5 customers) |
| **A365** | Agent 365 Standalone license combined with Microsoft Defender Suite, Microsoft 365 E5, or Microsoft 365 E7 |

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
> **PS All agents policies CA501-505 requires Agent 365 license assigned and Agent 365 portal onboarding need to be finished- otherwise policies will fail on import with following message.**

```text
"Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df32d38d-3943-4a55-bfbc-e1e892358ebb). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request."
```

---

### A365-ALSO-CA501-Agents-AllApps-AnyPlatform-Block-HighRiskAgent

This policy blocks agent identities with a high risk level from accessing resources in your tenant.

---

### A365-ALSO-CA502-Agents-AllAgentIdentities-AllAgentResources-Block-AllExceptSelected

By default, this policy prevents all agent identities from being used. Only agents that have been specifically excluded (approved) are allowed to be used. This can also be controlled in Agent 365 portal.

---

### A365-ALSO-CA503-Agents-AllAgentUsers-Grant-RequireCompliantDevice

This policy blocks access for all Agent Users from non-compliant devices.

---

### A365-ALSO-CA504-Agents-AllAgentUsers-AllResources-Block-RiskyAgents

This policy blocks autonomous agents operating as users when Microsoft Entra ID Protection detects medium or high risk.

---

### A365-ALSO-CA505-Agents-AllAgentUsers-AllResources-Grant-RequireCompliantNetWork

This policy blocks agent user sessions from all locations except those compliant with the Global Secure Access network.

---

## 🌐 Global Policies

### BP-ALSO-CA000-Global-AllApps-AnyPlatform-Grant-RequireMFA

This policy requires MFA for all cloud apps, from every platform. It captures all authentications in scope not captured by other MFA policies.

---

### BP-ALSO-CA001-Global-AllApps-AnyPlatform-Block-ExceptWhitelListedCountries

This policy blocks all countries, to all cloud apps, from every platform except for the countries configured in the named location ALSO-Whitelisted countries (NO). Norway is the only country in the scope. Remember to remove/add at your choice. PS: Named location needs to be imported, otherwise policy will fail on import with following message:

```text
"Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: 289aa93d-2f7e-4d67-8b31-ed63349446d7). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request."
```

---

### BP-ALSO-CA002-Global-AllApps-AnyPlatform-Block-LegacyAuthentication

This policy blocks legacy authentication for all users, to all cloud apps, from any platform.

---

### BP-ALSO-CA003-Global-RegisterOrJoinDevice-AnyPlatform-Grant-RequireMFA

This policy requires MFA for all users, to register or join a device to your tenant/environment.

> [!IMPORTANT]
> PS: Remember to disable Require Multifactor Authentication to register or join devices with Microsoft Entra first before turning on this policy.

---

### BP-ALSO-CA004-Globa-AllApps-AnyPlatform-Block-AuthenticationFlowsAndDeviceCodeFlow

This policy prevents all users from using Device Code Flow and Authentication Transfer (preview). This is important to avoid device code phishing.

---

### BP-ALSO-CA005-Global-Office365-iOSAndAndroid-ClientApps-Unmanaged-Grant-RequireAppEnforcedRestrictions

This policy requires App Enforced Restrictions on unmanaged (BYOD) iOS/IpadOS and Android devices.

---

### BP-ALSO-CA006-Global-Office365-AnyPlatform-Browser-Unmanaged-Grant-RequireAppEnforceRestrictions

This policy requires App Protection policies for all users when accessing Office 365 data from unmanaged (BYOD) iOS or Android devices. Needs to be configured in Intune first. Look in iOS/Ipad and Android repos to get template.

---

## 👑 Admin Policies

### BP-ALSO-CA100-Admins-AdminPortals-AnyPlatform-Grant-RequireMFA

This policy requires MFA for certain admin roles when they access the access Admin Portals. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA101-Admins-AllApps-AnyPlatform-Grant-RequireMFA

This policy requires MFA for certain admin roles when they access the any cloud app. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA102-Admins-AllApps-AnyPlatform-Grant-RequireSigninFrequency8H

This policy sets a Sign-in frequency for certain admin roles to a maximum of 8 hours. Admins need to re-authenticate of logon after 8 hours. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA103-Admins-AllApps-AnyPlatform-Grant-DisablePersistentBrowser

This policy prevents having persistent browser sessions for admins from every device. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA104-Admins-AllApps-AnyPlatform-Grant-CAEEnforceLocation

his policy allows Microsoft Entra ID to re-evaluate a user's access to resources in near real-time, rather than waiting for the typical token expiration time (which could be up to an hour). Read the Microsoft documentation here: https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation#conditional-access-policy-evaluation-preview. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

> [!WARNING]
> PS: This policy only support ON or OFF mode, report mode are not supported.

---

### BP-ALSO-CA105-Admins-AllApps-AnyPlatform-Grant-PhishingResistantMFA

Highly recommended one and aligns well with Zero Trust principles for admins.  This policy requires Phishing Resistant MFA for admins. Check your authentication methods in Entra ID first (FIDO2) or create custom authentication method. It does exclude Microsoft Graph Command Line Tools for own needs It's slightly different from the Microsoft Template policy. Global Reader and Intune Administrators are also included here. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA107-Admins-AllApps-Windows-Grant-RequireCompliantDevice

This policy requires compliant device for selected admin roles when signing in From Windows devices. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it. And set your compliance policies in Windows first of all. Check Intune policy repo to find compliance templates for Windows devices.

---

### BP-ALSO-CA108-Admins-AllApps-MacOS-Grant-RequireCompliantDevice

This policy requires compliant device for selected admin roles when signing in From MacOS devices. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it. And set your compliance policies for MacOS first of all. Check Intune policy repo to find compliance templates for MacOS devices.

---

### BP-ALSO-CA109-Admins-AllApps-AnyPlatform-Block-UnknownPlatforms

This policy blocks all platforms when signing in with admin account except Windows, MacOS, Android and iOS/IpadOS.  PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it.

---

### BP-ALSO-CA110-Admins-AllApps-iOSandAndroid-Grant-RequireCompliantDevice

This policy requires compliant device for selected admin roles when signing in From iOS/IpadOS or Android devices. PS: Only 24 admin roles are included ( privileged ). Add more if you feel for it. And set your compliance policies for iOS/IpadOS and Android first of all. Check Intune policy repo to find compliance templates for these devices. PS: Consider to block sign in from mobile devices for administrators if absolutely not needed!

---

## 👤 Internal User Policies

### BP-ALSO-CA200-Internals-AllApps-AnyPlatform-Grant-RequireMFA

This policy requires MFA for all internal identities, for all cloud applications, from any platform.

Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. PS: This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA202-Internals-AllApps-UnmanagedWindowsAndMacOs-Grant-RequireSigninFrequency12H

This policy sets a Sign-in frequency to a maximum of 12 hours for internals, to all cloud apps, using unmanaged Windows or MacOS devices. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA203-Internals-IntuneEnrollment-AnyPlatform-Grant-RequireMFA

This policy requires MFA for internals when enrolling their devices in Intune. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

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

This policy blocks unknown/unsupported device platforms for internals - MacOS, Windows, iOS/IpadOS and Android. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA205-Internals-AllApps-Windows-Grant-RequireCompliantDevice

This policy blocks access from non-compliant Windows devices. Remember to set compliance requirements in Intune for Windows first. Check Windows repo to find compliance templates for Windows. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA206-Internals-AllApps-AnyPlatform-Grant-DIsablePersistentBrowser

This policy prevents having persistent browser sessions for internals from unmanaged devices. Managed and compliant devices are excluded from the policy. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA207-Internals-SelectedApps-AnyPlatform-Block-SelectedApps

This policy prevents internals from accessing specific apps. In this example i've blocked a random app. You should review the included and excluded apps. Excluding office 365 is not necessary if its not included. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA208-Internals-AllApps-MacOs-RequireCompliantDevice

This policy requires MacOS devices to be compliant for internals. Remember to set compliance requirements in Intune for MacOS first. Check MacOS repo to find compliance templates for MacOS.

---

### BP-ALSO-CA209-Internals-AllApps-AnyPlatform-EnforceLocationCAE

This policy allows Microsoft Entra ID to re-evaluate a user's access to resources in near real-time, rather than waiting for the typical token expiration time (which could be up to an hour). Read the Microsoft documentation here: https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-continuous-access-evaluation#conditional-access-policy-evaluation-preview.

PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

> [!WARNING]
> This policy can only be in ON or OFF mode. Report mode are not supported.

---

## ⚙️ Service Account Policies

### BP-ALSO-CA300-ServiceAccounts-AllApps-AnyPlatform-RequireMFA

This policy requires ServiceAccounts to use MFA, from any platform when accessing any cloud app

PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### BP-ALSO-CA301-ServiceAccounts-AllApps-AnyPlatform-Block-UntrustedLocations

This policy prevents service accounts from logging in from untrusted countries.

PS: Verify the Named Location ALSO-Allowed countries for Service Accounts (NO) are imported to Entra ID, otherwise olicy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request. Only Norway are in the scope of the named location, so please add/remove at your specific needs.
```

---

## 🤝 Guest User Policies

### BP-ALSO-CA400-GuestUsers-AllApps-AnyPlatform-Grant-RequireMFA

This policy requires guest to use MFA, from any platform when accessing any cloud app.

---

### BP-ALSO-CA401-GuestUsers-AllApps-AnyPlatform-Block-NonGuestAppAccess

This policy blocks access for guests to all cloud apps (except for those excluded), from any device.

---

### BP-ALSO-CA402-GuestUsers-AllApps-AnyPlatform-Grant-SigninFrequency12H

This policy sets a Sign-in frequency to a maximum of 12 hours for guests, to all cloud apps, using any device.

---

### BP-ALSO-CA403-GuestUsers-AllApps-AnyPlatform-Grant-DisablePersistentBrowser

This policy prevents guest from having persistent browser sessions.

---

### BP-ALSO-CA404-GuestUsers-SelectedApps-AnyPlatform-Block-SelectedApps

This policy prevents guests from accessing specific apps. In this example i've blocked a random app. You should review the included and excluded apps. Excluding office 365 is not necessary if its not included. This is just an example.

---

## 🛡️ E5 Policies

### E5-ALSO-CA106-Tier0Admins-AllApps-AnyPlatform-Grant-RequirePhishingResistantMFAOnRoleActivation

This policy requires phishing resistant MFA on role activation for Tier 0 admins. PS: Authentication context ALSO- Tier 0 Admins needs to imported to Entra ID first, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request. Only Norway are in the scope of the named location, so please add/remove at your specific needs.
```

---

### E5-ALSO-CA201-Internals-AllApps-AnyPlatform-Block-HighRiskUser

This policy blocks all internal users which have a high risk (user risk) status, to all cloud apps, from all platforms.

PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

---

### E5-ALSO-CA210-Internals-AllApps-AnyPlatform-Block-HighRiskSignIn

This policy blocks all internal users which have a high risk (signin risk) status, to all cloud apps, from all platforms. PS: Verify the included group(s) and/or add your custom groups which have all internals in it. ALSO- All Internals is added as an example. This group needs to be imported to Entra, otherwise policy will fail on import with following message:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

## Before importing 

> [!IMPORTANT]
PLEASE ENSURE THAT YOU HAVE COMPLETED THESE STEPS, BEFORE YOU START IMPORTING. AND THAT YOU HAVE READ POLICY DESCIRPTION HERE: https://github.com/CoC-MS/ALSO-Microsoft-Security-Conditional-Access/tree/main#-conditional-access-policies


1. Verify that your tenant have at least Entra ID P1 license. 

https://entra.microsoft.com/-> Overview -> License


2. Verify that security defaults are OFF. It can be checked here 


https://entra.microsoft.com/-> Properties -> Security defaults


3. You have at least Conditional Access Administrator role assigned to your user 


## How to import

1. Download Micke M Intune Management Tool from here:  https://github.com/Micke-K/IntuneManagement
2. Extract folder and Start with start.cmd in the folder (works without local administrator rights on Windows and MacOS)
   <img width="635" height="247" alt="image" src="https://github.com/user-attachments/assets/ae7405c2-17cb-43a1-a96e-cd60181a2619" />

3. Command window and UI will open
4. Press on icon in upper right corner to sign in
   <img width="1311" height="965" alt="image" src="https://github.com/user-attachments/assets/2e835f79-5e07-4c7d-bd7c-5bd4976fde50" />

5. You may need a Global Administrator to consent to required API permissions first time if have not used these tool before. This can be done after sign-in by pressing same icon in upper right corner once more and press "Request Consent". Command Graph Command Line Tools application will be registered in Entra. Feel free to remove it after import or remove at least admin consent.

   <img width="342" height="177" alt="image" src="https://github.com/user-attachments/assets/7ed4361f-0888-4b49-b08e-5def9bfbf420" />

6. After sign in and admin consent navigate to Bulk button in the left upper corner and press Import

   <img width="273" height="202" alt="image" src="https://github.com/user-attachments/assets/9e8b32ce-93fe-4ef8-9c19-325d138add8c" />

7. Find downloaded and extracted folder from this repo and choose Config folder.
8. Choose Conditional Access, Named Locations and Authentication context in menu, remove everything else.
9. Choose Conditional Access state: OFF. Very important.
10. Uncheck import assignments if you don't want to to import groups, named locations and authentication context. PS: Many policies will fail on import here. 
11. Check results on your tenant and if something is missing in CMD window. 










