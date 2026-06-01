---
id: eb2f5ee9-ed4e-44c6-a250-f55c59adc6d6
title: "Warteschlange (Queue)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - middleware
  - asynchron
  - datenstruktur
  - fehlertoleranz
  - skalierung
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Warteschlange (Queue)]]

- **Kernkonzept:** Eine [[Warteschlange|Warteschlange]] ist ein Datenstruktur-Konzept, das [[Nachricht|Nachrichten]] oder [[Aufgabe|Aufgaben]] nach dem FIFO-Prinzip (First-In-First-Out) zwischenspeichert und sequenziell verarbeitet. Sie ermöglicht [[asynchrone Kommunikation]] in [[verteilte Systeme|verteilten Systemen]].
- **Nutzen & Zweck:** Eine [[Warteschlange|Warteschlange]] löst das Problem der [[Entkopplung]] von [[Sender]] und [[Empfänger]] in [[verteilte Systeme|verteilten Systemen]], indem sie [[Nachricht|Nachrichten]] persistent speichert und deren Auslieferung garantiert. Sie ermöglicht [[skalierbare]] und [[fehlertolerante]] Kommunikation, da [[Prozess|Prozesse]] nicht gleichzeitig aktiv sein müssen und [[Lastspitzen]] abgefedert werden können.
- **Abgrenzung & Grenzen:** Eine [[Warteschlange|Warteschlange]] sollte nicht genutzt werden, wenn [[Echtzeitkommunikation]] oder direkte [[Antwort|Antworten]] erforderlich sind, da sie [[Latenz]] einführt. Alternativen wie [[Remote Procedure Call (RPC)]] oder [[transiente Kommunikation]] eignen sich besser für synchrone [[Interaktion|Interaktionen]], bei denen [[Blockierung]] akzeptabel ist. Zudem ist sie überdimensioniert für einfache [[Punkt-zu-Punkt-Kommunikation]] ohne [[Pufferungsbedarf]].
- **Beispiel / Code:** Ein Beispiel für eine [[Message-oriented Middleware (MOM)]] mit [[Warteschlange|Warteschlangen]] in Python (Pseudocode):

```python
from queue import Queue
from threading import Thread

# Warteschlange initialisieren
message_queue = Queue()

def producer():
    message_queue.put("Datenpaket 1")
    message_queue.put("Datenpaket 2")

def consumer():
    while True:
        message = message_queue.get()  # Blockiert, bis Nachricht verfügbar
        print(f"Verarbeite: {message}")
        message_queue.task_done()

# Threads starten
Thread(target=producer, daemon=True).start()
Thread(target=consumer, daemon=True).start()
```

In [[verteilte Systeme|verteilten Systemen]] wird dies typischerweise durch Middleware wie RabbitMQ oder Apache Kafka realisiert.
