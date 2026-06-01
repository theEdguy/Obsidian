---
id: 7b8e84b8-19f5-429b-aa30-f75e400ed5a0
title: "Message Broker"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - middleware
  - nachrichtenorientierte-kommunikation
  - asynchron
  - warteschlangen
  - integration
  - skalierbarkeit
  - publish-subscribe
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Message Broker]]

- **Kernkonzept:** Ein [[Message Broker|Message Broker]] ist eine [[Middleware]]-Komponente, die die [[Kommunikation]] zwischen [[Anwendung|Anwendungen]] durch asynchrone [[Nachrichtenübermittlung|Nachrichtenübermittlungen]] über [[Warteschlange|Warteschlangen]] (Message Queues) ermöglicht. Er transformiert und routet [[Nachricht|Nachrichten]] zwischen heterogenen Systemen und unterstützt [[Publish-Subscribe|Publish-Subscribe-Modelle]].
- **Nutzen & Zweck:** Ein [[Message Broker]] löst das [[Problem]] der [[Kopplung|engen Kopplung]] zwischen [[Anwendung|Anwendungen]] in [[Verteilte Systeme|verteilten Systemen]], indem er asynchrone, persistente und zuverlässige [[Kommunikation]] ermöglicht. Er entkoppelt [[Sender]] und [[Empfänger]], ermöglicht [[Skalierbarkeit]], verbessert die [[Fehlertoleranz]] und vereinfacht die [[Integration]] heterogener Systeme durch [[Formattransformation]] und [[Routing]].
- **Abgrenzung & Grenzen:** Ein [[Message Broker]] sollte nicht genutzt werden, wenn [[Echtzeitkommunikation]] mit minimaler [[Latenz]] erforderlich ist, da die [[Verarbeitung]] in [[Warteschlange|Warteschlangen]] zusätzliche [[Verzögerung|Verzögerungen]] verursacht. Alternativen wie [[Remote Procedure Call|RPC]] oder [[Direct Messaging]] (z. B. [[MPI]]) sind besser geeignet, wenn synchrone oder transiente [[Kommunikation]] ausreicht. Zudem ist ein [[Message Broker]] überdimensioniert für einfache [[Punkt-zu-Punkt-Kommunikation|Punkt-zu-Punkt-Kommunikationen]] ohne [[Formatheterogenität]] oder [[Routing]]-Anforderungen.
- **Beispiel / Code:** ```
// Beispiel: Nachricht an eine Queue senden (IBM MQ-ähnliche Syntax)
MQQueue queue = queueManager.accessQueue("DEV.QUEUE.1", MQC.MQOO_OUTPUT);
MQMessage message = new MQMessage();
message.writeString("Hallo, Message Broker!");
MQPutMessageOptions pmo = new MQPutMessageOptions();
queue.put(message, pmo);
queue.close();

// Beispiel: Nachricht aus einer Queue empfangen
MQQueue queue = queueManager.accessQueue("DEV.QUEUE.1", MQC.MQOO_INPUT_SHARED);
MQMessage receivedMessage = new MQMessage();
MQGetMessageOptions gmo = new MQGetMessageOptions();
gmo.options = MQC.MQGMO_WAIT;
queue.get(receivedMessage, gmo);
String msgText = receivedMessage.readString(receivedMessage.getMessageLength());
queue.close();
```
