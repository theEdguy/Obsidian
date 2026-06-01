---
id: 04d8a858-940b-4f06-8a1c-58ec4a193e67
title: "Message Queues (MQ)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - nachrichtenorientierte-middleware
  - asynchrone-kommunikation
  - skalierbarkeit
  - integration
  - enterprise-architektur
  - queue-manager
  - message-broker
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Message Queues (MQ)]]

- **Kernkonzept:** Message Queues (MQ) ermöglichen asynchrone, persistente [[Kommunikation|Kommunikationen]] zwischen [[Komponente|Komponenten]] in [[Verteiltes System|verteilten Systemen]] durch Warteschlangen, die [[Nachricht|Nachrichten]] zwischenspeichern und weiterleiten. Sie entkoppeln Sender und Empfänger zeitlich und räumlich.
- **Nutzen & Zweck:** MQ löst das [[Problem]] der [[Skalierbarkeit|Skalierbarkeitsprobleme]] und [[Zuverlässigkeit|Zuverlässigkeitsprobleme]] in [[Verteiltes System|verteilten Systemen]], indem es [[Nachricht|Nachrichten]] puffert, [[Last|Lastspitzen]] abfedert und garantierte Zustellung auch bei temporären Ausfällen ermöglicht. Es vereinfacht die [[Integration]] heterogener [[Anwendung|Anwendungen]] und ermöglicht lose [[Kopplung|Kopplungen]].
- **Abgrenzung & Grenzen:** MQ ist ungeeignet für Echtzeit- oder synchrone [[Kommunikation|Kommunikationen]], da [[Latenz|Latenzen]] durch Pufferung entstehen. Alternativen wie [[RPC]] oder [[MPI]] bieten direkte, blockierende [[Kommunikation]], während MQ asynchron arbeitet. Bei einfachen [[System|Systemen]] mit geringer [[Komplexität]] kann MQ Overhead verursachen. Nicht ideal für [[Streaming]]-Szenarien mit hohen Durchsatzanforderungen ohne zusätzliche Optimierungen.
- **Beispiel / Code:** ```
// Beispiel: Nachricht an eine Queue senden (IBM MQ-ähnliche Syntax)
MQQueue queue = queueManager.accessQueue("DEV.QUEUE.1", MQC.MQOO_OUTPUT);
MQMessage message = new MQMessage();
message.writeString("Hallo, Message Queue!");
queue.put(message);
queue.close();

// Beispiel: Nachricht aus einer Queue empfangen
MQQueue queue = queueManager.accessQueue("DEV.QUEUE.1", MQC.MQOO_INPUT_AS_Q_DEF);
MQMessage receivedMessage = new MQMessage();
queue.get(receivedMessage);
String msgText = receivedMessage.readString();
queue.close();
```
