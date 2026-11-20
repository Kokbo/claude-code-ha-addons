# Claude Code Instructions

This file contains instructions for Claude Code when working on this repository.

## Before Every Commit

**IMPORTANT:** Update `claudecode/CHANGELOG.md` with the changes being committed before making any commit. Follow the existing format:

```markdown
## [VERSION] - YYYY-MM-DD

### Added/Changed/Fixed
- Description of change
```

## Project Structure

- `repository.yaml` - Add-on repository metadata
- `claudecode/` - Claude Code add-on
  - `config.yaml` - Add-on configuration (bump version here)
  - `Dockerfile` - Container build instructions
  - `README.md` - Short intro shown in the app store before install
  - `DOCS.md` - User documentation (Documentation tab)
  - `CHANGELOG.md` - Version history (**update before commits**)
  - `apparmor.txt` - Security profile

## Version Bumping

Use `./release.sh <version> [section] "note" ["note" ...]` — it bumps the version, stamps the changelog with **today's date** (from `date`, never hand-written), commits, and pushes in one step.

If editing the changelog manually instead, ALWAYS run `date +%Y-%m-%d` first and use its output — never copy the date from a previous entry.

## Home Assistant Add-on Notes

- Rebuild button only rebuilds from cached config
- To pick up config.yaml changes: uninstall/reinstall or bump version and update
- Base image is set in the Dockerfile (`ARG BUILD_FROM=...`); `build.yaml` is deprecated, don't re-add it
- Images are built by `.github/workflows/builder.yaml` with the `home-assistant/builder` composite actions; PRs build only, the `release` branch publishes
- Base images use s6-overlay v3 - be careful with init configuration
- `init: true` uses Docker's tini, `init: false` uses s6-overlay's /init
