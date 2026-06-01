---
id: a41a3b9a-491c-4dcb-aa2b-1ca36fe47d77
title: "Hierarchisch organisierte P2P-Netzwerke"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - peer-to-peer
  - hierarchie
  - koordination
  - skalierbarkeit
  - suche
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Hierarchisch organisierte P2P-Netzwerke]]

- **Kernkonzept:** Hierarchisch organisierte [[Peer-to-Peer-System|Peer-to-Peer-Systeme]] durchbrechen die Symmetrie reiner [[P2P-Netzwerk|P2P-Netzwerke]], indem sie [[Knoten|Knoten]] mit höherer Kapazität (Super-Peers) für [[Koordination]] und [[Indexierung]] einsetzen, während schwächere Knoten (Weak Peers) an diese angebunden sind.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Skalierbarkeitsproblem]] und die [[Ineffizienz]] bei der [[Suche]] in unstrukturierten [[P2P-Netzwerk|P2P-Netzwerken]], indem es [[Lastverteilung]] und schnellere [[Datenlokalisierung]] durch zentrale [[Index-Server]] oder Super-Peers ermöglicht.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn vollständige [[Dezentralisierung]] oder [[Ausfallsicherheit]] gegen [[Single-Point-of-Failure|Single Points of Failure]] priorisiert wird. Unterscheidet sich von reinen [[P2P-Netzwerk|P2P-Netzwerken]] durch die Einführung von Hierarchie und von [[Client-Server-Modell|Client-Server-Modellen]] durch die Beibehaltung von [[Peer-to-Peer-Kommunikation|Peer-Kommunikation]] zwischen Super-Peers.
- **Beispiel / Code:** Ein Super-Peer-Netzwerk könnte wie folgt strukturiert sein:

1. Super-Peers bilden ein Overlay-Netzwerk und verwalten [[Index|Indizes]] der bei ihnen registrierten Weak Peers.
2. Weak Peers senden [[Suchanfrage|Suchanfragen]] an ihren zugeordneten Super-Peer.
3. Der Super-Peer leitet die Anfrage an andere Super-Peers weiter oder antwortet direkt, falls die [[Ressource]] lokal bekannt ist.

Beispiel-Pseudocode für eine Suchanfrage:
```
function sucheRessource(ressourceId) {
    if (this.istSuperPeer) {
        if (this.lokalerIndex.enthaelt(ressourceId)) {
            return this.lokalerIndex.get(ressourceId);
        } else {
            return this.superPeerNetzwerk.suche(ressourceId);
        }
    } else {
        return this.superPeer.suche(ressourceId);
    }
}
```
