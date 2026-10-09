# 📂 File structure

[Public documentation](README.md)

This repository contains one set of pre-generated Conditional Access exports, not Windows packages, an application, or a build tool.

```text
/
├── README.md                         Existing documentation (unchanged)
├── README.preview.md                 Proposed landing page
├── Security.md
├── LICENSE
├── docs/
│   └── public/                       Preview documentation
└── ALSO_CA/
    ├── AuthenticationContext/        1 JSON export
    ├── ConditionalAccess/            41 JSON exports
    ├── Groups/                       40 JSON exports
    ├── NamedLocations/               3 JSON exports
    └── MigrationTable.json           Source mapping metadata
```

| Folder or file | Contents | Import consideration |
| --- | --- | --- |
| [ConditionalAccess](../../ALSO_CA/ConditionalAccess) | 33 BP, 3 E5, and 5 A365 policy exports; all currently disabled | Choose policies individually and explicitly select OFF in the import tool. |
| [Groups](../../ALSO_CA/Groups) | Internal, service-account, Tier 0, emergency-access exclusion, and per-policy exclusion groups | Review membership, duplicates, and all include/exclude mappings. |
| [NamedLocations](../../ALSO_CA/NamedLocations) | Two country locations and one compliant network location | Prepare locations before policies that reference them. |
| [AuthenticationContext](../../ALSO_CA/AuthenticationContext) | `ALSO-Tier0 Admins` context | Map the context for CA106 and configure role activation separately. |
| [MigrationTable.json](../../ALSO_CA/MigrationTable.json) | Source tenant/object mapping information | Keep with the export set for the tool's migration workflow; do not import as a policy or treat source IDs as destination IDs. |

There are **86 JSON files** in `ALSO_CA`, including migration metadata. Counts reflect files, not unique destination objects or recommended assignments. The duplicate-looking CA301 exclusion files remain unchanged.

There is no `build-manifest.json`, package assembly step, or Basic/Adv choice in this repository. Policy numbers and licence tags help navigation but do not replace reviewing settings and dependencies.

See [Policy guide](conditional-access-policies.md), [Conditional Access prerequisites](conditional-access-prerequisites.md), and [How to import](how-to-import.md).
