---
id: 0aeef149-7f3c-4042-905e-c48d844fda51
title: "Epidemische Protokolle"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - replikation
  - netzwerkprotokolle
  - fehlertoleranz
  - skalierbarkeit
  - epidemische-algorithmen
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Epidemische Protokolle]]

- **Kernkonzept:** Epidemische Protokolle sind Verfahren zur [[Datenverbreitung|Datenverbreitungen]] in [[Verteilte Systeme|verteilten Systemen]], bei denen [[Aktualisierung|Aktualisierungen]] schrittweise und zufällig zwischen [[Replikat|Replikaten]] ausgetauscht werden, bis alle [[Knoten]] konsistent sind.
- **Nutzen & Zweck:** Sie lösen das Problem der [[Skalierbarkeit|skalierbaren]] und [[Fehlertoleranz|fehlertoleranten]] [[Datenreplikation|Datenreplikation]] in großen, dynamischen Netzwerken, indem sie [[Latenz|Latenzen]] und [[Netzwerküberlastung|Netzwerküberlastungen]] reduzieren. Besonders nützlich für Systeme, in denen [[Konsistenz|starke Konsistenz]] nicht zwingend erforderlich ist.
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme, die [[Strenge Konsistenz|strenge Konsistenzgarantien]] benötigen (z. B. Finanztransaktionen). Im Vergleich zu [[Baum-basiertes Multicasting|baum-basierten Multicast-Verfahren]] oder [[Flooding]] ist die Konvergenzzeit langsamer, aber die [[Robustheit]] gegenüber [[Knotenausfall|Knotenausfällen]] höher. Alternativen wie [[Message Queues]] oder [[MPI]] bieten deterministischere [[Nachrichtenübertragung|Nachrichtenübertragungen]].
- **Beispiel / Code:** // Pseudocode für ein Gossip-basiertes Protokoll (Push-Modell)
function gossipUpdate() {
    if (this.node.isInfected()) {  // Knoten hat eine Aktualisierung
        const peers = this.selectRandomPeers(3);  // Wähle 3 zufällige Nachbarn
        peers.forEach(peer => {
            peer.sendUpdate(this.node.getUpdate());  // Sende Aktualisierung
        });
    }
}

// Anti-Entropy: Periodischer Abgleich zwischen zwei Replikaten
function antiEntropySync() {
    const randomPeer = this.selectRandomPeer();
    const diff = this.compareState(randomPeer);  // Finde Unterschiede
    this.mergeUpdates(diff);  // Synchronisiere Zustände
}
