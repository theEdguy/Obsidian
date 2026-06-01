---
id: 1b17e146-f31c-47a2-8d14-f57a8a490b9d
title: "Nachrichtenorientierte Kommunikation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - kommunikation
  - netzwerk
  - asynchron
  - middleware
  - nachrichten
  - entkopplung
  - mpi
  - message_queuing
  - skalierbarkeit
  - nachrichtenorientierte-middleware
  - fehlertoleranz
  - ibm-mq
  - persistenz
  - asynchrone-kommunikation
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Nachrichtenorientierte Kommunikation]]

- **Kernkonzept:** Nachrichtenorientierte [[Kommunikation]] ermöglicht den [[Austausch|Austausch]] von [[Nachricht|Nachrichten]] zwischen [[Prozess|Prozessen]] oder [[System|Systemen]] durch das Senden und Empfangen über [[Middleware]] oder [[Protokoll|Protokolle]] wie [[MPI (Message Passing Interface)|MPI]] oder [[Message_Queue|Message Queues]]. Sie unterstützt sowohl transiente als auch [[Persistenz|persistente]] [[Nachrichtenübermittlung|Nachrichtenübermittlungen]], um [[Lose_Kopplung|lose Kopplung]] und [[Fehlertoleranz]] in [[Verteilte Systeme|verteilten Systemen]] zu gewährleisten.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der [[Entkopplung]] in [[Verteilte Systeme|verteilten Systemen]], indem es [[Asynchronität|asynchrone]] und [[Persistenz|persistente]] [[Nachrichtenübermittlung|Nachrichtenübermittlungen]] ermöglicht. Es fördert [[Skalierbarkeit]], [[Fehlertoleranz]] und [[Entkopplung]] von [[Komponente|Komponenten]], vereinfacht die [[Koordination]] und unterstützt [[Event-gesteuertes_System|event-gesteuerte Architekturen]]. Durch die Verwendung von [[Warteschlange|Warteschlangen]] wird die [[Zuverlässigkeit]] der [[Kommunikation]] erhöht, da [[Nachricht|Nachrichten]] auch bei temporären [[Verbindung|Verbindungs]]abbrüchen oder [[Systemausfall|Systemausfällen]] erhalten bleiben und später zugestellt werden. Zudem ermöglicht es die Integration heterogener [[System|Systeme]] durch standardisierte [[Schnittstelle|Schnittstellen]] und [[Protokoll|Protokolle]].
- **Abgrenzung & Grenzen:** Nachrichtenorientierte [[Kommunikation]] ist nicht geeignet für [[Szenario|Szenarien]], die strikte [[Synchronisation]] oder [[Transaktionssicherheit]] erfordern, da [[Asynchronität]] und [[Pufferung]] zusätzliche [[Latenz|Latenzen]] verursachen können. Im Vergleich zu [[RPC]] oder [[Shared Memory]] fehlt die [[Zugriffstransparenz]], da [[Nachricht|Nachrichten]] explizit gesendet und empfangen werden müssen. Alternativen wie [[RPC]] oder [[Shared Memory]] bieten direktere [[Synchronisation]] und sind bei engen [[Kopplung|Kopplungen]] oder [[Echtzeitanforderung|Echtzeitanforderungen]] vorzuziehen. Für [[Echtzeitanwendung|Echtzeitanwendungen]] mit strengen [[Latenz|Latenzanforderungen]] sind nachrichtenorientierte Ansätze oft ungeeignet, insbesondere wenn [[Persistenz]] erforderlich ist, da diese zusätzlichen [[Speicher]]- und Verwaltungsaufwand verursacht. [[Transient Messaging]] (z. B. [[MPI (Message Passing Interface)|MPI]]) bietet zwar geringere [[Latenz|Latenzen]], erfordert jedoch aktive [[Verbindung|Verbindungen]] und ist weniger fehlertolerant.
- **Beispiel / Code:** {'beschreibung': 'Beispiele für nachrichtenorientierte [[Kommunikation]] mit verschiedenen [[Middleware|Middleware-Lösungen]] und [[Protokoll|Protokollen]]:', 'zero_mq': {'beschreibung': 'Ein einfaches Beispiel für nachrichtenorientierte [[Kommunikation]] mit ZeroMQ im [[Request-Reply_Pattern|Request-Reply-Muster]]:', 'server_code': {'sprache': 'Python', 'code': '```python\nimport zmq\ncontext = zmq.Context()\ns = context.socket(zmq.REP)\ns.bind("tcp://*:5555")\nwhile True:\n    message = s.recv()\n    s.send(message + "*")\n```'}, 'client_code': {'sprache': 'Python', 'code': '```python\nimport zmq\ncontext = zmq.Context()\ns = context.socket(zmq.REQ)\ns.connect("tcp://localhost:5555")\ns.send("Hello")\nprint(s.recv())\n```'}}, 'mpi': {'beschreibung': 'Beispiel für blockierendes Senden und Empfangen mit [[MPI (Message Passing Interface)|MPI]] (transiente [[Nachrichtenübermittlung|Nachrichtenübermittlung]]):', 'code': '```c\n#include <mpi.h>\n#include <stdio.h>\n\nint main(int argc, char** argv) {\n    MPI_Init(&argc, &argv);\n    \n    int rank;\n    MPI_Comm_rank(MPI_COMM_WORLD, &rank);\n    \n    if (rank == 0) {\n        int message = 42;\n        MPI_Send(&message, 1, MPI_INT, 1, 0, MPI_COMM_WORLD);\n        printf("Prozess 0 hat Nachricht gesendet.\\n");\n    } else if (rank == 1) {\n        int received;\n        MPI_Recv(&received, 1, MPI_INT, 0, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);\n        printf("Prozess 1 hat Nachricht empfangen: %d\\n", received);\n    }\n    \n    MPI_Finalize();\n    return 0;\n}\n```'}, 'message_queue': {'beschreibung': 'Beispiel für eine einfache [[Message_Queue|Message Queue]]-Operation (Pseudocode, transiente [[Nachrichtenübermittlung|Nachrichtenübermittlung]]):', 'code': '```java\n// Sender\nMessageQueue queue = new MessageQueue("queue_name");\nMessage msg = new Message("Hallo, Empfänger!");\nqueue.put(msg);\n\n// Empfänger\nMessage received = queue.get(); // Blockiert, bis Nachricht verfügbar\nSystem.out.println("Empfangen: " + received.getContent());\n```'}, 'persistent_message_queue': {'beschreibung': 'Beispiel für persistente [[Nachrichtenübermittlung|Nachrichtenübermittlung]] mit IBM MQ (Java):', 'code': '```java\n// Nachricht in IBM MQ-Warteschlange einstellen (Java)\nMQQueueManager qmgr = new MQQueueManager("QM1");\nMQQueue queue = qmgr.accessQueue("DEV.QUEUE.1", MQC.MQOO_OUTPUT);\nMQMessage message = new MQMessage();\nmessage.writeString("Hallo, persistente Kommunikation!");\nqueue.put(message);\nqueue.close();\nqmgr.disconnect();\n```', 'erlaeuterung': 'Die [[Nachricht]] wird in die lokale [[Warteschlange]] `DEV.QUEUE.1` geschrieben und vom [[Queue Manager]] `QM1` verwaltet. Selbst bei einem [[Systemausfall]] bleibt die [[Nachricht]] erhalten und wird später zugestellt.'}}
