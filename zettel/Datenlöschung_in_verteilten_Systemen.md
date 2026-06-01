---
id: e4ed371e-3508-4688-ac78-3ab34cf5941d
title: "Datenlöschung in verteilten Systemen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - datenmanagement
  - konsistenz
  - gossip-protokolle
  - epidemische-algorithmen
  - garbage-collection
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Datenlöschung in verteilten Systemen]]

- **Kernkonzept:** In [[verteiltes System|verteilten Systemen]] ermöglicht die Datenlöschung das sichere Entfernen von [[Information|Informationen]] durch [[Totenschein|Totenscheine]], um die [[Konsistenz]] trotz [[epidemischer Algorithmus|epidemischer Verbreitung]] zu wahren. Ohne diese Technik würden gelöschte [[Daten]] durch [[Gossip-Protokoll|Gossip-Protokolle]] wiederhergestellt.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]], dass [[Löschoperation|Löschoperationen]] in [[verteilte Datenhaltung|verteilten Datenhaltungen]] durch [[Replikation]] und [[asynchrone Kommunikation]] unterlaufen werden. Es stellt sicher, dass [[Daten]] dauerhaft entfernt werden, ohne durch [[Aktualisierung|Aktualisierungen]] anderer [[Knoten]] rückgängig gemacht zu werden.
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit extrem hoher [[Dynamik]] (z. B. häufige [[Knotenausfall|Knotenausfälle]]), da die [[Garbage Collection]] von [[Totenschein|Totenscheinen]] eine stabile [[Topologie]] voraussetzt. Alternativen wie [[transaktionale Löschung]] oder [[zentralisierte Steuerung]] bieten strengere [[Konsistenzgarantie|Garantien]], sind aber weniger [[skalierbar]].
- **Beispiel / Code:** // Pseudocode: Totenschein-basierte Löschung in einem Gossip-Protokoll
function deleteData(key) {
    // 1. Erstelle Totenschein mit globaler ID und Ablaufzeit
    tombstone = {
        id: generateUUID(),
        key: key,
        expiry: currentTime() + TOMBSTONE_LIFETIME
    };
    
    // 2. Verbreite Totenschein via Push-Pull-Gossip
    gossipBroadcast(tombstone);
    
    // 3. Lokale Löschung erst nach Bestätigung
    localStore.remove(key);
}

// Gossip-Runde: Synchronisiere Totenscheine
function gossipRound() {
    peer = selectRandomPeer();
    peerTombstones = peer.requestTombstones();
    
    // Wechselseitiger Abgleich
    for (tombstone in peerTombstones) {
        if (!localTombstones.contains(tombstone.id)) {
            localTombstones.add(tombstone);
            localStore.remove(tombstone.key);
        }
    }
    
    // Garbage Collection nach Ablauf
    if (currentTime() > tombstone.expiry) {
        initiateGlobalCollection(tombstone.id);
    }
}
