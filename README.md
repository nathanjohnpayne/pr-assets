# pr-assets

Review evidence, mostly screenshots, for issues and pull requests across the `nathanjohnpayne` fleet. Files here are embedded in issue and PR bodies and comments so reviewers can see what changed.

## Purpose

This repository is a store, not a project. It is never merged into anything, and nothing here is built, deployed or depended on. Do not clone it for development work: it only grows, and nothing in it is meant to be edited after upload.

GitHub's drag-and-drop attachments work only in the web interface, so agents and scripts upload evidence here instead. Screenshots never go into a code repository, and never onto a branch of one.

## Layout

```text
<repo>/<issue-or-PR-number>/<file>
_smoke/<file>
```

- `<repo>` is the source repository's name under `nathanjohnpayne`, for example `nathanpaynedotcom`.
- `<issue-or-PR-number>` is the issue or pull request the evidence belongs to.
- `_smoke/` holds upload and rendering checks only, not review evidence.

Embeds use a `raw.githubusercontent.com` URL pinned to the commit that added the file, for example `https://raw.githubusercontent.com/nathanjohnpayne/pr-assets/<commit-sha>/<repo>/<number>/<file>`. Pinning to a commit, not to `main`, means a reviewed image cannot change underneath the review.

## Privacy bar

Everything here is public, so every file must meet the same bar as a public PR body:

- Nothing from signed-in analytics or vendor dashboards.
- No personal data: no names, email addresses, phone numbers, account identifiers or customer records, in the image or in its filename.
- Nothing from a private repository.

In this first version the repository hosts screenshots from public repositories only. Evidence from a private repository never lands here, even when the image itself looks harmless; use an approved private method instead, or report that none is available.

## Retention

Keep everything. Old issues and PRs embed these files by commit SHA, and those embeds keep working only while the commits stay reachable from `main`. So:

- Never rewrite history on `main`.
- Never delete a file, even an obsolete one.
- Never delete `main` or force-push to it.

A file that should not have been uploaded is a privacy incident for the owner to handle, not something to clean up with a routine commit.

## How uploads happen

Uploads go through Mergepath's canonical upload script, which is being added under [nathanjohnpayne/mergepath#2938](https://github.com/nathanjohnpayne/mergepath/issues/2938). That issue, and the Mergepath documentation it adds, describe the command and its checks. The script commits the files under the layout above and prints Markdown image lines pinned to the resulting commit. Any push made another way, such as a `_smoke/` check, follows the same layout, privacy and retention rules.

## Who pushes

Only the owner's author identity, `nathanjohnpayne`, pushes here, using an identity-checked credential scoped to this repository with the minimum permissions needed. The identity and the destination are verified before every write. Reviewer identities, bots and ambient `gh` authentication do not push here.
