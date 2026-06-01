---
id: 4e447b3e-5f81-4400-a76c-cfc1d36570ba
title: "Ereignis-Bus (Event Bus)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - ereignisgesteuert
  - koordination
  - middleware
  - publish-subscribe
  - lose-kopplung
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Ereignis-Bus (Event Bus)]]

- **Kernkonzept:** Ein [[Ereignis-Bus|Ereignis-Bus]] ist ein [[Architekturstil|Architekturmuster]] in [[Verteilte Systeme|verteilten Systemen]], das [[Komponente|Komponenten]] ermöglicht, [[Ereignis|Ereignisse]] zu [[veröffentlichen|veröffentlichen]] (publish) oder [[abonnieren|abonnieren]] (subscribe), ohne direkt voneinander abhängig zu sein.
- **Nutzen & Zweck:** Der [[Ereignis-Bus]] löst das [[Problem]] der [[temporalen]] und [[referenziellen Kopplung]] in [[Verteilte Systeme|verteilten Systemen]]. Er ermöglicht [[lose Kopplung]] zwischen [[Komponente|Komponenten]], indem [[Ereignis|Ereignisse]] zentral vermittelt werden, ohne dass [[Sender]] und [[Empfänger]] direkt kommunizieren müssen. Dies fördert [[Skalierbarkeit]] und [[Flexibilität]] in dynamischen [[Systeme|Systemen]].
- **Abgrenzung & Grenzen:** Ein [[Ereignis-Bus]] ist ungeeignet, wenn [[Echtzeit-Anforderungen]] oder [[starke Konsistenz]] benötigt werden, da die [[Verarbeitung]] von [[Ereignis|Ereignissen]] asynchron und nicht deterministisch erfolgt. Alternativen wie [[direkte Kommunikation]] (z. B. [[RPC]]) oder [[geteilte Datenräume]] bieten hier Vorteile. Zudem kann ein [[Ereignis-Bus]] zu [[Komplexität]] führen, wenn die [[Ereignis|Ereignisflüsse]] schwer nachvollziehbar sind oder [[Fehlerbehandlung]] schwierig wird.
- **Beispiel / Code:** Ein einfaches Beispiel für einen [[Ereignis-Bus]] in Python mit dem `paho-mqtt`-Modul:

```python
import paho.mqtt.client as mqtt

# Publisher
client = mqtt.Client()
client.connect("localhost", 1883)
client.publish("temperatur/sensor1", "23.5°C")

# Subscriber
def on_message(client, userdata, msg):
    print(f"Empfangen: {msg.payload.decode()} auf Topic {msg.topic}")

client = mqtt.Client()
client.connect("localhost", 1883)
client.subscribe("temperatur/#")
client.on_message = on_message
client.loop_forever()
```

Hier fungiert der MQTT-Broker als [[Ereignis-Bus]], der [[Nachricht|Nachrichten]] zwischen [[Publisher]] und [[Subscriber]] vermittelt.
