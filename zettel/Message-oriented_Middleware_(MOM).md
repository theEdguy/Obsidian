---
id: 99c99d62-f345-4ee4-b74d-8f8cb73b0699
title: "Message-oriented Middleware (MOM)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - middleware
  - verteilte-systeme
  - kommunikation
  - asynchron
  - warteschlange
  - nachrichtenorientiert
  - skalierbarkeit
  - nachrichtenorientierte-kommunikation
  - queue-management
  - enterprise-integration
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Message-oriented Middleware (MOM)]]

- **Kernkonzept:** Message-oriented Middleware (MOM) ist eine [[Middleware|Middleware-Architektur]], die [[Nachricht|Nachrichten]] zwischen [[Prozess|Prozessen]] in [[Verteiltes_System|verteilten Systemen]] asynchron und persistent über [[Warteschlange|Nachrichtenwarteschlangen]] (Message Queues) überträgt, um [[Kommunikation|Kommunikationsabläufe]] zeitlich und räumlich zu entkoppeln. Die [[Warteschlange|Warteschlangen]] werden von [[Queue_Manager|Queue Managern]] verwaltet, die [[Zuverlässigkeit]] und [[Skalierbarkeit]] sicherstellen.
- **Nutzen & Zweck:** MOM löst das [[Problem]] der engen [[Kopplung]] in [[Client-Server-Modell|Client-Server-Architekturen]] und [[Verteilte_Anwendung|verteilten Anwendungen]], indem es [[Nachricht|Nachrichten]] zwischenspeichert und asynchron übermittelt. Dies ermöglicht [[Skalierbarkeit]], [[Fehlertoleranz]], [[Entkopplung]] von [[Kommunikationspartner|Kommunikationspartnern]] sowie [[Lastverteilung]] durch [[Asynchrone_Verarbeitung|asynchrone Verarbeitung]]. Selbst bei temporären [[Netzwerkausfall|Netzwerkausfällen]] oder [[Systemabsturz|Systemabstürzen]] bleibt die [[Zuverlässige_Kommunikation|zuverlässige Kommunikation]] gewährleistet. Zudem unterstützt MOM [[Enterprise_Integration|Enterprise-Integrationsszenarien]] durch standardisierte [[Schnittstelle|Schnittstellen]] und [[Protokoll|Protokolle]].
- **Abgrenzung & Grenzen:** MOM eignet sich nicht für [[Echtzeitanwendung|Echtzeitanwendungen]], die [[Synchrone_Kommunikation|synchrone Kommunikation]] oder sofortige Antworten erfordern, wie z. B. [[Transaktionssystem|Transaktionssysteme]] oder [[Remote_Procedure_Call_(RPC)|RPC]]. Im Vergleich zu [[Message-Passing_Interface_(MPI)|Message-Passing Interfaces (MPI)]] bietet MOM keine direkte [[Prozess-zu-Prozess-Kommunikation|Prozess-zu-Prozess-Kommunikation]], sondern arbeitet mit [[Middleware]]-basierten [[Warteschlange|Warteschlangen]]. Für einfache [[Punkt-zu-Punkt-Kommunikation|Punkt-zu-Punkt-Verbindungen]] kann der zusätzliche [[Overhead]] durch [[Warteschlange|Warteschlangenverwaltung]] und [[Queue_Manager|Queue Manager]] unnötig sein. Zudem erfordert MOM oft komplexere [[Fehlerbehandlung]], z. B. durch [[Dead_Letter_Queue_(DLQ)|Dead Letter Queues (DLQ)]], um nicht zustellbare [[Nachricht|Nachrichten]] zu verwalten.
- **Beispiel / Code:** ```python
# Beispiel 1: Asynchrone Kommunikation mit RabbitMQ (Python)
import pika

# Sender: Nachricht in die Queue einstellen
connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()
channel.queue_declare(queue='tasks')
channel.basic_publish(exchange='', routing_key='tasks', body='Hallo, MOM!')
connection.close()

# Empfänger: Nachricht asynchron verarbeiten
def callback(ch, method, properties, body):
    print(f"Empfangen: {body}")

channel.basic_consume(queue='tasks', on_message_callback=callback, auto_ack=True)
channel.start_consuming()
```

```java
// Beispiel 2: Nachricht in eine Queue einstellen und abrufen mit IBM MQ
import com.ibm.mq.*;

public class MOMExample {
    public static void main(String[] args) {
        try {
            MQQueueManager queueManager = new MQQueueManager("QM1");
            MQQueue queue = queueManager.accessQueue("DEV.QUEUE.1", MQC.MQOO_OUTPUT);
            MQMessage message = new MQMessage();
            message.writeString("Hallo, MOM!");
            queue.put(message);  // Nachricht asynchron senden
            
            // Nachricht blockierend abrufen
            MQQueue receiveQueue = queueManager.accessQueue("DEV.QUEUE.1", MQC.MQOO_INPUT_AS_Q_DEF);
            MQMessage receivedMessage = new MQMessage();
            receiveQueue.get(receivedMessage);
            String msgText = receivedMessage.readString();
            System.out.println("Empfangen: " + msgText);
        } catch (MQException e) {
            e.printStackTrace();
        }
    }
}
```

*Erläuterung*: Beide Beispiele zeigen die [[Entkopplung]] von [[Sender]] und [[Empfänger]] durch [[Warteschlange|Nachrichtenwarteschlangen]]. Der [[Sender]] legt eine [[Nachricht]] in der Queue ab, ohne auf eine Antwort zu warten. Der [[Empfänger]] verarbeitet die [[Nachricht]] asynchron, sobald sie verfügbar ist. IBM MQ bietet zusätzlich [[Transaktionssicherheit]] und [[Persistenz]] für kritische Anwendungsfälle.
