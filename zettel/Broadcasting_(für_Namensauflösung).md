---
id: 82d3f0df-a8a4-4f30-95fb-197ff94bcb62
title: "Broadcasting (für Namensauflösung)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - namensauflösung
  - netzwerk
  - kommunikation
  - verteilte-systeme
  - broadcast
  - lokalisierung
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Broadcasting (für Namensauflösung)]]

- **Kernkonzept:** Broadcasting ist ein Verfahren zur [[Namensauflösung|Auflösung]] linearer [[Bezeichner|Bezeichner]] in [[verteilte Systeme|verteilten Systemen]], bei dem eine Anfrage an alle [[Entität|Entitäten]] im Netzwerk gesendet wird, um die [[Adresse]] des gesuchten [[Zugriffspunkt|Zugriffspunkts]] zu ermitteln.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der [[Lokalisierung]] von [[Entität|Entitäten]] mit flachen [[Namen]] in lokalen Netzwerken (LANs), indem es eine einfache und direkte Methode zur [[Namensauflösung]] bietet, ohne zentrale [[Namensdienste]] oder komplexe [[Datenstruktur|Datenstrukturen]] wie [[verteilte Hash-Tabellen]] zu benötigen.
- **Abgrenzung & Grenzen:** Broadcasting skaliert nicht über ein LAN hinaus und verursacht hohen Netzwerkverkehr, da alle [[Prozess|Prozesse]] eingehende Anfragen auswerten müssen. Es ist ungeeignet für große oder geografisch verteilte Systeme. Alternativen wie [[heimatbasierte Ansätze]], [[verteilte Hash-Tabellen]] (z. B. [[Chord]]) oder [[hierarchische Ansätze]] (z. B. [[DNS]]) sind effizienter für komplexere Szenarien.
- **Beispiel / Code:** Beispiel: Address Resolution Protocol (ARP)

1. Ein Host sendet eine Broadcast-Nachricht ins lokale Netzwerk:
   "Wer hat die IP-Adresse 192.168.1.10?"
2. Der Host mit der gesuchten IP-Adresse antwortet direkt mit seiner MAC-Adresse:
   "192.168.1.10 ist bei MAC-Adresse 00:1A:2B:3C:4D:5E".

Pseudocode für Broadcasting in einem verteilten System:
```
function resolveName(identifier):
    broadcast(identifier)
    for each entity in network:
        if entity.identifier == identifier:
            return entity.address
    return null
```
