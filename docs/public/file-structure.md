# 📂 File structure

[Public documentation](README.md)

This repository contains three cumulative, pre-generated Conditional Access packages. Choose one package for the tenant; do not combine them.

```text
/
├── README.md
├── Security.md
├── LICENSE
├── docs/
│   └── public/                      Deployment documentation
├── ALSO_CA_BP/                      BP policies
├── ALSO_CA_E5/                      BP + E5 policies
└── ALSO_CA_E7/                      BP + E5 + A365 policies
```

Every package contains Conditional Access policies, groups, named locations, and migration metadata. E5 and E7 also contain the authentication context required by CA106:

```text
<package>/
├── AuthenticationContext/           E5 and E7 only
├── ConditionalAccess/
├── Groups/
├── NamedLocations/
└── MigrationTable.json
```

| Package | Conditional Access | Groups | Named locations | Authentication contexts | Migration table | Total JSON files |
| --- | ---: | ---: | ---: | ---: | ---: | ---: |
| [ALSO_CA_BP](../../ALSO_CA_BP) | 34 BP | 36 | 3 | 0 | 1 | 74 |
| [ALSO_CA_E5](../../ALSO_CA_E5) | 34 BP + 3 E5 | 40 | 3 | 1 | 1 | 82 |
| [ALSO_CA_E7](../../ALSO_CA_E7) | 34 BP + 3 E5 + 5 A365 | 40 | 3 | 1 | 1 | 87 |

| Folder or file | Contents | Import consideration |
| --- | --- | --- |
| `ConditionalAccess` | Disabled Conditional Access policy exports | Review policies individually and explicitly select OFF in the import tool. |
| `Groups` | Internal, service-account, Tier 0, emergency-access exclusion, and per-policy exclusion groups | Review membership, duplicates, and all include/exclude mappings. |
| `NamedLocations` | Country locations and, where required, a compliant network location | Prepare and review locations before dependent policies. |
| `AuthenticationContext` | `ALSO-Tier0 Admins` authentication context (`c1`) in E5 and E7 | Import or map before CA106, then configure PIM role activation to request it. |
| `MigrationTable.json` | Source tenant/object mapping information | Keep with the selected package; do not import it as a policy or treat source IDs as destination IDs. |

Package totals include `MigrationTable.json`. Counts describe files, not unique destination objects or recommended assignments.

The packages are cumulative. `ALSO_CA_E5` includes the BP policies, and `ALSO_CA_E7` includes BP, E5, and A365 policies. Select the package using the [licensing guide](../../README.md#conditional-access-licensing-guide).

See the [Policy guide](conditional-access-policies.md), [Conditional Access prerequisites](conditional-access-prerequisites.md), and [How to import](how-to-import.md).
