---
id: 5e61babb-9d1f-40ec-ac46-2dc996edad97
title: "REST-Architekturstil (Representational State Transfer)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architekturstil
  - verteilte-systeme
  - webservices
  - http
  - ressourcenorientiert
  - api-design
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[REST-Architekturstil (Representational State Transfer)]]

- **Kernkonzept:** Der [[REST-Architekturstil]] definiert ein verteiltes [[System|Systeme]] als Sammlung von [[Ressource|Ressourcen]], die über ein einheitliches [[Interface]] und ein gemeinsames [[Namensschema]] (z. B. URIs) adressierbar sind. [[Operation|Operationen]] wie CRUD werden über standardisierte [[Protokoll|Protokolle]] (z. B. HTTP) ausgeführt, wobei [[Nachricht|Nachrichten]] selbstbeschreibend sind.
- **Nutzen & Zweck:** REST löst das [[Problem]] der [[Skalierbarkeit]] und [[Interoperabilität]] in verteilten [[System|Systemen]], indem es [[Komponente|Komponenten]] entkoppelt, [[Schnittstelle|Schnittstellen]] vereinheitlicht und [[Zustand|Zustände]] über [[Repräsentation|Repräsentationen]] (z. B. JSON/XML) austauschbar macht. Es ermöglicht einfache Integration und [[Wartbarkeit]] durch Nutzung etablierter [[Webstandard|Webstandards]].
- **Abgrenzung & Grenzen:** REST ist ungeeignet für [[Anwendung|Anwendungen]] mit komplexen [[Transaktion|Transaktionen]], hoher [[Latenz|Latenzempfindlichkeit]] oder starker [[Kopplung]] zwischen [[Komponente|Komponenten]]. Alternativen wie [[SOAP]] (strikte [[Typsicherheit]]) oder [[GraphQL]] (flexible [[Abfrage|Abfragen]]) bieten mehr [[Funktionalität]] für spezifische [[Anforderung|Anforderungen]], erfordern aber oft mehr [[Aufwand]] in der [[Implementierung]]. REST verzichtet bewusst auf [[Session|Sessions]] und [[Zustand|Zustandshaltung]] auf Serverseite (stateless).
- **Beispiel / Code:** HTTP-Anfrage zum Erstellen einer [[Ressource]] (Create-Operation via POST):
```http
POST /api/books HTTP/1.1
Host: example.com
Content-Type: application/json

{
  "title": "Verteilte Systeme",
  "author": "Christian Zirpins"
}
```

Antwort mit [[Repräsentation]] der erstellten [[Ressource]]:
```http
HTTP/1.1 201 Created
Content-Type: application/json
Location: /api/books/123

{
  "id": 123,
  "title": "Verteilte Systeme",
  "author": "Christian Zirpins"
}
```
