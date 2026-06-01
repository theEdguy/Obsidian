---
id: f6fe72ac-a4e4-41b7-aa6e-0175332f0f0b
title: "Publish-Subscribe-Architekturen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - ereignisbasiert
  - koordination
  - mqtt
  - pubsub
  - entkopplung
  - nachrichtenmuster
  - middleware
  - ereignisgesteuert
  - tupelraum
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Publish-Subscribe-Architekturen]]

- **Kernkonzept:** Ein [[Architekturstil|Architekturstil]] und [[Nachrichtenmuster|Nachrichtenmuster]], bei dem [[Komponente|Komponenten]] Nachrichten über einen [[Ereignis-Bus]], [[Broker]] oder [[Tupelraum|Tupelraum]] veröffentlichen (publish) oder abonnieren (subscribe), ohne direkte [[Referenz|Referenzen]] zueinander zu benötigen. Dies ermöglicht [[temporale_Entkopplung|temporale]] und [[referenzielle_Entkopplung|referenzielle Entkopplung]] sowie [[räumliche_Entkopplung|räumliche Entkopplung]] der [[Komponente|Komponenten]].
- **Nutzen & Zweck:** Löst das [[Problem]] der [[Skalierbarkeit]] und [[Flexibilität]] in [[verteilte_Systeme|verteilten Systemen]], indem es [[Komponente|Komponenten]] ermöglicht, asynchron und ohne direkte [[Abhängigkeit|Abhängigkeiten]] zu kommunizieren. Besonders nützlich für [[Echtzeitdaten|Echtzeitdaten]]-Verarbeitung, [[Ereignisgesteuerte_Systeme|ereignisgesteuerte Systeme]], [[IoT]]-Anwendungen und [[Microservice|Microservice-Architekturen]]. Durch die [[Entkopplung|Entkopplung]] von [[Publisher|Publishern]] und [[Subscriber|Subscribern]] wird die Wartbarkeit und Erweiterbarkeit des Systems verbessert, da neue [[Komponente|Komponenten]] hinzugefügt werden können, ohne bestehende zu modifizieren.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Szenario|Szenarien]], die [[starke_Konsistenz|starke Konsistenz]], [[synchrone_Kommunikation|synchrone Kommunikation]] oder garantierte Zustellung mit Bestätigung erfordern, z. B. [[Transaktion|Transaktionen]] in [[Datenbank|Datenbanken]]. Im Vergleich zu [[Request-Response|Request-Response]]- oder [[RPC]]-Modellen fehlt die direkte Rückmeldung, was die Fehlerbehandlung erschweren kann. Zudem kann die [[Latenz|Latenz]] bei hoher [[Nachrichtenlast|Nachrichtenlast]] oder komplexen [[Filtermechanismus|Filtermechanismen]] ansteigen. Alternativen wie [[Message_Queue|Message Queues]] oder [[Client-Server-Architektur|Client-Server-Architekturen]] sind in solchen Fällen oft besser geeignet. Die [[Publish-Subscribe-Architektur]] unterscheidet sich von [[Observer_Pattern|Observer-Mustern]] durch die zentrale Rolle eines [[Broker|Brokers]] oder [[Tupelraum|Tupelraums]], der die Verteilung der Nachrichten übernimmt.
- **Beispiel / Code:** ### Beispiel 1: MQTT (Publish-Subscribe-Protokoll)
**Publisher (Python mit Paho-MQTT):**
```python
import paho.mqtt.client as mqtt

client = mqtt.Client()
client.connect("broker.hivemq.com", 1883)
client.publish("temperatur/sensor1", "23.5°C")
client.disconnect()
```

**Subscriber (Python mit Paho-MQTT):**
```python
def on_message(client, userdata, msg):
    print(f"Topic: {msg.topic}, Nachricht: {msg.payload.decode()}")

client = mqtt.Client()
client.connect("broker.hivemq.com", 1883)
client.subscribe("temperatur/#")
client.on_message = on_message
client.loop_forever()
```

*Erläuterung*: Der [[Publisher]] sendet eine Nachricht an ein [[Topic]], ohne den [[Subscriber]] zu kennen. Der [[Subscriber]] abonniert das [[Topic]] und erhält alle Nachrichten dazu. Der [[Broker]] vermittelt die Kommunikation.

---

### Beispiel 2: Linda-Tupelraum (Pseudocode)
```
# Publisher (Bob)
blog = linda.universe._rd(("MicroBlog", linda.TupleSpace))[1]
blog._out(("bob", "distsys", "I am studying chap 2"))
blog._out(("bob", "distsys", "The Linda example is simple"))

# Subscriber (Chuck)
blog = linda.universe._rd(("MicroBlog", linda.TupleSpace))[1]
t1 = blog._rd(("bob", "distsys", str))  # Blockiert bis passendes Tupel verfügbar
print(t1)  # Ausgabe: ("bob", "distsys", "I am studying chap 2")
```

*Erläuterung*: Der [[Tupelraum]] fungiert als [[Broker]], der [[Tupel|Tupel]] speichert und an [[Subscriber|Subscriber]] verteilt, die nach bestimmten Mustern filtern. Dies zeigt die [[räumliche_Entkopplung|räumliche Entkopplung]] der [[Komponente|Komponenten]].
