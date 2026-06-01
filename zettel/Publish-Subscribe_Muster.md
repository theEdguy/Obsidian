---
id: a733af45-2355-415e-97e3-8c7f41dcae94
title: "Publish-Subscribe Muster"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - kommunikationsmuster
  - ereignisgesteuert
  - entkopplung
  - nachrichtenorientiert
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Publish-Subscribe Muster]]

- **Kernkonzept:** Das Publish-Subscribe Muster ermöglicht die [[Entkopplung|entkoppelte]] Kommunikation zwischen [[Komponente|Komponenten]], bei der [[Nachricht|Nachrichten]] von [[Publisher|Publishern]] veröffentlicht und von [[Subscriber|Subscribern]] empfangen werden, ohne direkte Abhängigkeiten.
- **Nutzen & Zweck:** Es löst das Problem der [[Skalierbarkeit|skalierbaren]] und flexiblen [[Datenverteilung|Datenverteilung]] in [[Verteilte Systeme|verteilten Systemen]], indem es [[Ereignis|Ereignisse]] effizient an mehrere [[Empfänger|Empfänger]] übermittelt, ohne dass diese sich gegenseitig kennen müssen.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Szenario|Szenarien]], die eine strikte [[Request-Reply|Request-Reply]]-Semantik oder [[Transaktion|transaktionale]] [[Garantie|Garantien]] erfordern. Unterscheidet sich von [[Point-to-Point|Point-to-Point]]-Kommunikation (z. B. [[RPC]]) durch die [[Entkopplung|entkoppelte]] und [[Multicast|multicastfähige]] Natur. Bei hohen [[Latenz|Latenzanforderungen]] oder [[Echtzeit|Echtzeit]]-Systemen kann die asynchrone Natur nachteilig sein.
- **Beispiel / Code:** {'beschreibung': 'Ein [[Publisher]] sendet regelmäßig Zeitstempel an alle [[Subscriber]], die sich für das Thema "TIME" registriert haben. Der [[Subscriber]] empfängt nur die für ihn relevanten [[Nachricht|Nachrichten]].', 'publisher': {'sprache': 'Python (ZeroMQ)', 'code': 'import zmq, time\ncontext = zmq.Context()\ns = context.socket(zmq.PUB)\ns.bind("tcp://*:5556")\nwhile True:\n    time.sleep(5)\n    s.send("TIME " + time.asctime())'}, 'subscriber': {'sprache': 'Python (ZeroMQ)', 'code': 'import zmq\ncontext = zmq.Context()\ns = context.socket(zmq.SUB)\ns.connect("tcp://localhost:5556")\ns.setsockopt(zmq.SUBSCRIBE, "TIME")\nfor i in range(5):\n    print(s.recv())'}}
