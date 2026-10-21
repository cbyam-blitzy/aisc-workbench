# Set up on a new machine

Last updated: 2026-10-21. Refresh when plugin commands, repository names,
authentication requirements, or shared-reference loading change.

Clone this repository, install its local plugin, and use the checkout as your
working project. The repository includes the reusable skills, shared guidance,
and templates. Meeting access and customer materials require separate setup.

## Prerequisites

- Git and access to this GitHub repository.
- A signed-in Codex environment with plugin support. The commands below require
  the Codex CLI; desktop use also requires a compatible desktop app.
- An authorized Wispr Flow MCP connection for workflows that retrieve meeting
  context. Document review and rewriting can use supplied files without it.

No application build, package installation, or Git submodule initialization is
required for this repository's current contents.

## Clone and install

Run these commands in a terminal. Choose a parent directory where you want to
keep the checkout; it does not need to match the original machine's path.

```sh
git clone https://github.com/cbyam-blitzy/wispr.git
cd wispr
codex plugin marketplace add . --json
codex plugin add wispr-flow-agent-playbooks@wispr-flow --json
```

These are the current repository, marketplace, and plugin names. If the project
is renamed, update this runbook and the relevant manifests together.

For desktop use, restart the app and start a new chat in this checkout. Search
for a skill by its exact name, such as `$blitzy-review-aap` or
`$blitzy-humanizer`.

The local marketplace is defined in
[`marketplace.json`](../.agents/plugins/marketplace.json), and the skills are
declared in [`plugin.json`](../plugin.json). OpenAI installs local plugins into
a cache; see the [official plugin packaging documentation](https://developers.openai.com/plugins/build/plugins).

## Connect meeting context and prepare local files

Configure and authenticate Wispr Flow's MCP connection separately in the target
environment, using the authorized account and your organization's connection
instructions. This skills-only plugin does not configure the server or carry
credentials. Confirm the connection exposes the intended meeting tools before
running a meeting-based workflow.

Customer files under `accounts/` are Git-ignored and do not arrive with a clone.
Supply any needed transcripts or artifacts through an authorized transfer, or
retrieve meeting context through Wispr Flow. Keep local fallback transcripts in
`accounts/<account>/transcripts/`. Use only a transcript matching the requested
meeting and identify it as the fallback source.

Keep customer material and private MCP configuration out of version control.
The repository's [`AGENTS.md`](../AGENTS.md) defines the handling rules.

## Verify the setup

From the checkout root:

```sh
codex plugin marketplace list --json
git status --short --branch
```

Confirm `wispr-flow` resolves to this checkout and the install command returned
an `installedPath`. To compare installed skills with the checkout, replace the
placeholder below with that returned path:

```sh
diff -qr skills /path/from/installedPath/skills
```

No output and exit status 0 mean the skill directories match. In a new chat,
invoke `$blitzy-humanizer` on a short fictional sentence to check discovery and
execution without customer data. Confirm the agent can read
`shared_context/standards/writing_style_guide.md` from the checkout.

This runbook is based on repository inspection, local CLI help, and the linked
OpenAI documentation. A clean second-machine installation has not yet been
tested.

## Use and maintain the installation

Keep the checkout available and open it as the working project. Skills locate
current shared guidance in the working repository, including when the skill
itself runs from the plugin cache. Installing the plugin alone does not make
shared-reference discovery reliable from unrelated projects.

After pulling changes into a clean checkout, refresh the installed plugin with
`codex plugin add wispr-flow-agent-playbooks@wispr-flow --json`. Compare the
installed skills again, then restart the desktop app and start a new chat.
See [Refresh after changing skills](../README.md#refresh-after-changing-skills)
for the full refresh procedure.

If a command is unavailable, check `codex plugin --help` and use a CLI version
that supports local marketplaces. If skills are missing, verify marketplace
registration, refresh the cached install, and start a new chat. If shared guides
cannot be found, open the repository as the working project. If meeting tools
are unavailable, check the separate Wispr Flow connection and authorization.
