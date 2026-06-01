---
id: bb1a5363-3973-45ea-a8eb-b71a8b60a2f5
title: "Totenschein (Tombstone)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - datenverwaltung
  - gossip-protokolle
  - konsistenz
  - garbage-collection
  - epidemische-algorithmen
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Totenschein (Tombstone)]]

- **Kernkonzept:** Ein [[Totenschein]] (auch [[Tombstone]]) markiert in [[verteilten System|verteilten Systemen]] das [[Löschen]] eines [[Wert|Wertes]], um dessen [[Propagierung]] trotz [[epidemischer Algorithmus|epidemischer Algorithmen]] sicherzustellen, ohne die [[Daten]] physisch sofort zu entfernen.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]], dass [[Löschoperation|Löschoperationen]] in [[gossip-basierten System|gossip-basierten Systemen]] durch [[Aktualisierung|Aktualisierungen]] anderer [[Knoten]] rückgängig gemacht werden. Es stellt sicher, dass [[Löschen]] zuverlässig propagiert wird, bis alle [[Knoten]] den [[Totenschein]] erhalten haben.
- **Abgrenzung & Grenzen:** Ein [[Totenschein]] sollte nicht genutzt werden, wenn das [[System]] keine [[epidemische Verbreitung]] von [[Daten]] verwendet oder wenn [[Löschoperation|Löschoperationen]] sofort und atomar auf allen [[Knoten]] ausgeführt werden können. Alternativen wie [[transaktionale Löschung]] oder [[zentralisierte Koordination]] sind in solchen Fällen effizienter. Zudem muss der [[Totenschein]] nach erfolgreicher [[Propagierung]] entfernt werden, um [[Speicher]]- und [[Performanceprobleme]] zu vermeiden.
- **Beispiel / Code:** // Beispiel: Totenschein in einem Key-Value-Store
{
  "key": "user:123",
  "value": null,  // Markiert als gelöscht
  "tombstone": true,  // Expliziter Totenschein
  "timestamp": 1712345678,  // Zeitstempel für Garbage Collection
  "ttl": 86400  // Maximale Lebensdauer in Sekunden
}

// Gossip-basierter Austausch zwischen Knoten:
function gossipExchange(nodeA, nodeB) {
  for (const [key, entry] of nodeA.data) {
    if (entry.tombstone && !nodeB.data.has(key)) {
      nodeB.data.set(key, entry);  // Propagiere Totenschein
    }
  }
  // ... (analog für nodeB → nodeA)
}
