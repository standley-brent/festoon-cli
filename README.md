# festoon

The command-line client for [Festoon](https://app.festoon.dev): shared memory for your team's AI tools.

Festoon gathers the decisions, constraints and terminology that come out of AI-assisted work, groups them by project, and hands them back to every AI tool your team uses. A decision made in one Claude Code session is known in the next one, and in Cursor, VS Code and Claude Desktop too.

This repository publishes the CLI's release binaries. You don't need to clone it.

## Install

```sh
curl -fsSL https://get.festoon.dev | sh
```

This installs a single self-contained binary to `~/.local/bin/festoon`. No Python, package manager or `sudo` needed. If that directory isn't on your `PATH`, the installer tells you the line to add.

Supported platforms: **macOS** (Apple Silicon and Intel) and **Linux** (x64).

Installer options, set as environment variables:

| Variable | Default | |
|---|---|---|
| `FESTOON_INSTALL_DIR` | `~/.local/bin` | Where to put the binary |
| `FESTOON_VERSION` | `latest` | A specific release tag, e.g. `v0.1.1` |

You can also download a binary directly from [Releases](https://github.com/standley-brent/festoon-cli/releases).

## Get started

You need a Festoon account: sign up at [app.festoon.dev](https://app.festoon.dev), or accept an invitation from your team. Then:

```sh
festoon join
```

`join` opens your browser to sign in. It then:

- installs Claude Code hooks, so each session starts with your project's shared context and contributes back what it learns when it ends
- registers Festoon's MCP server with the AI tools it finds: Claude Code, Cursor, Windsurf, VS Code and Claude Desktop

Run `festoon join --no-hooks` or `--no-mcp` to skip either part.

## Commands

| Command | |
|---|---|
| `festoon join` | Sign in and connect this machine |
| `festoon status` | Show sign-in, hooks, and whether capture is working |
| `festoon context` | Print the shared context for the current repository |
| `festoon init-repo` | Add Festoon instructions to a repository's AI rules files, for tools without hooks |
| `festoon connect` | Re-register the MCP server in your AI tools |
| `festoon upgrade` | Update to the latest release |
| `festoon leave` | Remove Festoon from this machine and sign out everywhere (`--dry-run` to preview) |

## Privacy

- **See exactly what's recorded:** [app.festoon.dev/privacy](https://app.festoon.dev/privacy) describes what Festoon records and how to stop it.
- **Exclude a repository:** add an empty `.festoonignore` file at its root. Nothing from sessions inside that repository leaves your machine. The check runs in the CLI, not on the server.
- **Stop completely:** `festoon leave` removes the hooks and MCP registrations and revokes your sign-in on every machine.

## Updating

```sh
festoon upgrade
```

`festoon status` also tells you when a newer release is available.
