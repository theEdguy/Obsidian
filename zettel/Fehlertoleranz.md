---
id: 966a4b91-1649-43db-a483-769052b589d9
title: "Fehlertoleranz"
date: 2026-06-01
tags:
  - verteilte_systeme
  - zuverlässigkeit
  - fehlerbehandlung
  - architektur
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Fehlertoleranz]]

- **Kernkonzept:** [[Fehlertoleranz]] bezeichnet die Fähigkeit eines [[verteilten Systems]], auch bei Ausfällen einzelner [[Knoten]] oder Netzwerkkomponenten weiterhin korrekt zu funktionieren.
- **Nutzen & Zweck:** Erhöht die Zuverlässigkeit und Verfügbarkeit eines [[verteilten Systems]], indem Ausfälle kompensiert werden. Löst das Problem der Anfälligkeit für Hardware- oder Netzwerkfehler.
- **Abgrenzung & Grenzen:** Erfordert zusätzliche Ressourcen (z. B. [[Replikation]] oder Redundanz) und erhöht die Komplexität des Systems. Nicht alle Fehler können toleriert werden (z. B. byzantinische Fehler).
- **Beispiel / Code:** Ein Beispiel ist das [[Byzantinische Fehlermodell]], bei dem ein [[verteiltes System]] auch dann korrekt funktioniert, wenn einige [[Knoten]] fehlerhafte oder böswillige Nachrichten senden.
