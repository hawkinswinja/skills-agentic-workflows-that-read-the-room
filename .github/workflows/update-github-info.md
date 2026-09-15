---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
model: gpt-5-mini
tools:
  edit:
  web-fetch:
  github:
    toolsets: [default, repos, pull_requests]
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    max: 1
    draft: true
    title-prefix: "[github-info] "
---

# Update GitHub Info

Update the practical GitHub information page for Mona's review.

## Required reading

1. Read `notes/mona-notes.md` from the workspace.
2. Use the `web-fetch` tool to read `https://github.blog/latest/`.
3. Use the `web-fetch` tool to read `https://github.blog/changelog/`.
4. Use the `web-fetch` tool to read `https://awesome-copilot.github.com/workflows/`.
5. Use the GitHub repository API tools for all repository guidance and reference-file reads. Do not use terminal, CLI, shell, or sandboxed commands for GitHub API reads.
6. Read `site/content/github-info.md` before editing it.

## Task

Use the official GitHub Blog, Changelog, and Awesome Copilot workflows sources to make concise, practical updates in `site/content/github-info.md`. Preserve the existing editorial angle, mention the source for every Blog, Changelog, or Awesome Copilot item, and avoid inventing details. Keep the page useful for developers learning GitHub faster.

Edit only `site/content/github-info.md`. Review the diff and confirm that the update is focused and contains no unrelated changes. Then call the `create_pull_request` safe-output tool exactly once with a clear title and body explaining the sources reviewed and the updates made. Do not push directly to `main`, and stop after creating the pull request so Mona can review it.
