# Claude Code HA Apps

[![Builder][builder-badge]][builder-url]
[![Claude Code version][version-badge]](claudecode/CHANGELOG.md)
![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
[![License: MIT][license-badge]](LICENSE)

[![Open your Home Assistant instance and show the add app repository dialog with a specific repository URL pre-filled.](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2FKokbo%2Fclaude-code-ha-addons)

Home Assistant apps (called add-ons before Home Assistant 2026.2) for running [Claude Code](https://docs.anthropic.com/en/docs/claude-code) inside your smart home.

## Apps

| App | Description |
|-----|-------------|
| [Claude Code](claudecode/) | AI assistant for automations, debugging, and smart home management |
| [Auto-Monocle](auto-monocle/) | Auto-discover HA cameras and expose to Alexa via Monocle Gateway |
| [Playwright Browser](playwright-browser/) | Headless Chromium with CDP endpoint for browser automation |

## Installation

1. Click the button above, or go to **Settings** → **Apps** → **App store** → **⋮** → **Repositories** and add:

   ```
   https://github.com/Kokbo/claude-code-ha-addons
   ```

2. Install the app you want from the store and start it.
3. Open the Claude Code web terminal from the sidebar and log in. See the [Claude Code documentation](claudecode/DOCS.md) for details.

Requires Home Assistant OS or a Supervised installation (amd64 or aarch64).

## Highlights of the Claude Code app

- **Web terminal in the sidebar**, with optional tmux session persistence that survives browser refreshes
- **Home Assistant integration** through hass-mcp, with read-only tools pre-authorized
- **Optional browser automation** via Playwright MCP together with the Playwright Browser add-on
- **Login link as a notification:** the OAuth link shows up in the Home Assistant notification bell, because the container has no browser
- **Safe updates:** Claude Code can update itself on startup, and a release that fails to run on your hardware is rolled back automatically
- **Selectable model** and prebuilt images from GitHub Container Registry

## Documentation

- [Claude Code app](claudecode/DOCS.md) · [changelog](claudecode/CHANGELOG.md)
- [Auto-Monocle app](auto-monocle/README.md) · [changelog](auto-monocle/CHANGELOG.md)
- [Playwright Browser app](playwright-browser/README.md) · [changelog](playwright-browser/CHANGELOG.md)

## Credits

This repository is a fork of [apbb2/claude-code-ha-addons](https://github.com/apbb2/claude-code-ha-addons), which is itself based on [robsonfelix/robsonfelix-hass-addons](https://github.com/robsonfelix/robsonfelix-hass-addons) by Robson Felix. The fork by apbb2 substantially rewrote the startup, update, and security architecture of the Claude Code add-on.

## License

MIT License — see [LICENSE](LICENSE)

[builder-badge]: https://github.com/Kokbo/claude-code-ha-addons/actions/workflows/builder.yaml/badge.svg
[builder-url]: https://github.com/Kokbo/claude-code-ha-addons/actions/workflows/builder.yaml
[version-badge]: https://img.shields.io/badge/dynamic/yaml?url=https%3A%2F%2Fraw.githubusercontent.com%2FKokbo%2Fclaude-code-ha-addons%2Fmain%2Fclaudecode%2Fconfig.yaml&query=%24.version&label=claude%20code%20app
[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[license-badge]: https://img.shields.io/badge/License-MIT-yellow.svg
