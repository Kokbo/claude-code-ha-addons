# Claude Code HA Add-ons

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Open your Home Assistant instance and add this repository](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FKokbo%2Fclaude-code-ha-addons)

Home Assistant add-ons for running [Claude Code](https://docs.anthropic.com/en/docs/claude-code) inside your smart home.

## Add-ons

| Add-on | Description |
|--------|-------------|
| [Claude Code](claudecode/) | AI assistant for automations, debugging, and smart home management |
| [Auto-Monocle](auto-monocle/) | Auto-discover HA cameras and expose to Alexa via Monocle Gateway |
| [Playwright Browser](playwright-browser/) | Headless Chromium with CDP endpoint for browser automation |

## Installation

1. Click the badge above, or go to **Settings** → **Add-ons** → **Add-on Store** → **⋮** → **Repositories** and add:

   ```
   https://github.com/Kokbo/claude-code-ha-addons
   ```

2. Install the add-on you want from the store and start it.
3. Open the Claude Code web terminal from the sidebar and log in. See the [Claude Code README](claudecode/README.md) for details.

Requires Home Assistant OS or a Supervised installation (amd64 or aarch64).

## Highlights of the Claude Code add-on

- **Web terminal in the sidebar**, with optional tmux session persistence that survives browser refreshes
- **Home Assistant integration** through hass-mcp, with read-only tools pre-authorized
- **Optional browser automation** via Playwright MCP together with the Playwright Browser add-on
- **Login link as a notification:** the OAuth link shows up in the Home Assistant notification bell, because the container has no browser
- **Safe updates:** Claude Code can update itself on startup, and a release that fails to run on your hardware is rolled back automatically
- **Selectable model** and prebuilt images from GitHub Container Registry

## Documentation

- [Claude Code add-on](claudecode/README.md) · [changelog](claudecode/CHANGELOG.md)
- [Auto-Monocle add-on](auto-monocle/README.md) · [changelog](auto-monocle/CHANGELOG.md)
- [Playwright Browser add-on](playwright-browser/README.md) · [changelog](playwright-browser/CHANGELOG.md)

## Credits

This repository is a fork of [apbb2/claude-code-ha-addons](https://github.com/apbb2/claude-code-ha-addons), which is itself based on [robsonfelix/robsonfelix-hass-addons](https://github.com/robsonfelix/robsonfelix-hass-addons) by Robson Felix. The fork by apbb2 substantially rewrote the startup, update, and security architecture of the Claude Code add-on.

## License

MIT License — see [LICENSE](LICENSE)
