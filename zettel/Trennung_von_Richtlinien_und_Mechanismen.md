---
id: d0e8c203-2549-4fd6-a647-cb3133367b6f
title: "Trennung von Richtlinien und Mechanismen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - designprinzip
  - softwarearchitektur
  - konfiguration
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Trennung von Richtlinien und Mechanismen]]

- **Kernkonzept:** Ein Designprinzip, bei dem [[Richtlinie|Richtlinien]] (z. B. Sicherheits- oder Konsistenzregeln) von den [[Mechanismus|Mechanismen]] zu ihrer Umsetzung getrennt werden.
- **Nutzen & Zweck:** Erhöht die Flexibilität und Wartbarkeit, da [[Richtlinie|Richtlinien]] geändert werden können, ohne die zugrundeliegenden [[Mechanismus|Mechanismen]] anzupassen.
- **Abgrenzung & Grenzen:** Kann zu erhöhter Komplexität führen, wenn zu viele Parameter konfigurierbar sind. In einfachen Systemen kann eine feste Kopplung von [[Richtlinie|Richtlinien]] und [[Mechanismus|Mechanismen]] effizienter sein.
- **Beispiel / Code:** Ein Cache-System, bei dem die [[Richtlinie]] für die Cache-Invalidierung (z. B. Zeitbasiert) unabhängig vom [[Mechanismus]] der Cache-Speicherung (z. B. LRU-Algorithmus) konfiguriert werden kann.
