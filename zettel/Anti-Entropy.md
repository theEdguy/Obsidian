---
id: a5c90a0c-f1fd-417e-a0fc-73a8cf2908f5
title: "Anti-Entropy"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - konsistenz
  - gossip-protokolle
  - datenreplikation
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Anti-Entropy]]

- **Kernkonzept:** Anti-Entropy ist ein Mechanismus in [[Verteiltes System|verteilten Systemen]], um die Konsistenz von [[Daten|Datenbeständen]] zwischen [[Knoten]] durch zufälligen, periodischen Abgleich zu gewährleisten. Es verhindert die langfristige [[Divergenz]] von [[Zustand|Zuständen]] durch [[Gossip-Protokoll|gossip-basierte]] Kommunikation.
- **Nutzen & Zweck:** Das Konzept löst das Problem der [[Dateninkonsistenz]] in [[skalierbar|skalierbaren]] Systemen, indem es [[Aktualisierung|Aktualisierungen]] effizient verbreitet, ohne zentrale Koordination. Es reduziert den [[Kommunikationsaufwand]] im Vergleich zu [[Broadcast|Broadcasts]] und ist robust gegen [[Knotenausfall|Knotenausfälle]].
- **Abgrenzung & Grenzen:** Anti-Entropy ist ungeeignet für Systeme mit strengen [[Echtzeitanforderung|Echtzeitanforderungen]], da die Verbreitung [[logarithmisch]] (O(log(N))) Zeit benötigt. Es unterscheidet sich von [[2-Phase-Commit|2PC]] oder [[Paxos]] durch fehlende [[Transaktionssicherheit]] und ist nicht deterministisch. Für [[Löschoperation|Löschungen]] sind zusätzliche Mechanismen wie [[Totenschein|Totenscheine]] nötig, um [[Datenverlust]] zu vermeiden.
- **Beispiel / Code:** // Pseudocode für Push-Pull-Anti-Entropy
function synchronizeWithRandomNode() {
    const Q = selectRandomNode();
    const localUpdates = getLocalUpdatesSinceLastSync();
    const remoteUpdates = sendAndReceiveUpdates(Q, localUpdates);
    applyUpdates(remoteUpdates);
    markUpdatesAsSynced(localUpdates);
}

// Beispiel für Totenschein-Handling
function deleteValue(key) {
    const tombstone = createTombstone(key, currentTimestamp());
    propagateTombstone(tombstone); // Gossip-basierte Verbreitung
    scheduleTombstoneCleanup(tombstone, maxLifetime);
}
