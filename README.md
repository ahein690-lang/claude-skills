# Claude Skills — H&P

Custom Claude Code skills for Hein & Partner.

## Installed Skills

### `product-architect`
Specialist for technical and functional software product conception with deep SAP expertise.

**Trigger:** "ich will ein Produkt bauen", "konzipiere", "neue App", "Produktidee", "Softwarekonzept"

**Workflow:**
1. Structured dialog (4–5 rounds): Problem → SAP relevance → MVP scope → Tech → Deployment
2. Auto-delegates to `sap-berater` agent when SAP integration is involved
3. Generates a full concept package directly into the Obsidian vault under `20_Projekte/<ProductName>/`

**Generated artifacts:**
- `00-Konzept-Overview.md` — Vision, USP, target audience
- `01-Functional-Spec.md` — Features, User Stories, acceptance criteria
- `02-Technical-Spec.md` — Architecture, stack, data model, APIs
- `03-SAP-Integration.md` — SAP objects, BAPIs, OData (only when SAP-relevant)
- `04-DevOps-Concept.md` — CI/CD, deployment, monitoring
- `05-Roadmap.md` — MVP → Phase 2 → Phase 3 with measurable milestones
- `adr/001-*.md` — Architecture Decision Records

## Installation

```bash
DEST="$HOME/.claude/plugins/marketplaces/user-local/plugins"
mkdir -p "$DEST"
git clone https://github.com/ahein690-lang/claude-skills.git /tmp/claude-skills-install
cp -r /tmp/claude-skills-install/product-architect "$DEST/"
rm -rf /tmp/claude-skills-install
```

## License
MIT
