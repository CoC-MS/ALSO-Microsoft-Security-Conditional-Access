# 🔐 Conditional Access policy guide

[Public documentation](README.md)

This guide summarizes the 41 current exports by policy number. Links open the exact JSON files, preserving existing spelling. Read the complete conditions and controls before use; the names and original README describe intent but sometimes differ from the settings.

> [!IMPORTANT]
> All current exports are disabled. Import in **OFF** state and review [General prerequisites](general-prerequisites.md) and [Conditional Access prerequisites](conditional-access-prerequisites.md). Supporting object references must be mapped to the destination tenant.

## 🌐 Global policies

| Policy | Exported control / review |
| --- | --- |
| [BP CA000](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA000-Global-AllApps-AnyPlatform-Grant-RequireMFA.json) | MFA for all applications, subject to exclusions. |
| [BP CA001](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA001-Global-AllApps-AnyPlatform-Block-ExceptWhitelListedCountries.json) | Block outside the whitelisted country location; the export includes Norway, Netherlands, Belgium, and Luxembourg. |
| [BP CA002](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA002-Global-AllApps-AnyPlatform-Block-LegacyAuthentication.json) | Block legacy authentication client types. |
| [BP CA003](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA003-Global-RegisterOrJoinDevice-AnyPlatform-Grant-RequireMFA.json) | MFA for the device registration user action; coordinate with the device registration MFA setting. |
| [BP CA004](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA004-Globa-AllApps-AnyPlatform-Block-AuthenticationFlowsAndDeviceCodeFlow.json) | Block device code flow and authentication transfer; assess legitimate workflows. |
| [BP CA005](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA005-Global-Office365-iOSAndAndroid-ClientApps-Unmanaged-Grant-RequireAppEnforcedRestrictions.json) | Microsoft 365 mobile client scenario with `compliantApplication` grant and application-enforced restrictions; review both controls and device conditions. |
| [BP CA006](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA006-Global-Office365-AnyPlatform-Browser-Unmanaged-Grant-RequireAppEnforceRestrictions.json) | Application-enforced restrictions for SharePoint Online and Exchange Online browser access; configure service-side restrictions. |

## 👑 Administrator and Tier 0 policies

Role targeting varies: most administrator policies contain 24 role IDs, CA103 contains 23, and CA106 targets an authentication context rather than the same role list.

| Policy | Exported control / review |
| --- | --- |
| [BP CA100](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA100-Admins-AdminPortals-AnyPlatform-Grant-RequireMFA.json) | Multifactor authentication strength for Microsoft admin portals. |
| [BP CA101](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA101-Admins-AllApps-AnyPlatform-Grant-RequireMFA.json) | MFA for all applications. |
| [BP CA102](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA102-Admins-AllApps-AnyPlatform-Grant-RequireSigninFrequency8H.json) | Sign-in frequency of 8 hours; the exclusion group name says 12H. |
| [BP CA103](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA103-Admins-AllApps-AnyPlatform-Grant-DisablePersistentBrowser.json) | Persistent browser mode `never`; review the 23-role scope. |
| [BP CA104](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA104-Admins-AllApps-AnyPlatform-Grant-CAEEnforceLocation.json) | Strict-location CAE, but application scope is currently `None`; configure intended supported resources and use an ON/OFF pilot. |
| [BP CA105](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA105-Admins-AllApps-AnyPlatform-Grant-PhishingResistantMFA.json) | Phishing-resistant MFA; excludes Microsoft Graph Command Line Tools. |
| [E5 CA106](../../ALSO_CA/ConditionalAccess/E5-ALSO-CA106-Tier0Admins-AllApps-AnyPlatform-Grant-RequirePhishingResistantMFAOnRoleActivation.json) | Phishing-resistant MFA and every-time reauthentication for context `c1`; map the context and configure PIM activation separately. |
| [BP CA107](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA107-Admins-AllApps-Windows-Grant-RequireCompliantDevice.json) | Require a compliant Windows device. |
| [BP CA108](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA108-Admins-AllApps-MacOS-Grant-RequireCompliantDevice.json) | Require a compliant macOS device. |
| [BP CA109](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA109-Admins-AllApps-AnyPlatform-Block-UnknownPlatforms.json) | Block platforms outside the exported platform exclusions. |
| [BP CA110](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA110-Admins-AllApps-iOSandAndroid-Grant-RequireCompliantDevice.json) | Require a compliant iOS/Android device; assess whether administrators need mobile access. |

## 👤 Internal-user policies

Review the included internal-user group, exclusions, and device filters for each policy. Intune enrollment/compliance setup is separate.

