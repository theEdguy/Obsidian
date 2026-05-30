---
id: 7ffea62b-d32b-4e90-a34f-6dfc897864c3
title: "Systemarchitektur"
date: 2026-05-30
tags:
  - software_engineering
  - architektur
  - design
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Systemarchitektur]]

- **Kernkonzept:** Die [[Systemarchitektur]] beschreibt die grundlegende Struktur eines Systems, einschließlich [[Komponente|Komponenten]], [[Schnittstelle|Schnittstellen]], [[Datenhaltung]] und [[Ablauflogik]]. Sie legt fest, wie das System in Teilsysteme zerlegt wird.
- **Nutzen & Zweck:** Sie schafft eine stabile Grundlage für die [[Implementierung]] und ermöglicht die [[Skalierbarkeit]], [[Wartbarkeit]] und [[Erweiterbarkeit]] des Systems. Die [[Systemarchitektur]] ist essenziell für die Kommunikation zwischen [[Stakeholder|Stakeholdern]].
- **Abgrenzung & Grenzen:** Kein Ersatz für detailliertes [[Design]] oder [[Implementierung]]. Sie beschreibt nur die grobe Struktur, nicht die konkrete Umsetzung. Im Gegensatz zu [[Datenmodellierung]] konzentriert sie sich auf die Systemebene.
- **Beispiel / Code:** ```text
Systemarchitektur:
- Frontend: Webanwendung (React)
- Backend: Microservices (Java/Spring Boot)
- Datenhaltung: PostgreSQL
- Schnittstellen: REST-API, Message Queue (RabbitMQ)
```
