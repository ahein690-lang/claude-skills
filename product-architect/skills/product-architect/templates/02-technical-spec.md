---
title: "<ProductName> – Technical Spec"
tags: [Projekt, <ProductName>, TechSpec, Architektur]
created: <YYYY-MM-DD>
status: draft
---

# Technical Spec: <ProductName>

## Architektur-Überblick
> Kurze Beschreibung des Architektur-Musters (z.B. "Monolith mit API-Layer", "Microservices", "Desktop-App mit lokalem Backend")

```
[Architektur-Diagramm als ASCII oder Verweis auf draw.io]
```

## Tech-Stack

| Schicht | Technologie | Begründung |
|---|---|---|
| Backend | | |
| Frontend | | |
| Datenbank | | |
| Auth | | |
| AI/LLM | | |
| Deployment | | |
| CI/CD | | |

## Datenmodell (Kernentitäten)

```python
# Beispiel-Struktur
class <Entity>(SQLModel, table=True):
    id: int = Field(primary_key=True)
    # ...
```

## API-Design

### Endpunkte (MVP)
| Method | Path | Beschreibung | Auth |
|---|---|---|---|
| GET | /api/v1/... | | |

## Externe Abhängigkeiten

| Service | Zweck | Kritikalität |
|---|---|---|
| Anthropic API | | Hoch |
| | | |

## Sicherheitsaspekte
- Auth-Strategie: <JWT/Session/OAuth2>
- Secrets-Management: <.env / Vault>
- Input-Validierung: <Pydantic / zod>
- Rate-Limiting: <ja/nein, wo>

## Skalierbarkeit & Limits (MVP)
- Erwartete Last: <X concurrent users>
- Datenwachstum: <X records/month>
- Performance-Ziel: <X ms p95>

## Verwandte ADRs
- [[adr/001-stack-choice]]
- [[adr/002-deployment-model]]
