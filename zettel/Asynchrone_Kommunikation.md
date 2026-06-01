---
id: d72f90a5-78d3-41d6-91e6-818a7d38141c
title: "Asynchrone Kommunikation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - netzwerk
  - performance
  - synchronisation
  - rpc
  - client-server
  - middleware
  - asynchron
  - nachrichten
  - skalierbarkeit
  - fehlertoleranz
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Asynchrone Kommunikation]]

- **Kernkonzept:** Ein [[Kommunikationsmodell]] in [[verteilte Systeme|verteilten Systemen]], bei dem [[Sender]] und [[Empfänger]] nicht gleichzeitig aktiv sein müssen und [[Nachricht|Nachrichten]] in [[Warteschlange|Warteschlangen]] zwischengespeichert werden. Im Gegensatz zur [[synchrone Kommunikation|synchronen Kommunikation]] blockiert der [[Sender]] nicht auf eine Antwort des [[Empfänger|Empfängers]], was eine [[Lose_Kopplung|lose Kopplung]] der [[Kommunikationspartner]] ermöglicht und [[Entkopplung]] fördert.
- **Nutzen & Zweck:** Reduziert die Abhängigkeit von [[Netzwerk]]-[[Latenz|Latenzen]] und ermöglicht robustere [[Kommunikation]], da [[Empfänger]] [[Nachricht|Nachrichten]] verarbeiten können, sobald sie verfügbar sind. Dies fördert [[Skalierbarkeit]] und [[Fehlertoleranz]] in [[verteilte Systeme|verteilten Systemen]], da [[Prozess|Prozesse]] oder [[Komponente|Komponenten]] nicht aufeinander warten müssen. Besonders nützlich in Szenarien mit unvorhersehbaren [[Latenz|Latenzen]] oder temporären [[Ausfall|Ausfällen]], da es das [[Problem]] der [[Blockierung]] löst. Synchrone [[Kommunikation]] eignet sich hingegen für zeitkritische [[Operation|Operationen]], bei denen der [[Sender]] direkt auf eine Reaktion wartet und [[Koordination]] erforderlich ist.
- **Abgrenzung & Grenzen:** Nicht geeignet für Anwendungen, die sofortige Antworten oder [[Synchronisation]] erfordern (z. B. [[Echtzeit-System|Echtzeit-Systeme]] oder [[Transaktion|Transaktionen]] mit strengen [[Konsistenz]]-Anforderungen), da keine zeitliche Kopplung zwischen [[Sender]] und [[Empfänger]] besteht. Erfordert Mechanismen zur [[Pufferung]], [[Fehlerbehandlung]] und ggf. [[Persistente_Kommunikation|persistente Speicherung]] von [[Nachricht|Nachrichten]], was zu komplexeren [[Fehlerbehandlung|Fehlerbehandlungen]] und möglichen [[Performance]]-Einbußen führen kann. Synchrone [[Kommunikation]] blockiert den [[Sender]] bis zur Antwort, was die [[Skalierbarkeit]] einschränken kann, aber eine einfachere [[Koordination]] ermöglicht. Alternativen wie [[Message-oriented_Middleware|Message-oriented Middleware (MOM)]] oder [[Event-gesteuertes_System|Event-gesteuerte Systeme]] bieten flexible Lösungen für lose gekoppelte Szenarien.
- **Beispiel / Code:** ### Asynchrone Kommunikation (E-Mail-System):
Ein [[E-Mail]]-System überträgt [[Nachricht|Nachrichten]] asynchron zwischen [[Server|Servern]] und ermöglicht dem [[Empfänger]] den Abruf, sobald dieser online ist. Dies zeigt die [[Lose_Kopplung|lose Kopplung]] der [[Kommunikationspartner]].

**Beispiel 1: Asynchroner RPC mit Future (Java)**
```java
// Beispiel: Asynchroner RPC mit Future (Java)
Future<Integer> futureResult = remoteService.doCalculationAsync(5, 3);
// Client arbeitet weiter, ohne zu blockieren
int result = futureResult.get(); // Blockiert erst hier, falls Ergebnis noch nicht da ist
System.out.println("Ergebnis: " + result);
```

**Beispiel 2: Synchrone Kommunikation (RPC)**
```java
// Client-Seite (blockierend)
int result = remoteService.doCalculation(5, 3); // Blockiert bis Antwort da ist
System.out.println("Ergebnis: " + result);
```

**Beispiel 3: Asynchrone Kommunikation mit Message-oriented Middleware (Python, RabbitMQ)**
```python
import pika

# Verbindung zur Warteschlange herstellen
connection = pika.BlockingConnection(pika.ConnectionParameters('localhost'))
channel = connection.channel()

# Warteschlange deklarieren
channel.queue_declare(queue='task_queue', durable=True)

# Nachricht senden (asynchron)
channel.basic_publish(
    exchange='',
    routing_key='task_queue',
    body='Hallo, asynchrone Welt!',
    properties=pika.BasicProperties(delivery_mode=2)  # Persistente Nachricht
)

print(" [x] Nachricht gesendet")
connection.close()
```

Der Vergleich zeigt: Asynchrone Varianten nutzen [[Callback]]-Funktionen oder [[Future]]-Objekte, um Blockaden zu vermeiden. [[Message-oriented_Middleware|MOM]]-Systeme wie RabbitMQ ermöglichen die [[Pufferung]] und [[Persistente_Kommunikation|persistente Speicherung]] von [[Nachricht|Nachrichten]] in [[Warteschlange|Warteschlangen]], was die [[Entkopplung]] weiter verstärkt.
