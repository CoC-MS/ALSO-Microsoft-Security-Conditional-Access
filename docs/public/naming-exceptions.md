# 🏷️ Naming exceptions

[Public documentation](README.md)

The Windows example has a short-name exceptions page. Conditional Access instead needs guidance on existing naming variations and name/setting mismatches. There is no evidence of a separate short-name export scheme here.

| Export or name | Current exception | Action before use |
| --- | --- | --- |
| CA004 | `Globa` rather than `Global` | Use the existing filename; inspect the authentication-flow conditions. |
| CA206 | `DIsablePersistentBrowser` capitalization | Do not assume normalized spelling when locating the export. |
| CA208, CA209, CA300 | Omit components of the common naming format | Use the policy number and actual JSON rather than parsing a fixed component count. |
| CA102 exclusion group | Group name says `RequireSigninFrequency12H`; policy specifies 8 hours | Map the actual group ID and review membership, not the suffix alone. |
| CA301 exclusion groups | Two files differ by a space before `.json` | Inspect both object identities and migration mappings; do not import duplicate-looking groups blindly. |
| Global country location | Name ends `(NO)`, but export includes `NO`, `NL`, `BE`, `LU` | Review all four countries before enabling CA001. |
| CA104 | Name says `AllApps`; export targets `None` | Set the intended supported resources before deployment. |
| CA203 | Name says `IntuneEnrollment`; export targets Microsoft Intune | Review enrollment targeting and service principal prerequisites. |
| CA505 | Name says `Grant` and `AllResources`; export blocks outside a compliant network and targets `AllAgentIdResources` | Validate the configured action, location, and resource scope. |

The [Policy guide](conditional-access-policies.md) summarizes actual controls. The original README remains unchanged, including descriptions that differ from current settings. This documentation preview does not silently rename files, normalize exported names, or correct policy JSON.

Long filenames can also exceed Windows extraction/path limits. Use a short extraction path and, if needed, a long-path-capable archive tool; verify all exports are present before importing.
