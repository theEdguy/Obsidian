---
id: d0a6ab72-cbd8-42ad-9ea9-aa01ee7053d8
title: "Vermittlungsschicht (Routing)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - kommunikation
  - osi-modell
  - routing
  - verteilte-systeme
  - protokolle
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Vermittlungsschicht (Routing)]]

- **Kernkonzept:** Die Vermittlungsschicht ist die dritte Schicht im [[OSI-Referenzmodell|OSI-Referenzmodell]] und verantwortlich für das [[Routing|Leiten]] von [[Datenpaket|Datenpaketen]] durch ein [[Netzwerk]] aus [[Knoten|Knoten]] (und zwischen [[Netzwerk|Netzwerken]]). Sie ermöglicht die [[Adressierung]] und [[Wegewahl]] von Nachrichten zwischen [[Sender]] und [[Empfänger]].
- **Nutzen & Zweck:** Die Vermittlungsschicht löst das Problem der [[Wegewahl]] in komplexen [[Netzwerk|Netzwerken]], indem sie [[Datenpaket|Datenpakete]] effizient und zuverlässig durch mehrere [[Knoten]] oder [[Subnetz|Subnetze]] leitet. Ohne sie wäre eine skalierbare [[Kommunikation]] in [[Verteilte Systeme|verteilten Systemen]] nicht möglich, da direkte [[Punkt-zu-Punkt-Verbindung|Punkt-zu-Punkt-Verbindungen]] unpraktikabel wären.
- **Abgrenzung & Grenzen:** Die Vermittlungsschicht sollte nicht genutzt werden, wenn direkte [[Hardware]]-nahe [[Kommunikation]] (z. B. auf [[Sicherungsschicht]] oder [[Bitübertragungsschicht]]) ausreicht, da sie zusätzliche [[Latenz]] und [[Komplexität]] einführt. Alternativen wie [[Broadcast]] oder [[Multicast]] auf tieferen Schichten können in lokalen [[Netzwerk|Netzwerken]] effizienter sein. Zudem ist sie für [[Echtzeitanwendung|Echtzeitanwendungen]] mit strikten [[Latenz]]-Anforderungen oft ungeeignet.
- **Beispiel / Code:** Ein einfaches Beispiel für ein [[Routing]]-Protokoll ist das **Internet Protocol (IP)**. Hier ein Ausschnitt einer Routing-Tabelle in einem Router:

```
Destination     Gateway         Netmask         Interface
192.168.1.0    0.0.0.0         255.255.255.0   eth0
10.0.0.0       192.168.1.1     255.0.0.0       eth1
0.0.0.0        192.168.1.254   0.0.0.0         eth0
```

- Pakete an `192.168.1.0/24` werden direkt über `eth0` gesendet.
- Pakete an `10.0.0.0/8` werden an den Gateway `192.168.1.1` weitergeleitet.
- Alle anderen Pakete (Default-Route) gehen an `192.168.1.254`.
