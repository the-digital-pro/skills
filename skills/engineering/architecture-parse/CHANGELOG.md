# Changelog — architecture-parse

Tracks notable changes to this skill. Versions match the repo-level git
tags ([`v0.2.0`](https://github.com/the-digital-pro/skills/releases/tag/v0.2.0), …).

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Changed
- Output file is now written to the OS temporary directory
  (`$TMPDIR/<id>.json`, falling back to `/tmp/<id>.json`) instead of the
  user's current workspace. The skill prints the absolute path so the
  consumer can move the file into `public/projects/` of their visualizer
  or import it via **Import JSON**.

## [0.2.0] — 2026-05-22

### Added
- `tours[0]` walkthrough is now a **required** output. SKILL.md gains a
  dedicated "Walkthrough tour" section covering required shape, stop
  ordering (request flow), and what makes a stop note earn its place.
- Worked example in EXAMPLES.md now emits an 8-stop walkthrough that
  crosses drill-down diagram boundaries.
- REFERENCE.md adds canonical key order for `Tour` and `TourStop`.

### Changed
- Frontmatter `description` now mentions the walkthrough tour so the
  skill is selected for "walk a consumer through how this codebase
  functions" requests, not only diagram-generation requests.
- `tours` field promoted from optional to required at the project top
  level. The first tour MUST use `id: "walkthrough"`.

### Notes
- Existing project JSONs without a `tours` array are still
  structurally valid against the visualizer schema, but no longer
  match what this skill emits — re-run the skill to add the
  walkthrough.

## [0.1.0] — 2026-05-22

Initial release.

- Parses a codebase root and emits one JSON file conforming to the
  architecture-visualizer's `ProjectInputSchema`.
- Detection heuristics for Node, Python, Rust, Go, JVM ecosystems
  plus language-agnostic source-layout signals.
- 20px layout grid with recommended column/row coordinates.
- Canonical key order spec for byte-identical round-trips.
