---
id: 6496b947-7edb-4019-b48b-b2dbd7a26ff7
title: "Client-Server-Modell"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - kommunikation
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Client-Server-Modell]]

- **Kernkonzept:** Ein Architekturmodell, bei dem [[Client|Clients]] Anfragen an einen [[Server]] senden, der diese bearbeitet und Antworten zurückliefert. Berechnungen können dabei auf den [[Client]] verschoben werden.
- **Nutzen & Zweck:** Vereinfacht die zentrale Verwaltung von Ressourcen und Diensten, während [[Client|Clients]] entlastet oder spezifische Aufgaben übernehmen können.
- **Abgrenzung & Grenzen:** Bei hoher Last kann der [[Server]] zum Flaschenhals werden. Alternativen wie [[Peer-to-Peer]]-Modelle oder [[verteilte_Datenbanken]] sind in solchen Fällen besser geeignet.
- **Beispiel / Code:** Ein Webbrowser ([[Client]]) sendet eine HTTP-Anfrage an einen Webserver ([[Server]]), der die angeforderte Seite zurückgibt.
