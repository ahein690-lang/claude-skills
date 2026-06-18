# Architecture Decision Record (ADR) Guide

## Format

```markdown
---
title: "ADR-<NNN>: <Entscheidungstitel>"
tags: [ADR, <ProductName>]
created: <YYYY-MM-DD>
status: proposed | accepted | deprecated | superseded
---

# ADR-<NNN>: <Entscheidungstitel>

## Status
accepted

## Kontext
<Warum musste diese Entscheidung getroffen werden? Welche Kräfte/Constraints spielen eine Rolle?>

## Entscheidung
<Was wurde entschieden? Konkret und eindeutig.>

## Alternativen (die verworfen wurden)
- **<Alternative A>** — verworfen weil: <Grund>
- **<Alternative B>** — verworfen weil: <Grund>

## Konsequenzen
**Positiv:**
- <Vorteil 1>
- <Vorteil 2>

**Negativ / Trade-offs:**
- <Nachteil 1>
- <Risiko 1>

## Review-Datum
<YYYY-MM-DD> — <Unter welchen Bedingungen sollte diese Entscheidung revisited werden?>
```

## Standard ADRs to always create

1. **001-stack-choice** — Backend language/framework, frontend approach, database
2. **002-deployment-model** — VPS/cloud/desktop, containerized/systemd, scaling approach
3. **003-sap-connectivity** (if SAP relevant) — RFC vs OData vs IDoc vs CPI
4. **004-auth-strategy** — OAuth2/JWT/session, which provider
5. **005-ai-integration** (if AI features) — which model, direct API vs abstraction layer
