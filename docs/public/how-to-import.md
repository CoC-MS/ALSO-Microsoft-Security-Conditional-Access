# 📥 How to import

[Public documentation](README.md)

Complete [General prerequisites](general-prerequisites.md), [Conditional Access prerequisites](conditional-access-prerequisites.md), [Dependencies and import errors](dependencies-and-import-errors.md), and the review of selected policies in the [Policy guide](conditional-access-policies.md).


> [!WARNING]
> **Set Conditional Access state to OFF during import.** Do not bulk-enable policies or assume their source disabled state is preserved by every import workflow.


## 🎥 Full video tutorial on how to get started and how to import step by step


https://github.com/user-attachments/assets/88e2ba12-e3d2-41fa-a1ec-5ff9bc2fea42


## Full written tutorial on how to get started and how to import step by step

1.Download and extract it to Onedrive location the [Micke M Intune Management Tool](https://github.com/Micke-K/IntuneManagement) 

2. Download this repository with **Code > Download ZIP** on main page and extract it to a Onedrive location

   ![GitHub Code menu showing Download ZIP](https://github.com/user-attachments/assets/b4005205-abc8-4e9b-a8b0-d6f919f99c06)

2. Use the [licensing guide](../../README.md#conditional-access-licensing-guide) to choose exactly one package: `ALSO_CA_BP`, `ALSO_CA_E5`, or `ALSO_CA_E7`.

5. Select the sign-in icon in the upper-right corner. Sign in with authorized permissions and confirm the destination tenant.

   ![Import tool sign-in icon](https://github.com/user-attachments/assets/2e835f79-5e07-4c7d-bd7c-5bd4976fde50)

6. If API consent is required, have an Global Administrator to consent to required API permissions used by the app

   ![Sign-in menu showing Request Consent](https://github.com/user-attachments/assets/675ebdc9-dc87-4633-bfa5-fbb92f7ba53d)


## Import selected Conditional Access resources

1. Select **Bulk > Import** and point the workflow at the selected `ALSO_CA_BP`, `ALSO_CA_E5`, or `ALSO_CA_E7` package, not at the repository root folder

   ![Bulk menu showing Import](https://github.com/user-attachments/assets/9e8b32ce-93fe-4ef8-9c19-325d138add8c)

2. Select at least  **Conditional Access** and  **Named Locations**  . When importing CA106 from E5 or E7, also select **Authentication context** so `ALSO-Tier0 Admins` can be imported or mapped. Deselect unrelated workloads and select only the policies you intend to deploy. A365 and E5 policies are available only in `ALSO_CA_E7` and require Agent 365 license and prerequisites + Entra P2 for E5 policies.

3. Deselect Import assignments if you don't want to import included Exclusion groups for Break Glass Accounts, Internals etc.
4. Deselect replace dependency ID's if you don't wish to replace them. Read more info in the tool 

> [!WARNING]
> **You can also use the Conditional Access wizard to import only Conditional Access policies. However, keep in mind that some policies may fail during import if they depend on Named Locations or Authentication Contexts. Please review the policy documentation for a complete overview of any prerequisites and requirements.**

5. Choose **OFF** for Conditional Access state (default on OFF usually). 
8. Inspect tool results and command-window output for failures. Missing references, app/service principals, consent, or Agent 365 readiness must be resolved rather than ignored. Use the representative errors and policy dependency matrix in [Dependencies and import errors](dependencies-and-import-errors.md). Inspect the resulting objects in Entra and confirm all imported policies are disabled.

## Review, pilot, and enable

Verify user/group membership, roles, applications, locations, context mappings, grant/session controls, and emergency-access exclusions in the destination tenant. Apply the specific review items for CA104, CA203, CA505, and the country locations in [Conditional Access prerequisites](conditional-access-prerequisites.md).

Use What If and sign-in logs to evaluate expected targeting. Use report-only for supported policies, then a small controlled ON pilot. Strict-location CAE policies CA104 and CA209 require a controlled ON/OFF test rather than report-only. Validate actual sign-ins, enrollment, authentication methods, compliant devices, and application restrictions before expanding scope.

Keep a rollback/recovery plan and monitor results after enablement. Reimporting is not a documented reconciliation mechanism here; inspect existing destination objects to avoid unintended duplicates.

For import problems or documentation corrections, see [Reporting issues](reporting-issues.md).
