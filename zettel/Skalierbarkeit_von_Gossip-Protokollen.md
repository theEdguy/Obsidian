---
id: 478bffda-b2b8-444f-a84f-c77de4a861e8
title: "Skalierbarkeit von Gossip-Protokollen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - skalierbarkeit
  - epidemische_algorithmen
  - netzwerkkommunikation
  - fehlertoleranz
  - datenverbreitung
  - gossip_protokolle
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Skalierbarkeit von Gossip-Protokollen]]

- **Kernkonzept:** Gossip-Protokolle ermöglichen effiziente und robuste Verbreitung von [[Information|Informationen]] in [[verteilte Systeme|verteilten Systemen]] durch zufälligen [[Knoten|Knoten]]-Austausch, wobei die [[Skalierbarkeit]] durch logarithmische [[Runde|Runden]] (O(log(N))) erreicht wird.
- **Nutzen & Zweck:** Sie lösen das [[Problem]] der [[Datenverbreitung]] in großen, dynamischen [[Netzwerk|Netzwerken]], indem sie [[Redundanz]] nutzen, um [[Fehlertoleranz]] und [[Lastverteilung]] zu verbessern – ohne zentrale [[Koordination]] oder komplexe [[Topologie]]-Kenntnisse.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Anwendung|Anwendungen]], die deterministische [[Konsistenz]] oder sofortige [[Propagierung]] erfordern. Im Vergleich zu [[Baum-basierte Protokolle|baum-basierten Protokollen]] (z. B. [[Multicast-Bäume]]) verursachen sie höhere [[Netzwerk]]-Last durch [[Nachricht]]en-Redundanz. Bei [[Löschoperation|Löschoperationen]] sind zusätzliche Mechanismen (z. B. [[Totenschein|Totenscheine]]) nötig, um [[Daten]]-Konsistenz zu wahren.
- **Beispiel / Code:** ```python
# Pseudocode für Push-Pull-Gossip-Austausch
def gossip_push_pull(node_p, node_q):
    # Knoten P sendet seine Aktualisierungen an Q
    updates_p = node_p.get_updates()
    node_q.receive_updates(updates_p)
    
    # Knoten Q sendet seine Aktualisierungen an P
    updates_q = node_q.get_updates()
    node_p.receive_updates(updates_q)
    
    # Beide Knoten haben nun identische Informationen
```

**Erläuterung**: Nach O(log(N)) Runden (N = Anzahl [[Knoten]]) ist die [[Information]] im gesamten [[System]] verbreitet. Die [[Wahrscheinlichkeit]] p_stop im Gerüchte-Modell steuert die [[Terminierung]] des Algorithmus.
