---
name: update-github-info
description: Draft Mona website updates from official GitHub sources and propose them as a pull request.
on:
  workflow_dispatch: {}
  schedule:
    - cron: '0 9 * * *'
permissions:
  contents: read
tools:
  edit: {}
  web-fetch: {}
safe-outputs:
  create-pull-request:
    title-prefix: "[Mona website] "
    draft: true
    fallback-as-issue: false
network:
  allowed:
    - defaults
    - github.com
    - github.blog
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` first, and use the following sources for updates:

- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Update `site/content/github-info.md` with concise, practical content that reflects the latest GitHub Blog and GitHub Changelog updates.

Use the `edit` tool to modify the local file and `web-fetch` to retrieve live content from GitHub Blog and GitHub Changelog.

Open a pull request for Mona to review using `safe-outputs` with `create-pull-request`.
Do not write directly to `main`.

If there is nothing new to update, call `noop` with a clear reason.
