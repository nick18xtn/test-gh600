---
name: update-github-info
description: Draft concise updates for Mona's GitHub Info site from GitHub Blog and Changelog sources, then open a pull request for review.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
tools:
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before drafting any update.

Follow repository guidance from the project itself and read public references with web-fetch when needed.

Use `web-fetch` to read these external sources:
- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Also read repository guidance or reference files through the GitHub repository API tools, not through terminal commands, CLI helpers, or sandboxed commands.

Use the GitHub Blog, GitHub Changelog, and Awesome Copilot workflows as sources for new updates. Keep the content concise, practical, and aimed at developers learning GitHub faster.

Update `site/content/github-info.md` with the best available information, preserving Mona's editorial angle and citing sources when content comes from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows.

Before finalizing the work, check the syntax of the agentic workflow configuration is valid and that the YAML frontmatter is well-formed.

Open a pull request for Mona to review using `safe-outputs` with `create-pull-request`. Do not write directly to `main`.

The pull request should summarize the changes made to `site/content/github-info.md`, mention the GitHub Blog, GitHub Changelog, and Awesome Copilot workflows as sources, and make it easy for Mona to review before publishing.

## Usage

This workflow runs on a daily schedule and can also be triggered manually with `workflow_dispatch`.
