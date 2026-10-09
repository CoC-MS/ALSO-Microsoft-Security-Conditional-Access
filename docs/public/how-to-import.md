# 📥 How to import

[Public documentation](README.md)

Complete [General prerequisites](general-prerequisites.md), [Conditional Access prerequisites](conditional-access-prerequisites.md), and the review of selected policies in the [Policy guide](conditional-access-policies.md).

Use the [Micke M Intune Management Tool](https://github.com/Micke-K/IntuneManagement) as described in the existing repository guide. Follow its current setup and authentication instructions; UI labels and dependency handling may vary by version.

> [!WARNING]
> **Set Conditional Access state to OFF during import.** Do not bulk-enable policies or assume their source disabled state is preserved by every import workflow.

## Download and sign in

1. Download the repository with **Code > Download ZIP** and extract it to a short path. Verify all long filenames were extracted. Keep `ALSO_CA` and its migration metadata together.

   ![GitHub Code menu showing Download ZIP](https://github.com/user-attachments/assets/b4005205-abc8-4e9b-a8b0-d6f919f99c06)

2. Download and extract the tool. On Windows, launch `start.cmd` from its folder.

   ![Intune Management Tool folder with start.cmd](https://github.com/user-attachments/assets/ae7405c2-17cb-43a1-a96e-cd60181a2619)

3. Select the sign-in icon in the upper-right corner. Sign in with authorized permissions and confirm the destination tenant.

   ![Import tool sign-in icon](https://github.com/user-attachments/assets/2e835f79-5e07-4c7d-bd7c-5bd4976fde50)

4. If API consent is required, have an authorized administrator review the requested permissions and use **Request Consent** according to the tool's current instructions.

   ![Sign-in menu showing Request Consent](https://github.com/user-attachments/assets/675ebdc9-dc87-4633-bfa5-fbb92f7ba53d)

These illustrations are retained from the existing root README. They show the shared tool workflow, not a promise of the exact current UI.

## Import selected Conditional Access resources

1. Select **Bulk > Import** and point the workflow at the extracted `ALSO_CA` export set, not at `docs/public`.

   ![Bulk menu showing Import](https://github.com/user-attachments/assets/9e8b32ce-93fe-4ef8-9c19-325d138add8c)

2. Select **Conditional Access**, **Named Locations**, and **Authentication context** as needed for reviewed policies; deselect unrelated workloads. Select only the policies you intend to deploy, especially excluding A365 policies if agent prerequisites are not met.
3. Prepare required groups, locations, and authentication context before importing dependent policies, or use the tool's supported dependency-import/migration workflow. Review the source migration mappings and map every selected reference to the intended destination object.
4. The existing guide describes **Import assignments** as affecting dependency imports. Do not assume unchecking it makes the import complete or safe: omitted groups, locations, or context can cause policy import failures. If you omit automatic dependency import, create/map those objects separately first. Review the current tool version's behavior.
5. Explicitly choose **OFF** for Conditional Access state. Review selections and the target tenant before starting.
6. Inspect tool results and command-window output for failures. Missing references, app/service principals, consent, or Agent 365 readiness must be resolved rather than ignored. Inspect the resulting objects in Entra and confirm all imported policies are disabled.

## Review, pilot, and enable

Verify user/group membership, roles, applications, locations, context mappings, grant/session controls, and emergency-access exclusions in the destination tenant. Apply the specific review items for CA104, CA203, CA505, and the country locations in [Conditional Access prerequisites](conditional-access-prerequisites.md).

Use What If and sign-in logs to evaluate expected targeting. Use report-only for supported policies, then a small controlled ON pilot. Strict-location CAE policies CA104 and CA209 require a controlled ON/OFF test rather than report-only. Validate actual sign-ins, enrollment, authentication methods, compliant devices, and application restrictions before expanding scope.

Keep a rollback/recovery plan and monitor results after enablement. Reimporting is not a documented reconciliation mechanism here; inspect existing destination objects to avoid unintended duplicates.

For import problems or documentation corrections, see [Reporting issues](reporting-issues.md).
