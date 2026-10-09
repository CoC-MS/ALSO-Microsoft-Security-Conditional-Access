# 📖 Policy naming

[Public documentation](README.md)

The existing README describes the common naming format as:

```text
<MinimumLicense>-ALSO-CA###-<Persona>-<Apps>-<Platforms>-<AccessControls>-<SessionControls>
```

An actual exported example is:

```text
BP-ALSO-CA105-Admins-AllApps-AnyPlatform-Grant-PhishingResistantMFA
```

| Component | Meaning | Examples |
| --- | --- | --- |
| `MinimumLicense` | Source licence classification; verify actual feature entitlements | `BP`, `E5`, `A365` |
| `ALSO` | Template provider | `ALSO` |
| `CA###` | Policy identifier | `CA000`, `CA105`, `CA501` |
| `Persona` | Intended identity scope | `Global`, `Admins`, `Tier0Admins`, `Internals`, `ServiceAccounts`, `GuestUsers`, `Agents` |
| `Apps` | Intended resource scope | `AllApps`, `Office365`, `AdminPortals`, `SelectedApps` |
| `Platforms` | Intended device scope | `AnyPlatform`, `Windows`, `MacOS`, `iOSandAndroid` |
| `AccessControls` | Intended access action | `Grant`, `Block` |
| `SessionControls` | Descriptive control/purpose suffix; may describe a grant control rather than a session control | `RequireMFA`, `DisablePersistentBrowser`, `RequireCompliantDevice` |

Numbers group policies by persona: global `000`, administrators `100`, internals `200`, service accounts `300`, guests `400`, and agents `500` series. E5 policies CA106, CA201, and CA210 sit within the relevant persona series.

This is a descriptive convention, not a strict schema. Some exports omit components or add client-app/management scope; spellings and capitalization vary. Policy names do not guarantee the configured application, platform, licence, or action. See [Naming exceptions](naming-exceptions.md) and inspect the JSON.

Supporting groups often reuse a policy name followed by `Exclude`. Map references by object identity, not by reconstructing a filename from this convention. No names or policy assets are changed by this preview.
