# 🛡️ Conditional Access prerequisites

[Public documentation](README.md)

Complete [General prerequisites](general-prerequisites.md), then review the dependencies for each selected policy. Names alone are not a configuration specification.

## 👥 Identity scope and exclusions

Review included and excluded users, groups, administrative roles, guest types, agent identities, and applications in each JSON. Internal-user and service-account groups are supplied as examples; validate or populate membership explicitly. CA300 and CA301 reference `ALSO- CA-ServiceAccounts`, not the internal-user group.

Most administrator policies include 24 role IDs, but CA103 includes 23. These lists do not represent every administrative role; assess the actual IDs and your intended scope. Validate emergency-access exclusions across every policy you enable, including broad global policies.

Resolve source IDs to destination objects using the import tool's supported migration workflow. Review `MigrationTable.json` as source metadata; it does not prove that references exist in the target tenant. Missing or incorrect references can cause import failures or unintended targeting.

## 🌍 Locations and networks

| Dependency | Current export | Review |
| --- | --- | --- |
| `ALSO-Whitelisted countries (NO)` | Norway (`NO`) | CA001 blocks outside this location. Set the intended countries before enabling |
| `ALSO-Allowed countries for Service Accounts (NO)` | Norway (`NO`) | CA301 blocks outside this location. Set the intended countries before enabling. |
| `All Compliant Network locations` | Compliant network named location | CA505 blocks agent users outside this location. Confirm Global Secure Access setup and the required licences; importing the location does not deploy a compliant network. |

CA104 and CA209 use strict-location CAE. CA104 now targets all applications. Verify supported resources, network behavior, locations, and recovery access before testing. Do not assume report-only is supported for strict-location enforcement.

## 🔑 Authentication and role activation

Prepare MFA registration and permitted authentication methods for MFA policies. CA105 and CA106 require phishing-resistant MFA; ensure targeted users have a supported method and a recovery path. CA105 excludes Microsoft Graph Command Line Tools; review whether that exception is appropriate.

CA106 references the `ALSO-Tier0 Admins` authentication context (`c1`). The current packages do not include an `AuthenticationContext` export, so create or map the intended context before importing CA106, then configure the intended PIM role activation settings to request it. Importing a Conditional Access policy does not automatically attach a context to PIM roles.

For CA003, review the device setting **Require Multifactor Authentication to register or join devices with Microsoft Entra**. The existing guide calls for disabling that setting before enabling the Conditional Access replacement; plan the change without leaving a protection gap.

## 💻 Devices, enrollment, and applications

Deploy and validate Intune enrollment and compliance policies for each selected platform before enabling compliant-device requirements. These device-management policies are not included here.

CA203 intentionally uses the existing **Microsoft Intune** application (`0000000a-0000-0000-c000-000000000000`) as an example target. For the intended enrollment scenario, manually register the **Microsoft Intune Enrollment** service principal (`d4ebce55-015a-49b5-a083-c84d1797ae8c`) using an authorized administrator and Microsoft's supported workflow, then replace the example application target before deployment. Review related application exclusions in CA205 and CA208 as well.

For CA005, review both the `compliantApplication` grant control and the application-enforced restriction session control. CA006 targets SharePoint Online and Exchange Online browser access. Configure the application-side restrictions and validate client/platform support; importing these policies does not create Intune app protection policies or configure those services.

CA207, CA401, and CA404 contain selected applications or exclusions. Resolve every application ID against the target tenant and intentionally choose allowed/blocked applications.

## 🤖 Agent policies

The existing guide requires an **Agent 365 licence and Agent 365 portal onboarding before importing CA501-CA505**; otherwise import may fail. Confirm current feature availability, Graph support, and licensing with Microsoft. Leave these exports unselected if the tenant is not prepared for agent governance.

CA502 blocks agent identities by default, so define approved exclusions before enablement. CA503 requires compliant devices for agent users. CA505 blocks agent users outside the compliant network and targets `AllAgentIdResources`.

See the [Policy guide](conditional-access-policies.md), [Naming exceptions](naming-exceptions.md), and [How to import](how-to-import.md).
