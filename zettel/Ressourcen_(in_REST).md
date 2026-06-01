---
id: 8e43b136-d414-48d1-9e0b-a09012bcd40e
title: "Ressourcen (in REST)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - rest
  - verteilte-systeme
  - ressourcen
  - http
  - schnittstellen
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Ressourcen (in REST)]]

- **Kernkonzept:** In [[REST|REST-Architekturen]] sind [[Ressource|Ressourcen]] zentrale [[Entität|Entitäten]], die über ein einheitliches [[Namensschema]] identifiziert und von [[Service|Services]] verwaltet werden. Sie repräsentieren [[Zustand|Zustände]], die durch [[Operation|Operationen]] wie [[Erstellen]], [[Lesen]], [[Aktualisieren]] oder [[Löschen]] manipuliert werden.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der [[Kopplung|Kopplung]] in verteilten Systemen, indem es eine einheitliche [[Schnittstelle]] für den Zugriff auf [[Daten]] und [[Funktionalität|Funktionalitäten]] bietet. Es ermöglicht [[Skalierbarkeit]], [[Flexibilität]] und [[Interoperabilität]] durch standardisierte [[Protokoll|Protokolle]] wie [[HTTP]].
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit hoher [[Komplexität]] in der [[Logik]] oder starken [[Echtzeitanforderung|Echtzeitanforderungen]], da REST auf [[Statelessness]] und einfache [[Operation|Operationen]] setzt. Alternativen wie [[SOAP]] oder [[GraphQL]] bieten mehr [[Typsicherheit]] oder [[Abfrageflexibilität]], erfordern aber komplexere [[Schnittstelle|Schnittstellen]].
- **Beispiel / Code:** HTTP-Anfrage zum Erstellen einer Ressource (Bucket in Amazon S3):
```http
PUT /mybucket HTTP/1.1
Host: s3.amazonaws.com
Content-Length: 0
```

Vergleich mit SOAP (äquivalente Operation):
```python
import bucket
bucket.create("mybucket")
```
