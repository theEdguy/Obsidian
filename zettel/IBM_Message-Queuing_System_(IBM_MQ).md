---
id: 29b11d0b-f3be-44a9-8ce2-cf87888bf6e3
title: "IBM Message-Queuing System (IBM MQ)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - middleware
  - verteilte-systeme
  - nachrichtenorientierte-kommunikation
  - asynchron
  - warteschlangen
  - enterprise-integration
  - fehlertoleranz
  - routing
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[IBM Message-Queuing System (IBM MQ)]]

- **Kernkonzept:** IBM MQ ist eine [[Middleware|Middleware-Lösung]] für [[nachrichtenorientierte Kommunikation|nachrichtenorientierte]] und [[asynchrone Kommunikation|asynchrone]] [[persistente Kommunikation|persistente]] [[Nachrichtenübermittlung|Nachrichtenübermittlung]], die [[Warteschlangen|Warteschlangen]] (Message Queues) und [[Queue Manager|Queue Manager]] nutzt, um [[Nachrichten|Nachrichten]] zwischen [[verteilten Systemen|verteilten]] [[Anwendungen|Anwendungen]] zuverlässig zu übertragen.
- **Nutzen & Zweck:** IBM MQ löst das [[Problem]] der [[zuverlässigen Kommunikation|zuverlässigen]] und [[entkoppelten Kommunikation|entkoppelten]] [[Datenübertragung|Datenübertragung]] in [[heterogenen Systemen|heterogenen]] [[verteilten Umgebungen|verteilten Umgebungen]]. Es ermöglicht [[asynchrone Verarbeitung|asynchrone]] [[Nachrichtenübermittlung|Nachrichtenübermittlung]], [[Fehlertoleranz]] und [[Skalierbarkeit]] durch [[persistente Warteschlangen|persistente Warteschlangen]] und [[Routing-Mechanismen|Routing-Mechanismen]], ohne dass [[Sender]] und [[Empfänger]] gleichzeitig aktiv sein müssen.
- **Abgrenzung & Grenzen:** IBM MQ ist nicht geeignet für [[Echtzeitkommunikation|Echtzeitanwendungen]] mit [[harten Latenzanforderungen|harten Latenzanforderungen]], da es auf [[asynchrone Verarbeitung|asynchrone]] [[Pufferung]] setzt. Im Vergleich zu [[RPC|RPC-basierten]] oder [[MPI|MPI-Lösungen]] bietet es weniger [[Flexibilität]] für [[synchrone Interaktionen|synchrone]] [[Prozesskommunikation|Prozesskommunikation]]. Für [[Publish-Subscribe|Publish-Subscribe-Szenarien]] sind [[Message Broker|Message Broker]] mit [[themenbasiertem Routing|themenbasiertem Routing]] (z. B. Apache Kafka) oft besser geeignet. Zudem erfordert IBM MQ manuelle [[Konfiguration]] von [[Routing-Pfaden|Routing-Pfaden]], was bei [[dynamischen Netzwerken|dynamischen]] [[Topologien]] nachteilig sein kann.
- **Beispiel / Code:** // Beispiel: Nachricht an eine lokale Queue senden (IBM MQ Java API)
import com.ibm.mq.*;

public class MQSender {
    public static void main(String[] args) {
        try {
            MQQueueManager qMgr = new MQQueueManager("QM1");
            int openOptions = MQC.MQOO_OUTPUT | MQC.MQOO_FAIL_IF_QUIESCING;
            MQQueue queue = qMgr.accessQueue("DEV.QUEUE.1", openOptions);
            
            MQMessage message = new MQMessage();
            message.writeUTF("Hallo, IBM MQ!");
            MQPutMessageOptions pmo = new MQPutMessageOptions();
            queue.put(message, pmo);
            
            queue.close();
            qMgr.disconnect();
        } catch (MQException e) {
            e.printStackTrace();
        }
    }
}

// Beispiel: Routing-Konfiguration (manuell im Queue Manager)
// Alias Queue: LA1 -> QMA
// Remote Queue: QMA -> SQ1 (über Channel zu QMB)
