---
id: f2dd528c-e422-4ad8-8658-717cdf6fe7ca
title: "Gerüchte verbreiten (Rumor Spreading)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - epidemische_algorithmen
  - gossip_protokolle
  - multicast
  - fehlertoleranz
  - skalierbarkeit
  - netzwerkkommunikation
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Gerüchte verbreiten (Rumor Spreading)]]

- **Kernkonzept:** Ein [[epidemischer Algorithmus|epidemische Algorithmen]]-Ansatz, bei dem [[Knoten]] in einem [[verteilten System]] zufällig [[Aktualisierung|Aktualisierungen]] verbreiten, bis diese mit hoher Wahrscheinlichkeit alle [[Knoten]] erreichen. Ein aktiver [[Knoten]] stoppt die Verbreitung mit einer Wahrscheinlichkeit [[p_stop|p_stop]], sobald er auf einen bereits informierten [[Knoten]] trifft.
- **Nutzen & Zweck:** Löst das Problem der [[skalierbaren]] und [[fehlertoleranten]] Verbreitung von [[Information|Informationen]] in großen [[verteilten Systemen]], ohne zentrale [[Koordination]] oder komplexe [[Routing]]-Strukturen. Besonders nützlich für [[Multicast-Kommunikation]] in dynamischen oder unzuverlässigen [[Netzwerk|Netzwerken]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn eine garantierte Zustellung an *alle* [[Knoten]] erforderlich ist (z. B. bei kritischen Systemaktualisierungen). Im Vergleich zu [[deterministischen Algorithmen]] (wie [[Baum-basiertem Multicast]]) ist die Verbreitung langsamer und weniger vorhersehbar. Alternativen wie [[Anti-Entropy]] oder [[Hybridansätze]] können für strengere Konsistenzanforderungen besser sein. Nicht anwendbar, wenn [[Löschoperation|Löschoperationen]] ohne [[Totenschein|Totenscheine]] propagiert werden müssen.
- **Beispiel / Code:** ```python
import random

def rumor_spread(nodes, initial_updates, p_stop=0.5):
    # nodes: Liste aller Knoten-IDs
    # initial_updates: Dictionary {node_id: update}
    informed = set(initial_updates.keys())
    active = set(initial_updates.keys())
    
    while active:
        new_active = set()
        for node in active:
            # Wähle zufälligen Knoten zum Kontaktieren
            target = random.choice(nodes)
            if target not in informed:
                informed.add(target)
                new_active.add(target)
            elif random.random() < p_stop:
                # Stoppe mit Wahrscheinlichkeit p_stop
                continue
            else:
                new_active.add(node)
        active = new_active
    return informed
```

*Erläuterung*: Der Algorithmus simuliert die Verbreitung einer [[Aktualisierung]] in einem [[Netzwerk]]. Ein [[Knoten]] verbreitet die [[Information]] weiter, bis er auf einen bereits informierten [[Knoten]] trifft und mit Wahrscheinlichkeit `p_stop` stoppt.
