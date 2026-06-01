---
id: 461fc1ea-50bb-4108-b846-372e9254fa78
title: "Caching"
date: 2026-06-01
tags:
  - verteilte_systeme
  - performance
  - datenmanagement
  - netzwerk
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Caching]]

- **Kernkonzept:** Temporäres Speichern von Daten in einem schnellen Zwischenspeicher (Cache), um wiederholte Zugriffe zu beschleunigen und die Last auf [[Server]] oder Datenbanken zu reduzieren.
- **Nutzen & Zweck:** Reduziert Latenzzeiten und entlastet Backend-Systeme durch häufige Wiederverwendung von Daten.
- **Abgrenzung & Grenzen:** Nicht geeignet für Daten, die sich häufig ändern oder starke [[Konsistenz]] erfordern. Cache-Inkonsistenzen können auftreten.
- **Beispiel / Code:** Ein Webbrowser speichert häufig besuchte Seiten im Cache, um Ladezeiten zu verkürzen.
