# Changelog

All notable changes to this plugin are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/) and this project
adheres to [Semantic Versioning](https://semver.org).

## [0.2.0](https://github.com/paragon-stats/lastmile/compare/v0.1.0...v0.2.0) (2026-10-10)


### Features

* add the stop rule, derived rather than assumed ([8035fdc](https://github.com/paragon-stats/lastmile/commit/8035fdcbcba5b5e5749f7e3420fb84815c1f1ab1))
* make the self-auditing report the default, not an opt-in ([a343771](https://github.com/paragon-stats/lastmile/commit/a3437715f6c35840ce52417c394972f8c01b4653))
* run the bundle test before opening a branch, issue or merge request ([9c7d49c](https://github.com/paragon-stats/lastmile/commit/9c7d49cefb293e4e973a2ee06283460f884647cf)), closes [#3](https://github.com/paragon-stats/lastmile/issues/3)
* the avoidance test and gate rung 7, doing large work to avoid small work ([b373951](https://github.com/paragon-stats/lastmile/commit/b3739515f6f8cf6fd09b878f0a4565c91e0ad906)), closes [#5](https://github.com/paragon-stats/lastmile/issues/5)
* the avoidance test, and the bundle test before branching ([518098e](https://github.com/paragon-stats/lastmile/commit/518098ec2aaa15cc503c328846687bfb03c748fd))
* the lastmile harness ([e266e8a](https://github.com/paragon-stats/lastmile/commit/e266e8a17e929b6a022e1fbcc2d8f5397a76205f))

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
