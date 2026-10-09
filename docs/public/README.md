# 🛡️ ALSO Microsoft Security - Conditional Access documentation

Partner-facing guidance for reviewing and deploying the Conditional Access exports in this repository.

> [!NOTE]
> This documentation accompanies the [preview README](../../README.preview.md). The existing root README and policy assets have not been replaced by this preview.

> [!IMPORTANT]
> Confirm licensing, settings, references, dependencies, and exclusions before use. Import policies in **OFF** state, preserve emergency access, and validate a controlled pilot.

| Page | Purpose |
| --- | --- |
| 🚀 **[General prerequisites](general-prerequisites.md)** | Check licences, permissions, and rollout readiness. |
| 🛡️ **[Conditional Access prerequisites](conditional-access-prerequisites.md)** | Prepare identity, application, device, location, and agent dependencies. |
| 🔐 **[Policy guide](conditional-access-policies.md)** | Review exported controls by persona. |
| 📖 **[Policy naming](policy-naming.md)** | Understand naming components and licence tags. |
| 🏷️ **[Naming exceptions](naming-exceptions.md)** | Understand current names and settings that need special review. |
| 📂 **[File structure](file-structure.md)** | Locate policies and supporting exports. |
| 📥 **[How to import](how-to-import.md)** | Import selected resources and validate in Entra. |
| 🐛 **[Reporting issues](reporting-issues.md)** | Report problems safely. |

Start with the prerequisites, review selected policies and their dependencies, then follow the import guide. Read the repository's [Security information](../../Security.md) and [License](../../LICENSE).

## Viewing and adopting the preview

Open `README.preview.md` at the repository root in a Markdown preview, for example VS Code's **Open Preview** (`Ctrl+Shift+V`). The Copilot Editor canvas can also render the file. No site generator or dependency installation is required. GitHub renders the page when it is later published on a branch; these uncommitted local files are not yet available on GitHub.

All preview documentation and export links are relative to their actual file locations. External links point to existing services or repositories; there are no placeholder links to future pages.

To adopt manually later:

1. Keep this `docs/public` directory at the same path.
2. Copy the contents of root `README.preview.md` into root `README.md` and remove its **Documentation preview** note. Both files are at the same directory level, so its resource links need no path changes.
3. Change the preview link above from `../../README.preview.md` to `../../README.md` and remove this page's preview note and this adoption section. **That link change is for future adoption only**; the current link intentionally opens the preview.
4. Review the existing README's detailed descriptions and screenshots before replacing it. This guide summarizes each exported policy and preserves import illustrations, while calling out differences between prose, names, and settings. Retain any additional wording you still need.

No policy changes or import actions are required to adopt the documentation layout.
