# 🚀 General prerequisites

[Public documentation](README.md)

Check these items before importing Conditional Access resources into Microsoft Entra.

> [!IMPORTANT]
> The implementing partner is responsible for licence verification, compatibility review, testing, staged rollout, monitoring, and recovery. Read [Security information](../../Security.md).

## 🔐 Licensing

The existing repository classifies exports with these tags:

| Tag | Repository classification | Verify before deployment |
| --- | --- | --- |
| `BP` | Microsoft 365 Business Premium or Microsoft Entra ID P1 | Conditional Access entitlement for targeted users and additional service requirements for the selected controls. |
| `E5` | Microsoft Defender Suite for Business Premium, Microsoft 365 E3, or Microsoft 365 E5 | Actual Entra ID Protection and PIM entitlements; risk policies require Entra ID P2, and PIM requires eligible Entra ID P2 or ID Governance licensing. |
| `A365` | Agent 365 standalone with Microsoft Defender Suite for Business Premium, Microsoft 365 E3/E5, or Microsoft 365 E7 | Current Agent 365 entitlement, onboarding, and the selected agent/network features. |

These are source classifications, not a guarantee that a product name covers every setting. Confirm your tenant's purchased licences and Microsoft's current terms. Do not import E5 or A365 policies merely because BP policies are available.

## 🧰 Permissions and tenant preparation

Use the [Microsoft Entra admin center](https://entra.microsoft.com/) to confirm the target tenant and licences. The existing import guidance requires at least the **Conditional Access Administrator** role to manage policies. Creating groups, named locations, authentication context, or service principals may require additional permissions.

Have an authorized administrator review any API permissions and tenant-wide consent requested by the import tool. Conditional Access Administrator alone does not grant every dependency-creation or consent permission.

Plan the transition from **Security defaults** to Conditional Access. Security defaults must be disabled for the intended Conditional Access deployment, but do not disable existing protection without a reviewed replacement and recovery plan. Importing disabled policies does not itself protect the tenant.

## 🧪 Deployment readiness

Document existing policies, overlaps, tenant-specific references, affected identities, and exclusions. Prepare a small pilot and tested emergency-access accounts. Imported exclusion groups do not guarantee those accounts are excluded until membership and references are verified.

Prepare sign-in log review, the Conditional Access What If tool, and a rollback procedure. Start policies OFF, use report-only where supported, and enable only reviewed policies. Strict-location CAE policies require a separately controlled ON/OFF pilot.

Continue with [Conditional Access prerequisites](conditional-access-prerequisites.md) and [How to import](how-to-import.md).

## 📚 Microsoft sources

- [Conditional Access overview and licence requirements](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview).
- [Plan a Conditional Access deployment](https://learn.microsoft.com/en-us/entra/identity/conditional-access/plan-conditional-access).
- [Manage emergency access accounts](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access).
- [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection).
