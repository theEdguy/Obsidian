---
id: 5c63bec8-a644-468c-9a69-f025f8a18ab6
title: "CRUD-Operationen (Create, Read, Update, Delete)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - datenverwaltung
  - rest
  - http
  - schnittstellen
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[CRUD-Operationen (Create, Read, Update, Delete)]]

- **Kernkonzept:** CRUD-Operationen bilden die grundlegenden [[Aktion|Aktionen]] zur Verwaltung von [[Daten|Datenbeständen]] in [[System|Systemen]], insbesondere in [[verteilte Systeme|verteilten Systemen]]. Sie ermöglichen das Erstellen (Create), Lesen (Read), Aktualisieren (Update) und Löschen (Delete) von [[Ressource|Ressourcen]].
- **Nutzen & Zweck:** Das Konzept standardisiert die [[Interaktion|Interaktionen]] mit [[Daten|Daten]] und vereinfacht die [[Implementierung|Implementierungen]] von [[Schnittstelle|Schnittstellen]], insbesondere in [[REST-Architektur|REST-Architekturen]]. Es löst das [[Problem]] der einheitlichen [[Datenmanipulation|Datenmanipulation]] in heterogenen [[System|Systemen]] und reduziert die Komplexität bei der [[Entwicklung|Entwicklung]] von [[Anwendung|Anwendungen]].
- **Abgrenzung & Grenzen:** CRUD ist nicht geeignet für [[Systeme]], die komplexe [[Transaktion|Transaktionen]] oder [[Echtzeitverarbeitung|Echtzeitverarbeitungen]] erfordern. Alternativen wie [[Event-Sourcing]] oder [[CQRS]] (Command Query Responsibility Segregation) bieten hier mehr Flexibilität. Zudem ist CRUD weniger effizient für [[Daten|Datenbestände]] mit hoher [[Schreibhäufigkeit|Schreibhäufigkeit]] oder [[Konflikt|Konfliktanfälligkeit]].
- **Beispiel / Code:** HTTP-basierte CRUD-Operationen für eine Ressource (z. B. `/users`):

- **Create (POST)**: `POST /users` mit Nutzerdaten im Request-Body.
- **Read (GET)**: `GET /users/1` zum Abrufen des Nutzers mit ID 1.
- **Update (PUT/PATCH)**: `PUT /users/1` mit aktualisierten Nutzerdaten.
- **Delete (DELETE)**: `DELETE /users/1` zum Löschen des Nutzers.

Beispiel (HTTP-Request für Create):
```http
POST /users HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "name": "Max Mustermann",
  "email": "max@example.com"
}
```
