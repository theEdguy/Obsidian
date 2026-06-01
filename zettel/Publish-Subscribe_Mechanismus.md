---
id: 96bef556-6ca3-473e-a38a-de1ccb47b50d
title: "Publish-Subscribe Mechanismus"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - nachrichtenorientierte-kommunikation
  - middleware
  - ereignisgesteuerte-architektur
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Publish-Subscribe Mechanismus]]

- **Kernkonzept:** Der Publish-Subscribe Mechanismus ist ein [[Nachrichtenmuster|Nachrichtenmuster]], bei dem [[Nachricht|Nachrichten]] von [[Publisher|Publishern]] veröffentlicht und von [[Subscriber|Subscribern]] basierend auf [[Thema|Themen]] oder [[Ereignis|Ereignissen]] empfangen werden, ohne direkte Kopplung zwischen den [[Kommunikationspartner|Kommunikationspartnern]].
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der [[Entkopplung]] in [[Verteilte Systeme|verteilten Systemen]], indem es [[Skalierbarkeit]], [[Flexibilität]] und [[Echtzeitkommunikation]] ermöglicht. Es eignet sich besonders für [[Anwendungsfall|Anwendungsfälle]], bei denen [[Daten]] an viele [[Empfänger]] verteilt werden müssen, ohne dass diese sich gegenseitig kennen oder synchronisiert sein müssen.
- **Abgrenzung & Grenzen:** Der Publish-Subscribe Mechanismus sollte nicht genutzt werden, wenn eine direkte [[Antwort]] oder [[Bestätigung]] des Empfangs erforderlich ist, da er asynchron und entkoppelt arbeitet. Alternativen wie [[Request-Reply]] oder [[RPC]] sind besser geeignet, wenn [[Synchronisation]] oder [[Transaktion]]en benötigt werden. Zudem ist er weniger effizient für [[Punkt-zu-Punkt-Kommunikation]], da alle [[Subscriber]] die [[Nachricht]] erhalten, auch wenn nur ein [[Empfänger]] relevant ist.
- **Beispiel / Code:** Ein einfaches Beispiel mit einem Message Broker (z. B. MQTT):

```python
# Publisher
import paho.mqtt.client as mqtt
client = mqtt.Client()
client.connect("broker.example.com", 1883)
client.publish("temperatur/sensor1", "23.5°C")

# Subscriber
def on_message(client, userdata, msg):
    print(f"Empfangen: {msg.payload.decode()} auf Thema {msg.topic}")

client = mqtt.Client()
client.connect("broker.example.com", 1883)
client.subscribe("temperatur/#")
client.on_message = on_message
client.loop_forever()
```

Hier veröffentlicht ein [[Publisher]] eine [[Nachricht]] zum [[Thema]] `temperatur/sensor1`, und alle [[Subscriber]], die dieses [[Thema]] abonniert haben, erhalten die [[Nachricht]].
