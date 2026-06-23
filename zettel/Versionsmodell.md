---
id: ba4390a8-423f-4b61-bf57-00a96c7a1a80
title: "Versionsmodell"
date: 2026-06-24
tags:
  - software_engineering
  - prozessmodelle
  - versionierung
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Versionsmodell]]

- **Kernkonzept:** Ein [[iteratives_Prozessmodell]], bei dem ein [[Software-System]] in [[Versionen]] unterteilt wird, die schrittweise entwickelt und ausgeliefert werden.
- **Nutzen & Zweck:** Ermöglicht frühe [[Nutzerfeedback]]-Integration und [[Risikostreuung]] durch schrittweise [[Auslieferung]]. Grundlage für [[Continuous_Delivery]].
- **Abgrenzung & Grenzen:** Komplexer als [[Wasserfallmodell]], da [[Versionen]] koordiniert werden müssen. Unterscheidet sich von [[Spiralmodell]] durch Fokus auf [[Auslieferung]]. Nicht geeignet für [[Monolithische_Systeme]].
- **Beispiel / Code:** ```text
// Beispiel für Versionsplanung
Version 1.0: Kernfunktionalität (MVP)
Version 1.1: Erweiterte Features
Version 2.0: Skalierbarkeit und Performance
```
