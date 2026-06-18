---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch: {}
  schedule:
    - cron: '0 12 * * *'
permissions:
  contents: read
  issues: read
  pull-requests: read
tools:
  edit: {}
  web-fetch: {}
safe-outputs:
  create-pull-request:
    title-prefix: "[Mona GitHub Info]"
    draft: true
    fallback-as-issue: false
network:
  allowed:
    - defaults
    - github.blog
---

# Update GitHub Info content

Read `notes/mona-notes.md` before making any content updates.

Use these sources:
- `notes/mona-notes.md`
- `https://github.blog/latest/`
- `https://github.blog/changelog/`

Update `site/content/github-info.md` with concise, reader-friendly GitHub updates sourced from the GitHub Blog and GitHub Changelog.
Mention the source of each update and keep summaries practical for developers.

If there is nothing new or no actionable website update, call `noop` with a short reason.
Do not write directly to `main`.
Use `safe-outputs` with `create-pull-request` so changes are proposed in a PR for Mona to review.
Open a pull request with a title that mentions Mona or GitHub Info.
