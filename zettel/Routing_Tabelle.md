---
id: 8461cb10-a988-4dff-a49a-482a01167155
title: "Routing Tabelle"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - nachrichtenorientierte-kommunikation
  - message-queuing
  - routing
  - netzwerk
  - middleware
  - ibm-mq
  - adressauflösung
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Routing Tabelle]]

- **Kernkonzept:** Eine [[Routing Tabelle|Routing-Tabelle]] ist eine Datenstruktur, die in [[verteilte Systeme|verteilten Systemen]] und [[Nachrichtenwarteschlange|Nachrichtenwarteschlangen]] verwendet wird, um den Pfad für die Weiterleitung von [[Nachricht|Nachrichten]] zwischen [[Queue Manager|Queue-Managern]] oder [[Knoten]] zu bestimmen. Sie bildet logische Adressen auf physische Kontaktadressen ab.
- **Nutzen & Zweck:** Die [[Routing Tabelle|Routing-Tabelle]] löst das Problem der [[Adressauflösung]] und [[Nachrichtenweiterleitung]] in [[nachrichtenorientierte Kommunikation|nachrichtenorientierten Systemen]], insbesondere in [[Message-Queuing-Systemen]]. Sie ermöglicht die effiziente und zuverlässige Zustellung von [[Nachricht|Nachrichten]] über mehrere [[Hop|Hops]] hinweg, ohne dass Sender und Empfänger direkt miteinander kommunizieren müssen.
- **Abgrenzung & Grenzen:** Eine [[Routing Tabelle|Routing-Tabelle]] sollte nicht in Systemen mit dynamischen oder häufig wechselnden Netzwerktopologien verwendet werden, da sie manuell konfiguriert wird und kein [[dynamisches Routing]] unterstützt. Alternativen wie [[Overlay-Netzwerk|Overlay-Netzwerke]] mit [[Application-Level Multicasting]] oder [[Gossip-Protokoll|Gossip-basierte Protokolle]] bieten mehr Flexibilität, erfordern jedoch komplexere [[Koordination]]. Zudem ist sie ungeeignet für Systeme, die [[Publish-Subscribe]]-Mechanismen nutzen, da hier [[Message Broker]] mit themenbasiertem Routing bevorzugt werden.
- **Beispiel / Code:** Beispiel einer [[Routing Tabelle]] in IBM MQ (vereinfacht):

```
Routing Tabelle (Queue Manager QMA):
Ziel-Queue-Manager | Ziel-Queue | Nächster Hop
------------------|------------|------------
QMB               | SQ1        | QMB
QMC               | SQ2        | QMC
QMD               | SQ1        | QMB
```

Eine [[Nachricht]] von QMA an QMD mit Ziel-Queue SQ1 wird zunächst an QMB weitergeleitet, da dieser als nächster [[Hop]] in der Tabelle eingetragen ist. QMB leitet die [[Nachricht]] dann an QMD weiter.
