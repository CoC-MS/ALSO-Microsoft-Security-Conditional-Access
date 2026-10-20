# 🧩 Dependencies and import errors

**Disclaimer:** Licensing prerequisites and feature availability listed on this page may be incorrect, incomplete, or outdated. We strongly recommend verifying all licensing information against the latest official Microsoft licensing documentation before making any purchasing or deployment decisions.

[Public documentation](README.md)

Many Conditional Access exports reference tenant objects or services that must already exist, be imported with the policy, or be mapped through `MigrationTable.json`. A policy can fail to import even when its JSON is valid if a referenced group, named location, authentication context, application, or service capability is missing.

> [!IMPORTANT]
> Import policies in **OFF** state. Resolve every dependency and verify the resulting target objects before enabling a policy. A successful import does not prove that assignments, exclusions, or service configuration are correct.

## Common Microsoft Graph import errors

The previous README included these representative errors. Request IDs vary for every operation, so use the status and response text rather than matching the example request ID.

### Missing or unmapped dependency

This error commonly appears when a policy references a group, named location, authentication context, or application that is absent or not mapped in the destination tenant:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df5ea509-9005-47d1-9d00-8852534700ac). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request
```

CA001 previously showed the same class of failure with a different request ID:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: 289aa93d-2f7e-4d67-8b31-ed63349446d7). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request.
```

### Agent policy prerequisite failure

The previous README documented this representative Agent 365 import failure when licensing or onboarding was not ready:

```text
Failed to invoke MS Graph with URL https://graph.microsoft.com/beta/identity/conditionalAccess/policies (Request ID: df32d38d-3943-4a55-bfbc-e1e892358ebb). Status code: BadRequest. Response message: The server could not process the request because it is malformed or incorrect. Exception: The remote server returned an error: (400) Bad Request.
```

`400 Bad Request` is not specific enough to identify the missing dependency by itself. Inspect the selected policy, its source references, the import-tool output, and the destination tenant before retrying.

## Policy dependency guide

| Policy or series | Required preparation | Likely result if omitted |
| --- | --- | --- |
| CA001 | Import or map `ALSO-Whitelisted countries (NO)`. The current export contains Norway only; change it for the tenant before enablement. | Import can fail because the named-location reference cannot be resolved. |
| CA003 | Coordinate with the Entra device setting **Require Multifactor Authentication to register or join devices with Microsoft Entra**. | Duplicate or conflicting controls can affect device registration. |
| CA005 | Configure and assign the required Intune app protection policy and validate supported applications and clients. | The CA policy can import, but access can fail or the intended protection may not be available. |
| CA006 | Configure the corresponding SharePoint Online and Exchange Online application-enforced restrictions. | Importing Conditional Access alone does not configure the service-side restrictions. |
| CA104 and CA209 | Prepare trusted/compliant network locations, recovery access, and supported resources for strict-location CAE. | Report-only is not supported for this strict-location behavior; use a controlled ON/OFF pilot. |
| CA105 | Register phishing-resistant authentication methods for targeted administrators. Review the Microsoft Graph Command Line Tools exclusion. | Administrators can be unable to satisfy the authentication strength. |
| CA106 | Import or map the `ALSO-Tier0 Admins` authentication context (`c1`) included in the E5 and E7 packages, configure PIM role activation to request it, and prepare phishing-resistant authentication. | Import can fail on the missing context, or the imported policy can remain unused because PIM was not configured. |
| CA200-CA211, including E5 CA201 and E5 CA210 | Import or map `ALSO- All Internals`, populate the intended membership, and map each policy exclusion group. | Import can fail on unresolved group references, or scope can be empty/incorrect. |
| CA203 | Import/map the internal and exclusion groups. Register Microsoft Intune Enrollment manually, then replace the example Microsoft Intune application target. | Import can fail if the intended service principal is referenced before it exists; leaving the example target changes the scenario. |
| CA205, CA208, and CA211 | Deploy and validate the corresponding Windows, macOS, iOS, or Android Intune compliance policies first. | Users cannot satisfy the compliant-device grant, or the control does not provide the intended assurance. |
| CA207, CA401, and CA404 | Resolve every selected application ID and intentionally define the allow/block scope. | A tenant-specific or missing application reference can fail import or target the wrong resources. |
| CA300 | Import or map `ALSO- CA-ServiceAccounts`, populate the intended user-based service accounts, and review exclusions. | Import can fail on the group reference; unattended accounts may also be unable to complete MFA. |
| CA301 | Import/map the service-account group, its exclusion group, and `ALSO-Allowed countries for Service Accounts (NO)`. The current location contains Norway only. | Import can fail on unresolved references, or sign-ins can be blocked outside the configured countries. |
| CA501-CA505 | Assign the required Agent 365 licensing and complete Agent 365 portal onboarding before import. | Agent policy import can fail with `400 Bad Request`. |
| CA502 | Define approved agent exclusions before enablement. | The policy blocks agent identities by default. |
| CA503 | Prepare device compliance for agent users. | Agent users cannot satisfy the compliant-device requirement. |
| CA505 | Configure Global Secure Access and the compliant network named location. | Importing the named location does not deploy a compliant network; agent users can be blocked outside it. |

## Register Microsoft Intune Enrollment for CA203

CA203 intentionally contains the existing **Microsoft Intune** application (`0000000a-0000-0000-c000-000000000000`) as an example. For an Intune enrollment policy, register the **Microsoft Intune Enrollment** service principal (`d4ebce55-015a-49b5-a083-c84d1797ae8c`) in the destination tenant, then replace the example application target.

Run this only as an authorized administrator in the correct destination tenant:

```powershell
Connect-MgGraph
New-MgServicePrincipal -AppId d4ebce55-015a-49b5-a083-c84d1797ae8c
```

Confirm the connected tenant, review the created enterprise application, and use its destination object when updating or mapping CA203. The command does not import the Conditional Access policy or configure its groups and exclusions.

## Group and assignment dependencies

The packages include example groups and policy-specific exclusion groups. Importing a group definition does not populate the correct tenant membership automatically. Before enabling policies:

1. Map source group references to the intended destination groups.
2. Populate `ALSO- All Internals`, `ALSO- CA-ServiceAccounts`, emergency-access exclusions, Tier 0 groups, and policy-specific exclusions.
3. Confirm every include and exclude object in the resulting policy.
4. Use Conditional Access **What If** and sign-in logs with test identities.

If **Import assignments** or dependency import is disabled in the import tool, create and map the objects separately before importing dependent policies. Do not treat a skipped dependency as an optional assignment.

## Troubleshooting checklist

When import fails:

1. Confirm that the selected package matches the tenant's licensing and that required services are onboarded.
2. Confirm that groups, named locations, authentication context, applications, and service principals exist in the destination tenant.
3. Review `MigrationTable.json` and the import tool's object mapping; source object IDs are not destination object IDs.
4. Check the import-tool command window for the failed resource and Microsoft Graph response.
5. Import or map dependencies first, then retry only the affected policy in **OFF** state.
6. Inspect the resulting policy in Entra before enabling it.

See [How to import](how-to-import.md) for the original illustrated workflow, including download, sign-in, consent, and Bulk Import screenshots. See [Conditional Access prerequisites](conditional-access-prerequisites.md) for service-specific preparation and the [Policy guide](conditional-access-policies.md) for each policy's intent.
