# 🏷️ Naming exceptions

[Public documentation](README.md)

Conditional Access needs guidance on existing naming variations and name/setting mismatches. There is no separate short-name export scheme here.

| Export or name | Current exception | Action before use |
| --- | --- | --- |
| CA206 | `DIsablePersistentBrowser` capitalization | Do not assume normalized spelling when locating the export. |
| CA208, CA209, CA300 | Omit components of the common naming format | Use the policy number and actual JSON rather than parsing a fixed component count. |
| CA102 exclusion group | Group name says `RequireSigninFrequency12H`; policy specifies 4 hours | Map the actual group ID and review membership, not the suffix alone. |
| CA301 exclusion groups | Two files differ by a space before `.json` | Inspect both object identities and migration mappings; do not import duplicate-looking groups blindly. |
| CA203 | Name says `IntuneEnrollment`; export intentionally uses Microsoft Intune as an example application target | Register the Microsoft Intune Enrollment service principal manually, then replace the example target before deployment. |

The [Policy guide](conditional-access-policies.md) summarizes actual controls. This documentation does not silently rename files, normalize exported names, or correct policy JSON.

Long filenames can also exceed Windows extraction/path limits. Use a short extraction path and, if needed, a long-path-capable archive tool; verify all exports are present before importing.