| Policy | Exported control / review |
| --- | --- |
| [BP CA200](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA200-Internals-AllApps-AnyPlatform-Grant-RequireMFA.json) | MFA for the included internal-user group. |
| [E5 CA201](../../ALSO_CA/ConditionalAccess/E5-ALSO-CA201-Internals-AllApps-AnyPlatform-Block-HighRiskUser.json) | Block high user risk; confirm Entra ID Protection entitlement. |
| [BP CA202](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA202-Internals-AllApps-UnmanagedWindowsAndMacOs-Grant-RequireSigninFrequency12H.json) | Sign-in frequency of 12 hours; review unmanaged-device scope. |
| [BP CA203](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA203-Internals-IntuneEnrollment-AnyPlatform-Grant-RequireMFA.json) | MFA and every-time reauthentication; currently targets Microsoft Intune, not Microsoft Intune Enrollment. |
| [BP CA204](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA204-Internals-AllApps-AnyPlatform-Block-UnknownPlatforms.json) | Block platforms outside the exported platform exclusions. |
| [BP CA205](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA205-Internals-AllApps-Windows-Grant-RequireCompliantDevice.json) | Require compliant Windows devices; review Microsoft Intune application exclusion. |
| [BP CA206](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA206-Internals-AllApps-AnyPlatform-Grant-DIsablePersistentBrowser.json) | Persistent browser mode `never`; review managed/compliant-device exclusions. |
| [BP CA207](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA207-Internals-SelectedApps-AnyPlatform-Block-SelectedApps.json) | Block a selected application with an Office365 exclusion; replace/resolve tenant-specific application scope. |
| [BP CA208](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA208-Internals-AllApps-MacOs-RequireCompliantDevice.json) | Require compliant macOS devices; review Microsoft Intune application exclusion. |
| [BP CA209](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA209-Internals-AllApps-AnyPlatform-EnforceLocationCAE.json) | Strict-location CAE, not a macOS compliance policy as described in the original README; use an ON/OFF pilot. |
| [E5 CA210](../../ALSO_CA/ConditionalAccess/E5-ALSO-CA210-Internals-AllApps-AnyPlatform-Block-HighRiskSignIn.json) | Block high sign-in risk; confirm Entra ID Protection entitlement. |

## ⚙️ Service-account policies

These policies target user identities in the service-account group, not service principals or every workload identity. Verify unattended workflows can satisfy the proposed controls.

| Policy | Exported control / review |
| --- | --- |
| [BP CA300](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA300-ServiceAccounts-AllApps-AnyPlatform-RequireMFA.json) | MFA for browser and mobile/desktop client sign-ins in the service-account group; review all exclusions. |
| [BP CA301](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA301-ServiceAccounts-AllApps-AnyPlatform-Block-UntrustedLocations.json) | Block outside the service-account country location, currently Norway; inspect duplicate-looking exclusion group files. |

## 🤝 Guest-user policies

Review the exported guest/external-user conditions and application IDs rather than assuming every external identity or application is covered.

| Policy | Exported control / review |
| --- | --- |
| [BP CA400](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA400-GuestUsers-AllApps-AnyPlatform-Grant-RequireMFA.json) | Require MFA. |
| [BP CA401](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA401-GuestUsers-AllApps-AnyPlatform-Block-NonGuestAppAccess.json) | Block all applications except Office365 and a selected application ID; review the allowlist. |
| [BP CA402](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA402-GuestUsers-AllApps-AnyPlatform-Grant-SigninFrequency12H.json) | Sign-in frequency of 12 hours. |
| [BP CA403](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA403-GuestUsers-AllApps-AnyPlatform-Grant-DisablePersistentBrowser.json) | Persistent browser mode `never`. |
| [BP CA404](../../ALSO_CA/ConditionalAccess/BP-ALSO-CA404-GuestUsers-SelectedApps-AnyPlatform-Block-SelectedApps.json) | Block Microsoft admin portals in the current export. |

## 🤖 Agent policies

Complete Agent 365 licensing and onboarding before import. Agent identities and agent users use different targeting fields; inspect those conditions explicitly.

| Policy | Exported control / review |
| --- | --- |
| [A365 CA501](../../ALSO_CA/ConditionalAccess/A365-ALSO-CA501-Agents-AllApps-AnyPlatform-Block-HighRiskAgent.json) | Block high-risk agent identity service principals. |
| [A365 CA502](../../ALSO_CA/ConditionalAccess/A365-ALSO-CA502-Agents-AllAgentIdentities-AllAgentResources-Block-AllExceptSelected.json) | Block agent identities accessing agent resources; establish intended approved exclusions before enabling. |
| [A365 CA503](../../ALSO_CA/ConditionalAccess/A365-ALSO-CA503-Agents-AllAgentUsers-Grant-RequireCompliantDevice.json) | Require compliant devices for agent users. |
| [A365 CA504](../../ALSO_CA/ConditionalAccess/A365-ALSO-CA504-Agents-AllAgentUsers-AllResources-Block-RiskyAgents.json) | Block agent users with medium/high agent identity risk. |
| [A365 CA505](../../ALSO_CA/ConditionalAccess/A365-ALSO-CA505-Agents-AllAgentUsers-AllResources-Grant-RequireCompliantNetWork.json) | Block agent users outside the compliant network location for `AllAgentIdResources`; the `Grant` name is not the actual grant control. |

Continue with [How to import](how-to-import.md). For naming variations, see [Naming exceptions](naming-exceptions.md).
