---
id: 061dc256-a4d7-43c0-bf79-efe372ea63c0
title: "Informationsverbreitung in verteilten Systemen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - gossip-protokolle
  - epidemische-algorithmen
  - skalierbarkeit
  - datenreplikation
  - fehlertoleranz
  - konsistenzmodelle
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Informationsverbreitung in verteilten Systemen]]

- **Kernkonzept:** Die [[Informationsverbreitung]] in [[verteiltes System|verteilten Systemen]] nutzt epidemische Algorithmen wie Gossip-basierte Protokolle, um [[Aktualisierung|Aktualisierungen]] effizient und skalierbar an alle [[Knoten]] zu verbreiten, ohne zentrale Steuerung.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der effizienten und fehlertoleranten Verbreitung von [[Daten]] in großen, dynamischen [[Netzwerk|Netzwerken]], wo klassische [[Multicast]]-Methoden an Skalierbarkeit oder Robustheit scheitern. Es ermöglicht [[Konsistenz]] und [[Synchronisation]] ohne Single Point of Failure.
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit strikten [[Echtzeit]]-Anforderungen oder garantierter [[Zustellung]], da Gossip-Protokolle probabilistisch arbeiten. Alternativen wie [[deterministisch]]e [[Broadcast]]-Verfahren oder [[zentralisiert]]e [[Koordination]] bieten höhere Zuverlässigkeit, aber geringere Skalierbarkeit. Bei [[Datenlöschung|Datenlöschungen]] sind zusätzliche Mechanismen wie [[Totenschein|Totenscheine]] nötig, um [[Rückpropagierung]] zu verhindern.
- **Beispiel / Code:** ```python
# Pseudocode für Push-Pull-Gossip-Austausch
def gossip_push_pull(node_p, node_q):
    # Knoten P sendet seine Aktualisierungen an Q
    updates_p = node_p.get_updates()
    node_q.receive_updates(updates_p)
    
    # Knoten Q sendet seine Aktualisierungen an P
    updates_q = node_q.get_updates()
    node_p.receive_updates(updates_q)
    
    # Beide Knoten haben nun identische Daten
```

**Erläuterung**: Nach O(log(N)) Runden (N = Anzahl [[Knoten]]) ist die [[Aktualisierung]] mit hoher Wahrscheinlichkeit im gesamten System verbreitet. Die Stopp-Wahrscheinlichkeit *p_stop* im Gerüchte-Modell beeinflusst die Verbreitungskurve (s. Formel: *s = e^(-(1/p_stop + 1)(1-s))*).
