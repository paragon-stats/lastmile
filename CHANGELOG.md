# Changelog

All notable changes to this plugin are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and this project
adheres to [Semantic Versioning](https://semver.org).

## [0.1.0] - 2026-10-10

### Added

- `lastmile` skill (open Agent Skills format): a behavioural harness that stops
  an agent deferring the last mile of work. A seven-rung gate runs before
  reporting completion, deferring anything, or opening a branch, issue or merge
  request; a bundle test decides whether adjacent work travels with the change;
  an avoidance test catches large work done to dodge small work. Composes with
  `blastradius` (how much process a change earns) and `ponytail` (how much to
  build).
- Packaging as a single-plugin marketplace, so the skill installs and updates
  through `claude plugin` instead of a copied directory.
- CI inherited from the `techdocs-authoring` template: manifest-driven SemVer
  release via release-please, structural validation of plugin and skill
  frontmatter, and CodeQL scanning of GitHub Actions workflows.
