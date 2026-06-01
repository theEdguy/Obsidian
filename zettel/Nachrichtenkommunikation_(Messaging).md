---
id: 1b630fe3-5f5d-4315-8f8f-ff82c7d64c98
title: "Nachrichtenkommunikation (Messaging)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - verteilte-systeme
  - middleware
  - asynchron
  - nachrichtenorientiert
  - fehlertoleranz
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Nachrichtenkommunikation (Messaging)]]

- **Kernkonzept:** Die Nachrichtenkommunikation (Messaging) ermöglicht den [[Nachrichtenaustausch|asynchronen]] und [[persistenten]] [[Datenaustausch]] zwischen [[Prozess|Prozessen]] in [[Verteiltes System|verteilten Systemen]] durch Zwischenspeicherung in [[Warteschlange|Warteschlangen]] (Queues).
- **Nutzen & Zweck:** Sie löst das [[Problem]] der [[Synchronisation]] und [[Kopplung]] in [[Verteiltes System|verteilten Systemen]], indem sie [[Entkopplung]] von [[Sender]] und [[Empfänger]] ermöglicht. Dadurch wird [[Fehlertoleranz]] erhöht, [[Skalierbarkeit]] verbessert und [[Blockierung]] von [[Prozess|Prozessen]] vermieden.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Echtzeitkommunikation]] oder [[synchron]]e [[Interaktionen]], da [[Latenz]] durch Zwischenspeicherung entsteht. Unterscheidet sich von [[Remote Procedure Call (RPC)]] durch [[Asynchronität]] und [[Persistenz]], während RPC [[transient]] und [[synchron]] arbeitet. Für [[Client-Server-Modell|einfache Anfrage-Antwort-Muster]] ist RPC oft effizienter.
- **Beispiel / Code:** Beispiel für eine Message-oriented Middleware (MOM) mit JMS (Java Message Service):

// Sender (Producer)
QueueConnectionFactory factory = new QueueConnectionFactory();
QueueConnection connection = factory.createQueueConnection();
QueueSession session = connection.createQueueSession(false, Session.AUTO_ACKNOWLEDGE);
Queue queue = session.createQueue("exampleQueue");
QueueSender sender = session.createSender(queue);
TextMessage message = session.createTextMessage("Hallo, Empfänger!");
sender.send(message);

// Empfänger (Consumer)
QueueReceiver receiver = session.createReceiver(queue);
connection.start();
Message receivedMessage = receiver.receive();
if (receivedMessage instanceof TextMessage) {
    TextMessage textMessage = (TextMessage) receivedMessage;
    System.out.println("Empfangen: " + textMessage.getText());
}
