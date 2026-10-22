# 🚀 General prerequisites

[Public documentation](README.md)

Check these items before importing Conditional Access resources into Microsoft Entra.

> [!IMPORTANT]
> The implementing partner is responsible for licence verification, compatibility review, testing, staged rollout, monitoring, and recovery. Read [Security information](../../Security.md).

## 🔐 Licensing

The repository provides three cumulative packages and classifies policies with these tags:

Choose `ALSO_CA_BP` for BP policies, `ALSO_CA_E5` for BP and E5 policies, or `ALSO_CA_E7` for BP, E5, and A365 policies. See the [main licensing guide](../../README.md#conditional-access-licensing-guide).


## 🧰 Permissions 


> Ensure you have at least Conditional Access Administrator role before importing Conditional Access policies.


## Tenant preparation BP policies

Security defaults needs to be turned off. To check if your tenant are using Security defaults use this direct link here:

https://entra.microsoft.com/#view/Microsoft_AAD_IAM/TenantOverview.ReactView/initialValue//tabId//recommendationResourceId//fromNav/Identity

<img width="1913" height="954" alt="image" src="https://github.com/user-attachments/assets/bf17814a-ab3a-4a48-a917-69408977ac07" />

If you don't see this option, you should see the message: "Your organization is currently using Conditional Access."

If you're unable to switch it off, your tenant does not have an Entra ID P1 license.

## Tenant preparation E5 policies

Ensure that your Entra ID Protection are ok and that you have Entra ID P2 license on tenant 


Ensure that Entra ID Protection is enabled and that your tenant has an Entra ID P2 license.

Direct link: https://entra.microsoft.com/#view/Microsoft_AAD_IAM/TenantOverview.ReactView/initialValue//tabId//recommendationResourceId//fromNav/Identity

<img width="1620" height="582" alt="image" src="https://github.com/user-attachments/assets/436a8f15-9c77-46ba-b578-4236a76163cc" />


## Tenant preparation E7 policies

For Agent 365 policies

1. Ensure that Agent 365 licenses are assigned to your users
2. Check that your Agent 365 is provisioned in your tenant. It should be operative. Direct link: Agent 365 Overview

   You can double-check whether you are able to select Agents in Conditional Access manually. If the option is not greyed out, then you are good to go. 

For Global Secure Access policies

1. Check that your Global Secure Access is provisioned in your tenant. Direct link: https://entra.microsoft.com/#view/Microsoft_Azure_Network_Access/ForwardingProfile.ReactView

<img width="1880" height="1049" alt="image" src="https://github.com/user-attachments/assets/2d3abc95-9f5d-4596-9edd-80873d993133" />

2. And activate adaptive access: https://entra.microsoft.com/#view/Microsoft_Azure_Network_Access/Security.ReactView

<img width="1863" height="1083" alt="image" src="https://github.com/user-attachments/assets/022195a6-d05f-4f59-840a-4e085c8aa489" />



## 🧪 Deployment readiness

Document existing policies, overlaps, tenant-specific references, affected identities, and exclusions. Prepare a small pilot and tested emergency-access accounts. Imported exclusion groups do not guarantee those accounts are excluded until membership and references are verified.

Prepare sign-in log review, the Conditional Access What If tool, and a rollback procedure. Start policies OFF, use report-only where supported, and enable only reviewed policies. Strict-location CAE policies require a separately controlled ON/OFF pilot.

Continue with [Conditional Access prerequisites](conditional-access-prerequisites.md) and [How to import](how-to-import.md).

## 📚 Microsoft sources

- [Conditional Access overview and licence requirements](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview).
- [Plan a Conditional Access deployment](https://learn.microsoft.com/en-us/entra/identity/conditional-access/plan-conditional-access).
- [Manage emergency access accounts](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/security-emergency-access).
- [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection).

**Disclaimer:** Licensing prerequisites and feature availability listed on this page may be incorrect, incomplete, or outdated. We strongly recommend verifying all licensing information against the latest official Microsoft licensing documentation before making any purchasing or deployment decisions.

**Enterprise licenses:** [Microsoft Enterprise Plan Comparison](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/education/Modern-Work-Plan-Comparison-Enterprise.pdf)

**SMB licenses:** [Microsoft SMB Plan Comparison](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/bade/documents/products-and-services/en-us/education/Modern-Work-Plan-Comparison-Enterprise.pdf)
