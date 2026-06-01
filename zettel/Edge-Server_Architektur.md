---
id: 70a2eef5-73ad-45ab-8012-214055bfad7e
title: "Edge-Server Architektur"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - verteilte-systeme
  - performance
  - cdn
  - edge-computing
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Edge-Server Architektur]]

- **Kernkonzept:** Die Edge-Server Architektur platziert [[Server|Server]] am Rand eines [[Netzwerk|Netzwerks]], nahe der [[Grenze|Grenzen]] zwischen [[Unternehmensnetzwerk|Unternehmensnetzwerken]] und dem [[Internet]], um [[Daten]] schneller und effizienter an [[Endnutzer]] auszuliefern.
- **Nutzen & Zweck:** Dieses Konzept reduziert [[Latenz]] und [[Netzwerkbelastung]] im [[Kernnetzwerk]] des Internets, indem [[Inhalte]] oder [[Dienste]] geografisch näher an die [[Nutzer]] gebracht werden. Es löst [[Probleme]] wie [[Überlastung]] zentraler [[Server]] und verbessert die [[Performance]] für [[Endnutzer]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Systeme]], die starke [[Konsistenz]] oder zentrale [[Kontrolle]] erfordern, da Edge-Server oft [[Cache|Caches]] oder [[Replikate]] nutzen. Unterscheidet sich von [[Peer-to-Peer|P2P-Systemen]] durch die hierarchische [[Struktur]] und von reinen [[Client-Server-Architekturen]] durch die dezentrale [[Platzierung]] der [[Server]].
- **Beispiel / Code:** Ein Content Delivery Network (CDN) wie Cloudflare nutzt Edge-Server, um statische [[Inhalte]] (z. B. Bilder, CSS-Dateien) von einem [[Server]] nahe dem [[Nutzer]] auszuliefern:

```
// Pseudocode für Edge-Server-Routing
if (request.region == "EU") {
    serveFrom(edgeServerEU);
} else if (request.region == "US") {
    serveFrom(edgeServerUS);
} else {
    serveFrom(originServer);
}
```
