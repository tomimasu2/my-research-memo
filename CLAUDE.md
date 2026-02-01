# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a research note-taking repository for studying causal inference and related topics. The project uses:
- **Obsidian** for note management (configured in `.obsidian/`)
- **Zotero** for academic paper management with PDF linking via `zotero://` links
- **Markdown** for all content with YAML frontmatter for metadata

## Directory Structure

- `article/` - Research papers and notes, organized by citation key (e.g., `athey2016jul.md`, `gao2025.md`)
- `template/code/` - Zotero export template for automatically generating markdown files from Zotero library
- `Inbox/` - Capture area for notes (Obsidian convention)

## Key Patterns

### Article/Paper Files

Each paper note follows this structure:

```yaml
---
title: "Paper Title"
Tags: [optional tags]
Publisher: "[optional]"
DOI: https://doi.org/[DOI]
cite key: [citation_key]
description: [optional description]
rating: [optional rating]
---
## Projects
## ノート (Notes section with Japanese headers)
## AI要約 (AI Summary section)
## 注釈 (Annotations section)
```

### Zotero Integration

The `template/code/zotero_integration.md` file is a Zotero export template that uses Jinja2 templating syntax. When exporting from Zotero, it automatically:
- Generates markdown frontmatter from paper metadata
- Creates links to PDF files via `zotero://select/` protocol
- Preserves annotations and comments from Zotero
- Organizes notes by collection

Key template variables include:
- `{{title}}`, `{{DOI}}`, `{{publicationTitle}}`, `{{citekey}}`
- `{{collections}}` - Zotero collections the paper belongs to
- `{{annotations}}` - Extracted annotations with colors and page numbers
- `{% persist %}` blocks - Prevent Zotero re-exports from overwriting manual notes

### Language

The repository uses both English and Japanese. Japanese headers (`ノート`, `注釈`) are standard in this workflow.

## Development Notes

- Do not modify the Zotero template structure unless updating Zotero export format
- When adding new papers, maintain the citation key convention in filenames
- Manual notes should be placed within `{% persist %}` blocks in the template to survive re-exports
- The `.obsidian` directory contains Obsidian vault configuration; modifications affect the editor experience

# GitHub 運用ルール
- **URL:** `https://github.com/tomimasu2/my-research-memo`
- **ツール:** GitHub操作（接続・起票・閲覧）には必ず `gh` コマンドを使用すること。

## Language Rules

- **Internal thinking**: English
- **Responses to user**: Japanese (日本語)

Claude Code should conduct all internal analysis and reasoning in English, but provide all user-facing responses in Japanese.
