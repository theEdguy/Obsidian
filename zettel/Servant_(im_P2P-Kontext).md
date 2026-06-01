---
id: e926d4d4-e891-44fd-8c67-898ab57f33ea
title: "Servant (im P2P-Kontext)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - peer-to-peer
  - architektur
  - middleware
  - dezentralisierung
  - koordination
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Servant (im P2P-Kontext)]]

- **Kernkonzept:** Ein [[Servant|Servant]] ist ein [[Prozess|Prozesse]] in [[Peer-to-Peer-System|Peer-to-Peer-Systemen]], der gleichzeitig als [[Client|Clients]] und [[Server|Server]] agiert und somit symmetrische [[Rolle|Rollen]] in der [[Kommunikation]] übernimmt.
- **Nutzen & Zweck:** Der [[Servant|Servant]] löst das [[Problem]] der [[Zentralisierung]] in [[verteilten Systemen]], indem er [[Dezentralisierung]] ermöglicht. Er vermeidet [[Engpässe]] durch [[Single-Point-of-Failure]] und fördert [[Skalierbarkeit]] sowie [[Ausfallsicherheit]] durch gleichberechtigte [[Knoten|Knoten]].
- **Abgrenzung & Grenzen:** Ein [[Servant|Servant]] ist ungeeignet für [[Anwendung|Anwendungen]], die [[starke Konsistenz]] oder [[zentrale Kontrolle]] erfordern, wie z. B. [[Transaktionssysteme]]. Im Vergleich zu [[Client-Server-Architekturen]] erhöht er die [[Komplexität]] der [[Koordination]] und [[Synchronisation]] zwischen [[Knoten|Knoten]]. Alternativen wie [[Broker-basierte Systeme]] oder [[strukturierte P2P-Netzwerke]] (z. B. [[Chord]]) können effizienter sein, wenn [[deterministisches Routing]] benötigt wird.
- **Beispiel / Code:** In einem [[P2P-basierten]] [[Microblogging-System]] könnte ein [[Servant|Servant]] wie folgt agieren:

```python
# Servant als Client: Neue Nachricht veröffentlichen
blog = linda.universe._rd(("MicroBlog", linda.TupleSpace))[1]
blog._out(("user123", "distsys", "Studying Servant patterns"))

# Servant als Server: Nachrichten anderer Knoten lesen
message = blog._rd((str, "distsys", str))
```

Hier fungiert jeder [[Knoten]] sowohl als [[Publisher]] (via `_out`) als auch als [[Subscriber]] (via `_rd`), ohne zentrale [[Instanz]].
