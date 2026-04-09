---
name: mkdocs-markdown-writer
description: "Create or update MkDocs markdown pages for this SCADA user manual. Use when asked to draft docs, add a new section, write how-to guides, add screenshots, or produce navigation-ready .md files under docs/."
---

# MkDocs Markdown Writer

Use this skill to create high-quality markdown pages for this repository.

## Use When

- The user asks to create a new markdown page under docs/.
- The user asks to rewrite or expand existing manual content.
- The user asks to add images, step-by-step guides, notes, warnings, or links.

## Repository Context

- Documentation root: `docs/`
- Build config: `mkdocs.yml`
- Conventions reference: `docs/conventions.md`
- Theme: Material for MkDocs
- Key enabled markdown features include admonitions, tabbed content, details, task lists, and mermaid fences.

## Required Output Rules

1. Keep all output in valid Markdown.
2. Start each page with exactly one H1 heading.
3. Use concise, task-focused sections with H2/H3 headings.
4. Prefer short paragraphs and numbered steps for procedures.
5. Use relative links for internal pages and assets.
6. Place screenshots in the same folder as the page or in `docs/assets/images/` and reference with relative paths.
7. Use fenced code blocks with language tags when showing commands or config.
8. Use Material-compatible admonitions when needed:

```md
!!! note
    Helpful context.

!!! warning
    Important safety or migration information.

!!! tip
    Optional best practices.
```

## Authoring Workflow

1. Determine target file path under `docs/`.
2. If the page is new, create the file from `templates/page-template.md` and fill all placeholders.
3. If the page already exists, preserve existing terminology and style while improving clarity.
4. Validate all relative links and image references.
5. If this page should appear in navigation, propose the exact `nav` entry update for `mkdocs.yml`.

## Quality Checklist

- The title clearly describes the page purpose.
- Procedures are actionable and in logical order.
- Terminology matches existing docs (for example: project, workspace, tag, asset, device).
- Internal links resolve to existing files.
- No TODO placeholders remain.

## Response Format

When completing a request with this skill, return:

1. The created or updated markdown content.
2. The target file path.
3. Any `mkdocs.yml` nav snippet that should be added.
4. A brief list of assumptions or missing inputs.
