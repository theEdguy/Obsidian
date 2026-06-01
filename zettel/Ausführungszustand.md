---
id: c78b54d0-8e4b-413a-b515-d9dcae367c62
title: "Ausführungszustand"
date: 2026-06-01
tags:
  - verteilte_systeme
  - mobilitaet
  - prozessverwaltung
  - kontextmanagement
  - heterogenitaet
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Ausführungszustand]]

- **Kernkonzept:** Der [[Ausführungszustand]] beschreibt den dynamischen [[Kontext|Kontexte]] eines [[Thread|Threads]] oder [[Prozess|Prozesses]], einschließlich [[Programmzähler]], [[Stack]] und [[Registerinhalt|Registerinhalte]], der die Fortsetzung einer [[Berechnung]] nach einer [[Migration]] ermöglicht.
- **Nutzen & Zweck:** Er ermöglicht [[starke Mobilität]] in [[verteilten Systemen]], indem er die exakte Wiederaufnahme einer [[Berechnung]] auf einem anderen [[Knoten]] ohne Neustart erlaubt. Dies löst das [[Problem]] der [[Unterbrechung]] von [[Prozess|Prozessen]] bei [[Code-Migration]] und verbessert die [[Effizienz]] und [[Kontinuität]] von [[verteilten Anwendungen]].
- **Abgrenzung & Grenzen:** Nicht sinnvoll in [[heterogenen Systemen]] ohne [[abstrakte Maschine]], da [[Hardware]]- und [[Betriebssystem]]-abhängige [[Kontext|Kontexte]] nicht direkt übertragbar sind. Unterscheidet sich von [[schwacher Mobilität]], die nur [[Code]] und [[Daten]] migriert und einen Neustart erfordert. [[Mobile Agents]] nutzen [[Ausführungszustand|Ausführungszustände]], während [[Code-on-Demand]] (CoD) darauf verzichtet.
- **Beispiel / Code:** In Java könnte ein serialisierter [[Thread]]-Zustand (z. B. via `ObjectOutputStream`) den [[Ausführungszustand]] speichern:
```java
// Serialisierung des Ausführungszustands
ByteArrayOutputStream bos = new ByteArrayOutputStream();
ObjectOutputStream oos = new ObjectOutputStream(bos);
oos.writeObject(currentThread.getStackTrace());
oos.writeObject(registerValues);
```
Die Deserialisierung auf dem Zielknoten stellt den [[Kontext]] wieder her, um die [[Berechnung]] fortzusetzen.
