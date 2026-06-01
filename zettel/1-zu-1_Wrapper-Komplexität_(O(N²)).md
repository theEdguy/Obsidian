---
id: eb41d280-b66b-44ab-8884-9947d1814a04
title: "1-zu-1 Wrapper-Komplexität (O(N²))"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - middleware
  - integration
  - komplexität
  - verteilte-systeme
  - wrapper
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[1-zu-1 Wrapper-Komplexität (O(N²))]]

- **Kernkonzept:** Die [[1-zu-1|1-zu-1]]-Wrapper-Architektur erfordert für jede [[Anwendung]] einen dedizierten [[Wrapper]] pro anderer [[Anwendung]], was zu quadratischer [[Komplexität]] (O(N²)) führt, wenn N [[Anwendung|Anwendungen]] integriert werden müssen.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der [[Integration]] heterogener [[Schnittstelle|Schnittstellen]] in [[Legacy-System|Legacy-Systemen]] oder [[Middleware]], indem es [[Kompatibilität]] zwischen [[Anwendung|Anwendungen]] herstellt, die nicht direkt miteinander kommunizieren können.
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit vielen [[Anwendung|Anwendungen]], da der [[Aufwand]] für [[Implementierung]] und [[Wartung]] der [[Wrapper]] mit N² skaliert. Alternativen wie [[Broker-Architektur|Broker-Architekturen]] (O(N)) sind effizienter. Zudem erhöht sich die [[Latenz]] durch zusätzliche [[Abstraktion|Abstraktionsebenen]].
- **Beispiel / Code:** Angenommen, es gibt 3 Anwendungen A, B und C:
- A benötigt Wrapper für B und C.
- B benötigt Wrapper für A und C.
- C benötigt Wrapper für A und B.

Ergebnis: 3 × (3–1) = 6 Wrapper (O(N²)).

Kontrast zur Broker-Lösung:
- Jede Anwendung kommuniziert nur mit dem Broker (3 Wrapper für A, B, C + 3 vom Broker zu den Anwendungen = 6 Wrapper, aber linear skalierbar: O(N)).
