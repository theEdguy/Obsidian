---
id: 92977373-e1c6-4fd2-889a-3aa44f7c3716
title: "Transiente Kommunikation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - verteilte-systeme
  - netzwerkprotokolle
  - synchronisation
  - client-server
  - middleware
  - fehlertoleranz
  - asynchron
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Transiente Kommunikation]]

- **Kernkonzept:** Transiente [[Kommunikation]] liegt vor, wenn ein [[Kommunikationsserver]] eine [[Nachricht]] verwirft, sobald sie nicht sofort an den nächsten [[Server]] oder [[Empfänger]] weitergeleitet werden kann, und erfordert die gleichzeitige Aktivität von [[Sender]] und [[Empfänger]]. Im Gegensatz dazu ermöglicht [[persistente Kommunikation|persistente Kommunikation]] das Speichern von [[Nachricht|Nachrichten]] durch einen [[Kommunikationsdienst]], bis die Auslieferung erfolgt, unabhängig von der Verfügbarkeit der [[Kommunikationspartner]].
- **Nutzen & Zweck:** Transiente [[Kommunikation]] ermöglicht einfache, direkte [[Interaktion|Interaktionen]] zwischen [[Prozess|Prozessen]] in [[Verteiltes_System|verteilten Systemen]], wo geringe [[Latenz]] und sofortige [[Antwort|Antworten]] priorisiert werden. Sie löst das [[Problem]] synchroner [[Koordination]] ohne komplexe [[Pufferung]] und eignet sich für [[Szenario|Szenarien]] mit zuverlässigen [[Netzwerk|Netzwerken]] und garantierter [[Verfügbarkeit]] aller [[Prozess|Prozesse]]. [[Persistente_Kommunikation|Persistente Kommunikation]] hingegen adressiert [[Zuverlässigkeit]] in [[verteilten Systemen]], indem sie [[Nachrichtenverlust]] verhindert, selbst bei temporärer Unerreichbarkeit von [[Kommunikationspartner|Kommunikationspartnern]] oder [[Netzwerk|Netzwerken]]. Sie unterstützt [[asynchrone_Kommunikation|asynchrone Kommunikation]] und entkoppelt [[Sender]] und [[Empfänger]] zeitlich, was [[Lose_Kopplung|lose Kopplung]] fördert.
- **Abgrenzung & Grenzen:** Transiente [[Kommunikation]] ist nicht geeignet für [[Szenario|Szenarien]] mit unzuverlässigen [[Netzwerk|Netzwerken]], hohen [[Ausfallwahrscheinlichkeit|Ausfallwahrscheinlichkeiten]] oder [[asynchrone_Kommunikation|asynchronen Anforderungen]], da fehlende [[Pufferung]] zu [[Nachrichtenverlust]] führen kann. Alternativen wie [[Message-oriented_Middleware]] oder [[Remote_Procedure_Call|RPC]] bieten robustere Mechanismen für solche Fälle. [[Persistente_Kommunikation|Persistente Kommunikation]] ist hingegen ungeeignet für [[Echtzeitanwendung|Echtzeitanwendungen]], die [[synchrone_Kommunikation|synchrone Kommunikation]] erfordern, da die [[Latenz]] durch Zwischenspeicherung steigt. Sie verursacht zudem höheren [[Speicherbedarf]] und [[Verwaltungsaufwand]], was die [[Skalierbarkeit]] beeinträchtigen kann. Direkte [[TCP]]-Verbindungen oder [[RPC]] sind effizienter, wenn die [[Verfügbarkeit]] aller [[Prozess|Prozesse]] garantiert ist.
- **Beispiel / Code:** ### Transiente Kommunikation (Beispiel: [[Client-Server]]-Modell mit TCP)
```java
// Client
Socket socket = new Socket("server.example.com", 1234);
OutputStream out = socket.getOutputStream();
out.write("Anfrage".getBytes());  // Blockiert bis Antwort
InputStream in = socket.getInputStream();
byte[] response = new byte[1024];
in.read(response);  // Blockiert bis Antwort empfangen
if (response == null) {
    handleError();  // Nachricht ging verloren (z. B. durch Netzwerkunterbrechung)
}
socket.close();
```

### Persistente Kommunikation (Beispiel: [[Message-oriented_Middleware|MOM]] mit JMS)
```java
// Sender (Java mit JMS)
ConnectionFactory factory = new ActiveMQConnectionFactory("tcp://localhost:61616");
Connection connection = factory.createConnection();
Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);
Destination queue = session.createQueue("AuftragQueue");
MessageProducer producer = session.createProducer(queue);
TextMessage message = session.createTextMessage("Auftrag XYZ");
producer.send(message);  // Nachricht wird in der Queue gespeichert
connection.close();

// Empfänger (kann später oder auf anderem System laufen)
Connection connection = factory.createConnection();
connection.start();
Session session = connection.createSession(false, Session.AUTO_ACKNOWLEDGE);
Destination queue = session.createQueue("AuftragQueue");
MessageConsumer consumer = session.createConsumer(queue);
Message receivedMsg = consumer.receive();  // Blockiert nicht dauerhaft
if (receivedMsg instanceof TextMessage) {
    String text = ((TextMessage) receivedMsg).getText();
    System.out.println("Empfangen: " + text);
}
connection.close();
```
