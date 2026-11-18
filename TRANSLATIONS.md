# Translations / 多语言翻译

> English is the single source of truth. Every other language is a 1:1 mirror of it.
> 英文原文为唯一事实来源，其他语言均为它的 1:1 镜像。

This fork is structured for i18n from the start: any language can be added
without changing the English source or any other language.

## Languages / 语言一览

| Language | Code | Status | Files | Maintainer |
| --- | --- | --- | --- | --- |
| English (source) | `en` | ✅ Original, upstream | `README.md`, `00-…-45-…/`, `glossary/` | upstream: hacrex |
| 简体中文 | `zh-CN` | ✅ Complete, 2026-11-18 | `README.zh-CN.md`, `zh-CN/` (51 files) | matf5 |
| Your language | `<locale>` | ⬚ Not started | `README.<locale>.md`, `<locale>/` | — |

## How a language is laid out / 一个语言长什么样

Using `zh-CN` as the example, and `<locale>` as any BCP 47 code
(`ja`, `es`, `pt-BR`, `fr`, `de`, `ko`, `zh-TW`, …):

```
README.<locale>.md          # full translation of README.md, links point into <locale>/
<locale>/                   # 1:1 mirror, same folder names, file names and order as English
  00-introduction/README.md
  …
  45-multi-modal-vibe-coding/README.md
  glossary/terms.md
  Blueprint.md
  CONTRIBUTING.md
  RESOURCES.md
  ROADMAP.md
```

Rules, shared by every language (see `TRANSLATION.md` for the full list):

1. Translate prose, headings, tables and lists only. Never change code
   blocks, commands, URLs, link targets, file paths, variable names or badges.
2. Heading count, table rows, list items and code fences must match the
   English file one-to-one; verify with a script before submitting.
3. Keep the English file untouched. A translation PR touches only its own
   `<locale>/` and `README.<locale>.md`.
4. Content changes go to the English source first (upstream), then to each
   translation. A translation PR must not invent new content.
5. Proper nouns (Cursor, Ollama, RAG, MCP, Kubernetes, Docker, React, …),
   numbers, percentages, sources and years stay as in the original.

## Adding a new language / 新增一种语言

1. File an issue titled `[i18n] Add <Language> (<locale>)` so people know
   you are working on it and to claim maintainership.
2. Fork this repo, copy `zh-CN/` to `<locale>/`, copy `README.zh-CN.md`
   to `README.<locale>.md`, and translate file by file.
3. Add your language to the table above, with yourself as maintainer.
4. Submit one PR per language (or per section group for a large language).
   The maintainer reviews in that language before merging.

## Syncing with upstream / 与上游同步

Upstream (`hacrex/the-vibe-coding-handbook`) updates in English. To sync:
fetch upstream, diff the English files, re-translate only the changed
paragraphs in each locale, keep structure and counts in sync, then update
the upstream commit recorded in `TRANSLATION.md` and re-run verification.

## Fork-only changes / Fork 专属改动

The language-switcher lines at the top of `README.md` (`Read this in
other languages: …`), `README.zh-CN.md` (`其他语言版本：…`) and the
`[English 原文](…)` link at the top of every `zh-CN/<section>/README.md`
are fork-only additions — upstream has none of them. They are plain link
lines, not headings/tables/lists/code, so they do not affect the 1:1
structure counts. After an upstream sync overwrites `README.md`, re-add
the switcher line; do not treat its absence as an upstream change and do
not drop it.
