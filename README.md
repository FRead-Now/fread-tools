# fread-tools

The command-line tools FRead's editors prepare works with, released for macOS,
Linux and Windows. Each [release](https://github.com/FRead-Now/fread-tools/releases)
says which catalog schema it serves and which commits it was built from.

| Tool | What it does |
| --- | --- |
| `ingest-gutenberg-html` | Ingest a Project Gutenberg book, or re-ingest one from its pin |
| `ingest-override` | Record a correction that survives re-ingest: a block's kind or text, an image, a footnote's role |
| `ingest-work` | Edit a detached work by hand (export, edit, import), or create a work from a file |
| `ingest-notes` | Place notes and images on a work from a TOML file |
| `ingest-audiobook` | Import a recording's alignment as an audiobook bridged to its text |
| `fread-admin` | Inspect and manage works in the catalog |

It installs [fux](https://github.com/MarcelInTO/fux), the editor works are
edited in, and FRead's snippet library for it.

## Install

On macOS or Linux, with [Homebrew](https://brew.sh):

```sh
brew install marcelinto/tap/fux fread-now/tap/fread-tools
```

fux is named beside fread-tools because it comes from its own tap, and
Homebrew installs a formula from another tap only when you name it: that
taps it and records that you trust it. Later, `brew upgrade` updates both.

On Windows, with [Scoop](https://scoop.sh):

```powershell
scoop bucket add fread https://github.com/FRead-Now/scoop-bucket
scoop install fread-tools
```

Upgrade with `brew upgrade fread-tools` or `scoop update fread-tools` when the
operator tells you a new release is out. Check what you have with
`ingest-work --version`:

```
ingest-work v0.1.0 (schema 53)
```

## Matched to the catalog

The tools work against FRead's working catalog, at the schema they were built
for, and refuse any other:

- "*the working catalog is at schema 52, these tools need 53*": the catalog is
  behind your tools. Ask the operator to migrate it.
- "*… these tools were built for 53: upgrade the tools*": your tools are behind
  the catalog. Upgrade them.

You need database credentials and network access from the operator before any
tool can reach the catalog. Nothing in this repository grants either.

## Licence

© FRead. All rights reserved. You may download and run these tools to prepare
works for FRead. The open-source components they are built from, and their
licences, are listed in `THIRD-PARTY-NOTICES.md` in every release archive.

This repository holds the releases only. The tools are built from FRead's
private sources, and the release, the tap and the bucket are published by that
build; the file here is overwritten at every release.
