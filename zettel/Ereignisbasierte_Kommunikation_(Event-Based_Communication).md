---
id: c5f0cc57-9127-4968-a0cd-549167fc9fc7
title: "Ereignisbasierte Kommunikation (Event-Based Communication)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - ereignisbasiert
  - publish-subscribe
  - koordination
  - entkopplung
  - kommunikation
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Ereignisbasierte Kommunikation (Event-Based Communication)]]

- **Kernkonzept:** Ein [[Architekturstil|Architekturstil]] in [[Verteilte Systeme|verteilten Systemen]], bei dem [[Komponente|Komponenten]] über [[Ereignis|Ereignisse]] kommunizieren, die von [[Publisher|Publishern]] erzeugt und von [[Subscriber|Subscribern]] konsumiert werden, ohne direkte referenzielle oder temporale [[Kopplung|Kopplung]].
- **Nutzen & Zweck:** Löst das [[Problem]] der engen [[Kopplung]] in [[Verteilte Systeme|verteilten Systemen]], indem es [[Komponente|Komponenten]] ermöglicht, asynchron und unabhängig voneinander zu agieren. Ermöglicht skalierbare, flexible [[Systeme]], die auf [[Änderung|Änderungen]] oder [[Ereignis|Ereignisse]] reagieren, ohne direkte Abhängigkeiten.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Anwendung|Anwendungen]], die starke [[Konsistenz]] oder synchrone [[Antwort|Antworten]] erfordern. Unterscheidet sich von [[Request-Response-Modell|Request-Response-Modellen]] durch fehlende direkte [[Kopplung]] und von [[Message-Queue|Message-Queues]] durch die fehlende Persistenz der [[Nachricht|Nachrichten]]. Weniger effizient für einfache, direkte [[Kommunikation]] zwischen zwei [[Komponente|Komponenten]].
- **Beispiel / Code:** Ein einfaches Publish-Subscribe-Beispiel mit einem Ereignis-Bus:

```python
# Publisher
class EventBus:
    def __init__(self):
        self.subscribers = {}

    def subscribe(self, event_type, subscriber):
        if event_type not in self.subscribers:
            self.subscribers[event_type] = []
        self.subscribers[event_type].append(subscriber)

    def publish(self, event_type, data):
        if event_type in self.subscribers:
            for subscriber in self.subscribers[event_type]:
                subscriber(data)

# Subscriber
def log_event(data):
    print(f"Event received: {data}")

# Nutzung
bus = EventBus()
bus.subscribe("user_created", log_event)
bus.publish("user_created", {"user_id": 123, "name": "Alice"})
```

*Ausgabe:* `Event received: {'user_id': 123, 'name': 'Alice'}`
