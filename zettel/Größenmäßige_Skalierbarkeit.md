---
id: 09070b54-79d7-474d-841a-eb71673ba4ed
title: "Größenmäßige Skalierbarkeit"
date: 2026-06-01
tags:
  - verteilte_systeme
  - skalierbarkeit
  - performance
  - architektur
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Größenmäßige Skalierbarkeit]]

- **Kernkonzept:** Die Fähigkeit eines [[verteilten Systems]], eine wachsende Anzahl von [[Nutzer|Nutzern]] oder [[Prozess|Prozessen]] zu bewältigen, ohne dass die Leistung pro Nutzer signifikant abnimmt.
- **Nutzen & Zweck:** Ermöglicht es Systemen, mit steigender Nutzerzahl umzugehen, indem [[Ressource|Ressourcen]] wie [[Rechenleistung]] oder [[Speicher]] horizontal skaliert werden.
- **Abgrenzung & Grenzen:** Erfordert oft den Einsatz von Load-Balancing oder [[Replikation]], was zusätzliche Komplexität mit sich bringt. Nicht alle Anwendungen lassen sich einfach parallelisieren.
- **Beispiel / Code:** Ein Webserver-Cluster, bei dem eingehende Anfragen auf mehrere Server verteilt werden, um die Last zu balancieren.
