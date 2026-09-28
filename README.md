# ALSO Microsoft Security Conditional Access policy templates

Conditional Access templates are organized in license folders  

Name structure are following

Example: Minimum license required-ALSO-CA000--Persona-TypeOfProtection-Apps-Platforms-GrantorBlock-Actions

**ALSO**- Company providing policy
**CA000**- Number of policy
**Minimum license required**- Minimum license required to use policy

**BP**- Business Premium
**E5** - Defender Suite or Microsoft 365 E5
**E7**- Microsoft 365 E7
**A365** - Agent 365 stand alone license 

**Persona**: 

  **Global**: Policies that apply broadly to all personas or cover scenarios that are not specific to another persona.
- **Admins**: Non-guest cloud or synchronized identities assigned Microsoft Entra ID or Microsoft 365 administrative roles.
- **Internals**: Employees with accounts in the tenant who work in standard end-user roles.
- **Guests**: External users invited to the tenant with Microsoft Entra B2B guest accounts.
- **Agents**: Agent identities and agent-related resources that can be governed by Conditional Access.
 
**TypeOfProtection**

Identity Protection, App Protection, Attack Surface Reduction, Base Protection

""Apps""

Apps scoped to the conditional access template policy - AllApps, Selected Apps

""Platforms**

Platform scoped to the conditional access template policy- AllPlatforms, Windows, MacOS etc

**GrantOrBlock**

Grants access or blocks access 

**Actions** 

Which actions are taken in the policy for example RequirePhishingResistantMFA, ComoliantDevice, DisablePersistantBrowser



