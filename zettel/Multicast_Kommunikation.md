---
id: 1f9ec214-c730-4523-af94-2988628f6502
title: "Multicast Kommunikation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - netzwerkkommunikation
  - datenverbreitung
  - overlay-netzwerke
  - skalierbarkeit
  - middleware
  - gossip_protokolle
  - fehlertoleranz
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Multicast Kommunikation]]

- **Kernkonzept:** Multicast Kommunikation ermöglicht das gleichzeitige Senden von [[Nachricht|Nachrichten]] an mehrere [[Empfänger|Empfänger]] in [[verteilte Systeme|verteilten Systemen]], ohne jeden einzeln adressieren zu müssen. Dies erfolgt über [[Overlay-Netzwerk|Overlay-Netzwerke]] wie [[Baum|Bäume]], [[Mesh-Netzwerk|Mesh-Netzwerke]] oder gossip-basierte [[Algorithmus|Algorithmen]], bei denen [[Knoten]] [[Aktualisierung|Aktualisierungen]] untereinander austauschen, ohne eine zentrale [[Instanz]] zu benötigen.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der effizienten [[Datenverbreitung]] in [[verteilte Systeme|verteilten Systemen]], indem es [[Netzwerk|Netzwerkressourcen]] schont und [[Skalierbarkeit]] sowie [[Fehlertoleranz]] verbessert. Es wird genutzt, um [[Aktualisierung|Aktualisierungen]], [[Benachrichtigung|Benachrichtigungen]] oder [[Streaming-Daten]] an viele [[Knoten]] gleichzeitig zu senden, insbesondere in großen [[Netzwerk|Netzwerken]], in denen zeitnahe [[Synchronisation]] ohne strenge [[Konsistenzgarantie|Konsistenzgarantien]] erforderlich ist. Gossip-basierte Verfahren ermöglichen dabei eine robuste und dezentrale Verbreitung von [[Information|Informationen]].
- **Abgrenzung & Grenzen:** Multicast ist ungeeignet für [[Punkt-zu-Punkt-Kommunikation]] oder wenn [[Zuverlässigkeit]], [[Reihenfolge]] oder strenge [[Konsistenzgarantie|Konsistenzgarantien]] (z. B. [[ACID]]) erforderlich sind. Alternativen wie [[Unicast]] oder [[Broadcast]] sind in solchen Fällen vorzuziehen, da sie einfacher umzusetzen sind, aber weniger [[Skalierbarkeit]] bieten. Zudem erfordert Multicast oft spezielle [[Netzwerk|Netzwerkunterstützung]] oder [[Middleware]], was die [[Komplexität]] erhöht. Gossip-basierte Verfahren können [[Datenverlust]] nicht vollständig ausschließen und benötigen zusätzliche Mechanismen wie [[Totenschein|Totenscheine]] für [[Löschoperation|Löschoperationen]]. Deterministische [[Latenz]] ist ebenfalls nicht garantiert.
- **Beispiel / Code:** ### Application-Level Multicasting (ALM) in Chord:
1. Initiator generiert einen Multicast-Bezeichner `mid`.
2. Suche nach `succ(mid)` (zuständiger [[Knoten]] für `mid`), der zur Wurzel des Multicast-Baums wird.
3. Ein neuer [[Knoten]] `P` sendet einen Beitritts-Request zur Wurzel.
4. Der Request wird entlang des Pfades zur Wurzel weitergeleitet, bis ein [[Knoten]] `Q` ihn verarbeitet:
   - Falls `Q` den Baum noch nicht kennt, wird `P` Kind von `Q`, und der Request wird weitergeleitet.
   - Falls `Q` den Baum kennt, wird `P` Kind von `Q`, und der Request wird nicht weitergeleitet.

### Gossip-basierter Push-Pull-Algorithmus (Pseudocode):
```python
def gossip_push_pull(node):
    partner = random.choice(network_nodes)
    # Push: Sende lokale Aktualisierungen an Partner
    partner.receive_updates(node.updates)
    # Pull: Empfange Aktualisierungen vom Partner
    node.updates.update(partner.request_updates())
```

**Erläuterung**: Ein [[Knoten]] wählt zufällig einen Partner aus, tauscht [[Aktualisierung|Aktualisierungen]] aus und synchronisiert so seinen [[Zustand]]. Nach O(log(N)) Runden sind alle [[Knoten]] konsistent.
