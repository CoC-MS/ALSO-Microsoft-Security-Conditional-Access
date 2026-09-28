# ALSO Microsoft Security Conditional Access

Conditional Access templates are organized first by Microsoft 365 license requirement, then by configuration level, and finally by persona.

```text
Licence Required/
|-- Basic/
|-- Intermediate/
|-- Advanced/
`-- Full/
No Licence/
|-- Basic/
|-- Intermediate/
|-- Advanced/
`-- Full/
```

Each configuration level contains the following personas:

- **Global**: Policies that apply broadly to all personas or cover scenarios that are not specific to another persona.
- **Admins**: Non-guest cloud or synchronized identities assigned Microsoft Entra ID or Microsoft 365 administrative roles.
- **Internals**: Employees with accounts in the tenant who work in standard end-user roles.
- **Guests**: External users invited to the tenant with Microsoft Entra B2B guest accounts.
- **Agents**: Agent identities and agent-related resources that can be governed by Conditional Access.


