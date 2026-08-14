# Diagrams

> This folder is intentionally near-empty. Here's why, and where diagrams actually live.

## Where the diagrams actually are

Every diagram in this playbook (30+ Mermaid flowcharts, quadrant charts, and Gantt charts) lives **inline** in the Markdown file it illustrates, right next to the prose it supports. This follows [CONTRIBUTING.md](../CONTRIBUTING.md)'s guidance directly: *"Use Mermaid for diagrams — keep visuals in Markdown so they're easy to maintain and render on GitHub."*

Keeping a diagram next to its explanation means:
- It stays in sync when the prose changes (no separate file to forget to update)
- It renders directly on GitHub/GitLab without a build step
- A reader never has to jump between two files to understand one concept

## So what is this folder for?

This folder exists to satisfy the top-level repository structure listed in the root [README.md](../README.md), which calls out `diagrams/` as a home for "visual assets (Mermaid source files)." In practice, no standalone diagram source files have been needed yet — every diagram has a natural home inline.

If you're contributing a diagram that's genuinely shared across multiple pages (not tied to one page's narrative), or a visual asset that isn't a Mermaid diagram (e.g., a screenshot), this is the right place for it. Otherwise, put your Mermaid diagram inline in the relevant topic file.

## Status

🟢 Active — intentionally sparse. See [CONTRIBUTING.md](../CONTRIBUTING.md) for the diagram convention.
