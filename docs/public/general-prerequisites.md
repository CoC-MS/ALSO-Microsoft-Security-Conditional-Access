# 🚀 General prerequisites

[Public documentation](README.md)

Check these items before importing Conditional Access resources into Microsoft Entra.

> [!IMPORTANT]
> The implementing partner is responsible for licence verification, compatibility review, testing, staged rollout, monitoring, and recovery. Read [Security information](../../Security.md).

## 🔐 Licensing

The repository provides three cumulative packages and classifies policies with these tags:

Choose `ALSO_CA_BP` for BP policies, `ALSO_CA_E5` for BP and E5 policies, or `ALSO_CA_E7` for BP, E5, and A365 policies. See the [main licensing guide](../../README.md#conditional-access-licensing-guide).

These are source classifications, not a guarantee that a product name covers every setting. Confirm your tenant's purchased licences and Microsoft's current terms. Do not import E5 or A365 policies merely because BP policies are available.

## 🧰 Permissions and tenant preparation


> Ensure you have Conditional Access Administrator role before importing Conditional Access policies and that your Security defaults are turned off. To check if your tenant are using Security defaults use this direct link here:

https://entra.microsoft.com/#view/Microsoft_AAD_IAM/TenantOverview.ReactView/initialValue//tabId//recommendationResourceId//fromNav/Identity

<img width="1559" height="197" alt="image" src="https://github.com/user-attachments/assets/b947568d-76d3-4a93-ae4a-5e293c68e59a" />

## 🧪 Deployment readiness

Document existing policies, overlaps, tenant-specific references, affected identities, and exclusions. Prepare a small pilot and tested emergency-access accounts. Imported exclusion groups do not guarantee those accounts are excluded until membership and references are verified.

Prepare sign-in log review, the Conditional Access What If tool, and a rollback procedure. Start policies OFF, use report-only where supported, and enable only reviewed policies. Strict-location CAE policies require a separately controlled ON/OFF pilot.

Continue with [Conditional Access prerequisites](conditional-access-prerequisites.md) and [How to import](how-to-import.md).

## 📚 Microsoft sources

- [Conditional Access overview and licence requirements](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview).
- [Plan a Conditional Access deployment](https://learn.microsoft.com/en-us/entra/identity/conditional-access/plan-conditional-access).
- [Manage emergency access accounts](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access).
- [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection).
