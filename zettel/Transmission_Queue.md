---
id: cd1d479c-0dad-432f-8606-e24b8f396066
title: "Transmission Queue"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - nachrichtenorientierte-kommunikation
  - message-queuing
  - fehlertoleranz
  - netzwerk
  - middleware
  - ibm-mq
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Transmission Queue]]

- **Kernkonzept:** Eine [[Transmission Queue|Transmission Queue]] ist eine spezielle [[Warteschlange|Warteschlange]] in [[Message-Queuing-System|Message-Queuing-Systemen]], die ausgehende [[Nachricht|Nachrichten]] zwischenspeichert, bevor sie an entfernte [[Queue Manager]] weitergeleitet werden. Sie dient als Puffer für die asynchrone Übertragung zwischen [[Knoten]] in verteilten Systemen.
- **Nutzen & Zweck:** Die [[Transmission Queue]] löst das Problem der zuverlässigen und geordneten Nachrichtenübertragung in verteilten Systemen, indem sie [[Nachricht|Nachrichten]] temporär speichert, bis die Weiterleitung an den nächsten [[Queue Manager]] oder das Ziel erfolgreich abgeschlossen ist. Sie ermöglicht [[Fehlertoleranz]] und [[Lastverteilung]] durch Pufferung bei Netzwerkstörungen oder Überlastung.
- **Abgrenzung & Grenzen:** Eine [[Transmission Queue]] sollte nicht genutzt werden, wenn synchrone Kommunikation erforderlich ist (z. B. bei [[RPC]]-Aufrufen) oder wenn die [[Latenz]] kritisch ist, da die Pufferung Verzögerungen verursacht. Alternativen wie [[MPI]] oder direkte [[Socket]]-Kommunikation bieten hier geringere [[Latenz]], allerdings ohne die [[Fehlertoleranz]] und [[Skalierbarkeit]] von [[Message-Queuing-Systemen]].
- **Beispiel / Code:** In IBM MQ wird eine [[Transmission Queue]] wie folgt konfiguriert:

```
DEFINE QLOCAL('QMGR.A.TO.QMGR.B') +
       USAGE(XMITQ) +
       TRIGGER +
       INITQ(SYSTEM.CHANNEL.INITQ) +
       TRIGDATA('QMGR.A.TO.QMGR.B')
```

Hier wird eine lokale [[Warteschlange]] als [[Transmission Queue]] definiert, die [[Nachricht|Nachrichten]] an den [[Queue Manager]] `QMGR.B` weiterleitet. Der `TRIGGER`-Mechanismus startet automatisch einen [[Message Channel Agent]] zur Übertragung.
