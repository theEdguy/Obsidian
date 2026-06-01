---
id: 8ac1d2e9-5c99-4266-8cdf-18efc794d7d5
title: "Time-To-Live (TTL)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - verteilte-systeme
  - koordination
  - peer-to-peer
  - routing
  - ressourcenmanagement
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Time-To-Live (TTL)]]

- **Kernkonzept:** Time-To-Live (TTL) ist ein Mechanismus, der die [[Lebensdauer|Lebensdauer]] eines [[Datenpaket|Datenpakets]] oder einer [[Anfrage|Anfrage]] in einem [[Netzwerk]] begrenzt, indem eine maximale Anzahl von [[Sprung|Sprüngen]] (Hops) oder eine Zeitspanne festgelegt wird.
- **Nutzen & Zweck:** TTL verhindert endlose [[Zirkulation|Zirkulationen]] von [[Datenpaket|Datenpaketen]] oder [[Anfrage|Anfragen]] in [[verteilte Systeme|verteilten Systemen]], reduziert [[Netzwerkbelastung|Netzwerkbelastungen]] und vermeidet [[Ressourcenverschwendung|Ressourcenverschwendungen]] durch unkontrollierte [[Propagation|Propagation]].
- **Abgrenzung & Grenzen:** TTL ist ungeeignet, wenn [[Daten]] dauerhaft verfügbar sein müssen oder wenn die [[Topologie]] des [[Netzwerk|Netzwerks]] dynamisch und unvorhersehbar ist. Alternativen wie [[Quittungsmechanismus|Quittungsmechanismen]] oder [[Zeitstempel]] können in solchen Fällen besser geeignet sein. In [[strukturierte P2P-Systeme|strukturierten P2P-Systemen]] wird TTL oft durch präzisere [[Routing-Algorithmus|Routing-Algorithmen]] ersetzt.
- **Beispiel / Code:** In einem unstrukturierten [[Peer-to-Peer-System|P2P-System]] wird eine Suchanfrage mit einem TTL-Wert von 5 initiiert:
```
// Pseudocode für Flooding mit TTL
function floodSearch(query, ttl) {
  if (ttl <= 0) return;
  for (neighbor in neighbors) {
    if (!neighbor.hasSeen(query)) {
      neighbor.searchLocally(query);
      neighbor.floodSearch(query, ttl - 1);
    }
  }
}
```
