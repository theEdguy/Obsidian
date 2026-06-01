---
id: b0eed78f-385b-4bbb-8ea2-ec31c5dbbfce
title: "Zustandsloser Server"
date: 2026-06-01
tags:
  - verteilte_systeme
  - server_architektur
  - skalierbarkeit
  - netzwerkprotokolle
  - zustandsmanagement
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Zustandsloser Server]]

- **Kernkonzept:** Ein [[zustandsloser|zustandsloser]] [[Server]] verwaltet keine [[Information|Informationen]] über den [[Zustand]] seiner [[Client|Clients]] zwischen einzelnen [[Anfrage|Anfragen]]. Jede [[Interaktion]] ist in sich abgeschlossen und enthält alle notwendigen [[Daten]].
- **Nutzen & Zweck:** Das Konzept löst [[Probleme]] der [[Skalierbarkeit]] und [[Ausfallsicherheit]] in [[verteilten Systemen]], indem es [[Abhängigkeiten]] zwischen [[Anfrage|Anfragen]] eliminiert. Es vereinfacht die [[Wiederherstellung]] nach [[Fehler|Fehlern]] und ermöglicht [[Lastverteilung]] ohne [[Zustandssynchronisation]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Performanz]] durch [[Zustandsvorhaltung]] (z. B. [[Caching]] oder [[Vorauslesen]]) optimiert werden muss. Unterscheidet sich von [[zustandsbehafteten Servern]], die [[Client|Client-]]spezifische [[Daten]] speichern, aber höhere [[Komplexität]] in [[Fehlerbehandlung]] und [[Skalierung]] aufweisen.
- **Beispiel / Code:** Ein HTTP-Server (z. B. REST-API) verarbeitet jede [[Anfrage]] unabhängig:
```
GET /api/resource/123
Host: example.com
```
Der Server antwortet mit den [[Daten]] zu Ressource 123, ohne zu speichern, ob der [[Client]] diese zuvor angefordert hat.
