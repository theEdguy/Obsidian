---
id: 68af08d4-7eda-4796-ac3b-e961aaf4303f
title: "Gossiping Protokoll"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerkprotokolle
  - epidemische_algorithmik
  - replikation
  - skalierbarkeit
  - fehlertoleranz
  - multicast
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Gossiping Protokoll]]

- **Kernkonzept:** Ein [[Gossiping|Gossip-Protokoll]] ist ein [[epidemisches_Protokoll|epidemisches Protokoll]], das zur [[skalierbaren|skalierbaren]] und [[fehlertoleranten|fehlertoleranten]] Verbreitung von [[Information|Informationen]] in [[verteilten_Systemen|verteilten Systemen]] genutzt wird. Dabei leiten [[Knoten|Knoten]] aktualisierte Zustände an zufällig ausgewählte Nachbarn weiter, ähnlich der Ausbreitung von Gerüchten.
- **Nutzen & Zweck:** Gossiping-Protokolle lösen das [[Problem]] der effizienten und robusten [[Datenverbreitung]] in großen, dynamischen [[Netzwerken]]. Sie ermöglichen [[schließlich_konsistente|schließlich konsistente]] Systeme ohne zentrale Steuerung und sind besonders nützlich für [[Replikation|Replikationsmechanismen]], [[Fehlererkennung]] und [[Lastverteilung]].
- **Abgrenzung & Grenzen:** Gossiping-Protokolle sind ungeeignet für [[Echtzeitanforderungen|Echtzeitanforderungen]] oder [[strikte_Konsistenz|strikte Konsistenzgarantien]], da sie [[lazy_Propagation|lazy Propagation]] nutzen. Im Vergleich zu [[baum-basiertem_Multicasting|baum-basierten Multicast-Verfahren]] verursachen sie höhere [[Netzwerklast]], bieten aber bessere [[Fehlertoleranz]]. Für [[deterministische_Garantien|deterministische Garantien]] (z. B. [[FIFO_Reihenfolge|FIFO-Reihenfolge]]) sind [[Message-Queuing-Systeme|Message-Queuing-Systeme]] wie IBM MQ besser geeignet.
- **Beispiel / Code:** Pseudocode für ein einfaches Gossiping-Protokoll zur Verbreitung einer Aktualisierung:

```
function gossip_update(update):
    if not already_received(update):
        apply_update(update)
        neighbors = select_random_neighbors(k=3)  // Wähle 3 zufällige Nachbarn
        for neighbor in neighbors:
            send_update(neighbor, update)
```

Erläuterung: Ein [[Knoten]], der eine Aktualisierung erhält, wendet sie an und leitet sie an eine kleine, zufällige Auswahl seiner Nachbarn weiter. Dies wiederholt sich, bis alle [[Knoten]] die Aktualisierung erhalten haben.
