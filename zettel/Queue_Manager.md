---
id: e7b88523-9f9d-43b0-b3fc-736df386507a
title: "Queue Manager"
date: 2026-06-01
tags:
  - verteilte_systeme
  - nachrichtenorientierte_kommunikation
  - middleware
  - warteschlangen
  - routing
  - asynchron
  - persistenz
  - ibm_mq
  - enterprise_integration
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Queue Manager]]

- **Kernkonzept:** Ein [[Queue Manager|Queue Manager]] verwaltet [[Warteschlange|Warteschlangen]] in [[nachrichtenorientierte_Middleware|nachrichtenorientierten Middleware-Systemen]] und ermöglicht das [[Routing|Routing]] von [[Nachricht|Nachrichten]] zwischen verteilten [[Anwendung|Anwendungen]] durch persistente, asynchrone Kommunikation.
- **Nutzen & Zweck:** Der [[Queue Manager|Queue Manager]] löst das [[Problem]] der zuverlässigen, entkoppelten Kommunikation in verteilten Systemen. Er ermöglicht [[Skalierbarkeit]], [[Fehlertoleranz]] und [[Lastverteilung]], indem er [[Nachricht|Nachrichten]] zwischen [[Sender]] und [[Empfänger]] puffert und weiterleitet, selbst wenn diese nicht gleichzeitig verfügbar sind.
- **Abgrenzung & Grenzen:** Ein [[Queue Manager|Queue Manager]] ist nicht geeignet für [[Echtzeitkommunikation]] oder [[synchron]]e [[Interaktion|Interaktionen]], da er auf asynchrone [[Nachrichtenübertragung]] setzt. Alternativen wie [[RPC]] oder [[MPI]] bieten direkte, blockierende Kommunikation, während [[Queue Manager]] auf Entkopplung und Persistenz fokussieren. Für einfache [[Punkt-zu-Punkt-Kommunikation]] kann er überdimensioniert sein.
- **Beispiel / Code:** ```
// Beispiel: Nachricht an eine lokale Queue senden (IBM MQ-ähnliche Syntax)
MQPUT(Hconn, Hobj, &msgDesc, &putOpts, msgLength, msgBuffer, &compCode, &reason);

// Nachricht aus einer entfernten Queue empfangen (Routing über Queue Manager)
MQGET(Hconn, Hobj, &msgDesc, &getOpts, msgBufferSize, msgBuffer, &msgLength, &compCode, &reason);
```

*Erläuterung*: Der [[Queue Manager]] leitet die Nachricht von der lokalen [[Sende-Queue]] zur [[Empfangs-Queue]] des Zielsystems weiter, wobei [[Channel]]s und [[Message Channel Agents]] die Netzwerkkommunikation übernehmen.
