---
id: 1fd19376-808f-444a-a469-3123ec9eae43
title: "put (Operation)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - nachrichtenorientierte_kommunikation
  - middleware
  - warteschlangen
  - asynchron
  - message_queuing
  - synchronisation
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[put (Operation)]]

- **Kernkonzept:** Die [[Operation|Operationen]] `put` und `get` sind grundlegende [[Nachrichtenorientierte_Middleware|nachrichtenorientierte]] [[Operation|Operationen]] in [[Message_Queuing|Message-Queuing-Systemen]], die das [[Einfügen|Einfügen]] (`put`) und [[Entnehmen]] (`get`) von [[Nachricht|Nachrichten]] in bzw. aus [[Warteschlange|Warteschlangen]] ermöglichen. Sie bilden die Basis für [[asynchrone Kommunikation]] und [[Entkopplung]] in [[verteilte Systeme|verteilten Systemen]].
- **Nutzen & Zweck:** Die `put`-Operation fügt [[Nachricht|Nachrichten]] in eine [[Warteschlange]] ein und ermöglicht so [[asynchrone Kommunikation]] sowie [[Pufferung]] zwischen [[Sender|Sendern]] und [[Empfänger|Empfängern]], selbst bei temporärer Nichtverfügbarkeit. Die `get`-Operation entnimmt [[Nachricht|Nachrichten]] aus der [[Warteschlange]], blockiert dabei jedoch den [[Prozess]], bis eine [[Nachricht]] verfügbar ist. Zusammen lösen sie das [[Problem]] der [[Koordination]] und [[Synchronisation]] in [[verteilte Systeme|verteilten Systemen]], indem sie [[Skalierbarkeit]], [[Fehlertoleranz]] und [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] fördern. Sie sind essenziell für [[Event-gesteuerte_Architektur|Event-gesteuerte Architekturen]] und [[Microservices]].
- **Abgrenzung & Grenzen:** Beide [[Operation|Operationen]] sind ungeeignet für [[synchrone Kommunikation]], bei der sofortige Antworten erforderlich sind (z. B. [[RPC]] oder [[REST]]). Die `get`-Operation blockiert den [[Prozess]], was bei [[Echtzeitanforderungen]] oder [[nicht-blockierende Operationen|nicht-blockierenden Szenarien]] problematisch sein kann. Alternativen wie `poll` (nicht-blockierend) oder `notify` (ereignisgesteuert) sind hier vorzuziehen. Im Vergleich zu direkten [[Prozess]]-zu-[[Prozess]]-Mechanismen wie `MPI_send`/`MPI_recv` fehlt die direkte [[Synchronisation]], was zu höherer [[Latenz]] führen kann. Zudem sind [[Middleware]]-basierte Lösungen wie `put`/`get` oft zu langsam für [[Echtzeitsysteme|Echtzeitsysteme]] mit strengen [[Latenz]]-Anforderungen.
- **Beispiel / Code:** ```java
// Pseudocode: Nachricht in eine Warteschlange einfügen (put) und entnehmen (get)
QueueManager qm = new QueueManager("QM1");

// put-Operation: Nachricht in die Warteschlange einfügen
Message msg = new Message("Dateninhalt");
qm.put("ZIEL_QUEUE", msg);

// get-Operation: Nachricht aus der Warteschlange entnehmen (blockierend)
Message receivedMsg = qm.get("ZIEL_QUEUE"); // Blockiert bis Nachricht verfügbar
processMessage(receivedMsg);

// IBM MQ-spezifisch (Java)
// put-Operation
MQQueue queue = qm.accessQueue("ZIEL.QUEUE", MQC.MQOO_OUTPUT);
MQMessage mqMsg = new MQMessage();
mqMsg.writeString("Beispielnachricht");
MQPutMessageOptions pmo = new MQPutMessageOptions();
queue.put(mqMsg, pmo);

// get-Operation
MQQueue inputQueue = qm.accessQueue("QUEUE.NAME", MQC.MQOO_INPUT_AS_Q_DEF);
MQMessage receivedMessage = new MQMessage();
inputQueue.get(receivedMessage); // Blockiert bis Nachricht empfangen
```
