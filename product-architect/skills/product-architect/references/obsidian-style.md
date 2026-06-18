# Obsidian Style Guide — OpenClaw Wiki

## Frontmatter (every document)

```yaml
---
title: "<Dokumenttitel>"
tags: [Projekt, <ProductName>, <Kategorie>]
created: <YYYY-MM-DD>
status: draft | in-review | approved | archived
version: "1.0"
---
```

## Linking conventions
- Link to related docs: `[[02-Technical-Spec]]`, `[[../10_SAP/SAP_BP_Migration]]`
- Link to existing wiki concepts when relevant (e.g. `[[S4HANA_Transformation_Projektstruktur]]`)
- Use `> [!NOTE]` / `> [!WARNING]` / `> [!TIP]` callouts for important info

## Section structure
- H1: Document title (repeat from frontmatter)
- H2: Major sections
- H3: Subsections
- Tables for comparisons and structured data
- Code blocks with language tags for all code/config/XML

## File naming
- `00-Konzept-Overview.md` (zero-padded numbers for sort order)
- `adr/001-stack-choice.md` (three-digit ADR numbers)
- Slugs: lowercase, hyphens, no umlauts in filename (umlauts OK in content)
