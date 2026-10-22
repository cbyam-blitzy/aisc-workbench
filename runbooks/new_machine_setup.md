# Set up and maintain AISC Workbench

Last updated: 2026-10-22. Refresh when installation commands, plugin identifiers,
authentication requirements, or reference loading change.

Install the local plugin from a checkout, use that checkout as the working
project, and refresh the cached skills after updates. Meeting access and
customer files require separate setup.

## Prerequisites

Have repository access and a signed-in Codex environment with local plugin support.

- Install Git and a Codex CLI that provides `codex plugin` commands.
- For desktop use, have a compatible signed-in desktop app.
- Follow the [Wispr Flow MCP setup runbook](wispr_flow_mcp_setup.md) to configure
  an authorized connection for meeting retrieval.
  Supplied-document review does not require that connection.
- No application build, package installation, or submodule initialization is
  required for this repository's current contents.

## Install from a checkout

Clone the repository, register its marketplace, and install the skills plugin.
Choose a local parent directory; the commands do not depend on a particular
username or absolute path.

```sh
git clone https://github.com/cbyam-blitzy/aisc-workbench.git
cd aisc-workbench
codex plugin marketplace add . --json
codex plugin add aisc-workbench@aisc-workbench --json
```

The repository and marketplace are named `aisc-workbench`. Install the plugin
using `aisc-workbench@aisc-workbench`; its marketplace display name is
**AISC Workbench**. These are the names in the current
[plugin manifest](../plugin.json) and
[marketplace catalog](../.agents/plugins/marketplace.json).

Open the checkout as your working project. For desktop use, restart the app
and start a new chat. In the chat composer, type `$` followed by the exact
skill name, such as `$blitzy-humanizer`, then add your task and inputs.
Use `$`, not `/`, to invoke these skills; do not enter skill requests in
the terminal. See the [usage instructions and skill summaries](../README.md#how-to-run-a-skill)
for examples and required inputs. Keep the checkout available: cached skills
read shared standards and references from the working repository.

## Connect meeting evidence and local files

Authenticate meeting access separately and supply customer files only through
an authorized local workflow.

- Follow the [Wispr Flow MCP setup runbook](wispr_flow_mcp_setup.md) for server
  registration, browser authorization, retrieval verification, and troubleshooting.
  This skills-only plugin supplies neither the server nor credentials.
- `accounts/` is Git-ignored and absent from a fresh clone. Retrieve meeting
  context through Wispr Flow or supply authorized local artifacts as needed.
- Put fallback transcripts in `accounts/<account>/transcripts/`. Use only the
  transcript matching the requested meeting and identify the fallback source.
- Keep customer evidence and private MCP configuration out of Git. Follow
  [AGENTS.md](../AGENTS.md) for handling and authorization rules.

## Verify the installation

Check marketplace registration, cached skills, and access to live shared standards.
Run commands from the checkout root.

```sh
codex plugin marketplace list --json
```

Confirm `aisc-workbench` resolves to this checkout. The install command returns
`installedPath`; replace the placeholder below with that value:

```sh
diff -qr skills /path/from/installedPath/skills
```

No output and exit status 0 mean the installed skills match the checkout.
In a new chat, send this skill request in the chat composer:

```text
$blitzy-humanizer Rewrite this sentence naturally and return only the final version: We would like to confirm the remaining technical inputs.
```

Confirm it returns a rewrite and the agent can read these files from the
working project:

- `shared_context/standards/writing_style_guide.md`
- `shared_context/standards/readability_directives.md`
- `shared_context/standards/file_naming_directives.md`

Local marketplace registration, plugin refresh, and skill-copy comparison were
verified on 2026-10-21. A clean second-machine installation remains untested.

## Refresh after updates

Refresh the installed cache after changing or pulling skills; saving the
checkout alone does not refresh installed skills.

1. Review local changes before pulling repository updates.
2. From the checkout root, run:

   ```sh
   codex plugin add aisc-workbench@aisc-workbench --json
   ```

3. Compare `skills/` with the returned `installedPath/skills` as above.
4. Restart the desktop app and start a new chat.

The refresh includes saved, uncommitted skill edits. Skills read shared
references from the checkout, so keep those files current as well.

## Troubleshooting

Resolve registration and project access before diagnosing individual skills.

| Symptom | Action |
| --- | --- |
| Marketplace is missing or points to an old checkout path | From the current checkout root, run `codex plugin marketplace add . --json`, refresh the plugin, and verify registration again |
| Upgrading an installation with a previous plugin name | Remove the previous plugin with `codex plugin remove OLD_PLUGIN@OLD_MARKETPLACE --json` and its marketplace with `codex plugin marketplace remove OLD_MARKETPLACE --json`; then register this checkout and install `aisc-workbench@aisc-workbench` |
| Checkout was moved | Reopen the project at its new location and re-register its marketplace from that directory |
| A skill does not appear when using `/` | Type `$` in the chat composer and use its exact skill name; `/` does not invoke these repository skills |
| Skills are missing or outdated | Refresh the plugin, compare installed skills, restart the app, and start a new chat |
| Shared references cannot be found | Use the full checkout as the working project; a plugin installed into an unrelated project may not locate them |
| Meeting tools are unavailable | Follow the [Wispr Flow MCP troubleshooting steps](wispr_flow_mcp_setup.md#troubleshooting) and verify retrieval |
| `codex plugin` commands are unavailable | Check `codex plugin --help` and use a CLI version supporting local marketplaces |

## Appendix — Sources and evidence

Installation guidance follows the current repository configuration and locally
verified commands; desktop cache behavior is described in the official documentation.

- **Plugin packaging and local marketplaces:** [OpenAI plugin packaging documentation](https://developers.openai.com/plugins/build/plugins).
- **Repository configuration:** [plugin manifest](../plugin.json),
  [marketplace catalog](../.agents/plugins/marketplace.json), and
  [project enablement](../.codex/config.toml).
- **Verification boundary:** local registration, refresh, and skill comparison
  were exercised on 2026-10-21; fresh-machine onboarding was not exercised.
