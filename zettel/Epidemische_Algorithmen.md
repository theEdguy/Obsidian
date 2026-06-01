---
id: 753b16c1-43ed-4b9e-8cad-93b832db2f62
title: "Epidemische Algorithmen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - gossip-protokolle
  - fehlertoleranz
  - skalierbarkeit
  - datenreplikation
  - netzwerkkommunikation
  - epidemische-algorithmen
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Epidemische Algorithmen]]

- **Kernkonzept:** Epidemische Algorithmen nutzen [[Gossip-Protokoll|Gossip-Protokolle]] zur dezentralen und fehlertoleranten Verbreitung von [[Information|Informationen]] in [[Verteiltes System|verteilten Systemen]], inspiriert von der Ausbreitung von [[Krankheit|Krankheiten]] oder Gerüchten.
- **Nutzen & Zweck:** Sie lösen das Problem der effizienten und skalierbaren [[Datenverbreitung]] in großen, dynamischen [[Netzwerk|Netzwerken]], wo klassische [[Multicast-Kommunikation|Multicast-Verfahren]] aufgrund von [[Skalierbarkeit|Skalierbarkeitsproblemen]] oder [[Fehlertoleranz|Fehlertoleranzanforderungen]] versagen. Besonders nützlich für [[Aktualisierung|Aktualisierungen]] in [[Replikation|replizierten Systemen]] oder [[Datenbank|Datenbanken]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn deterministische [[Konsistenzgarantie|Konsistenzgarantien]] (z. B. [[Starke Konsistenz]]) oder sofortige [[Propagierung]] erforderlich sind. Alternativen wie [[2-Phasen-Commit]] oder [[Paxos]] bieten stärkere [[Synchronisation]], sind aber weniger skalierbar. Epidemische Algorithmen können [[Datenverlust]] nicht vollständig ausschließen und erfordern zusätzliche Mechanismen (z. B. [[Totenschein|Totenscheine]]) für [[Löschoperation|Löschoperationen]].
- **Beispiel / Code:** ```python
# Pseudocode für Push-Pull-Gossip-Austausch
import random

def gossip_push_pull(node, network):
    # Wähle zufälligen Knoten Q aus dem Netzwerk
    q = random.choice(network.nodes)
    if q != node:
        # Tausche Aktualisierungen mit Q aus
        updates_from_q = q.get_updates()
        node.send_updates(q)
        node.apply_updates(updates_from_q)
```

**Erläuterung**: Ein Knoten wählt zufällig einen anderen Knoten aus und tauscht mit diesem [[Aktualisierung|Aktualisierungen]] aus. Nach O(log(N)) Runden sind alle Knoten im [[System]] synchronisiert.
