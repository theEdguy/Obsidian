---
id: bdbeac87-a6cf-408d-a889-61a797644a66
title: "Ressourcenbasierte Architekturen (Resource-Oriented Architectures)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architekturstil
  - rest
  - ressourcenorientierung
  - http
  - schnittstellen
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Ressourcenbasierte Architekturen (Resource-Oriented Architectures)]]

- **Kernkonzept:** Ressourcenbasierte Architekturen organisieren [[verteiltes_System|verteilte Systeme]] als Sammlung von [[Ressource|Ressourcen]], die über ein einheitliches [[Schnittstellen|Schnittstellen]]-Design und ein gemeinsames [[Namensschema|Namensschema]] identifiziert und manipuliert werden. Sie folgen dem REST-Architekturstil, bei dem [[Operation|Operationen]] zustandslos und selbstbeschreibend sind.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der [[Komplexität]] in [[verteilten_System|verteilten Systemen]], indem es eine einheitliche, skalierbare und flexible [[Interaktion]] zwischen [[Komponente|Komponenten]] ermöglicht. Es reduziert die [[Kopplung]] durch standardisierte [[Schnittstelle|Schnittstellen]] (z. B. HTTP) und fördert die [[Wiederverwendbarkeit]] von [[Ressource|Ressourcen]] über verschiedene [[Anwendung|Anwendungen]] hinweg.
- **Abgrenzung & Grenzen:** Ressourcenbasierte Architekturen eignen sich weniger für [[Anwendung|Anwendungen]] mit hoher [[Transaktionslast]] oder komplexen [[Ablaufsteuerung|Ablaufsteuerungen]], da sie keine [[Prozedur|prozedurale]] oder [[Objekt|objektorientierte]] [[Logik]] direkt abbilden. Im Vergleich zu [[SOAP]] oder [[RPC]] fehlt [[Typsicherheit]], was die [[Fehlererkennung]] erschwert. Alternativen wie [[Service-orientierte_Architektur|service-orientierte Architekturen]] oder [[Objekt-basierte_Architektur|objektbasierte Architekturen]] bieten mehr [[Kontrolle]] über [[Datenformat|Datenformate]] und [[Ablauf]].
- **Beispiel / Code:** {'beschreibung': 'Beispiel für eine CRUD-Operation auf einer Ressource via HTTP (REST):', 'code': {'erstellen': 'PUT http://example.com/ressourcen/123\nContent-Type: application/json\n\n{"name": "Beispiel", "wert": 42}', 'lesen': 'GET http://example.com/ressourcen/123', 'aktualisieren': 'POST http://example.com/ressourcen/123\nContent-Type: application/json\n\n{"name": "Geändert", "wert": 100}', 'löschen': 'DELETE http://example.com/ressourcen/123'}, 'hinweis': 'Die Ressource wird über eine URI identifiziert, und die Operationen folgen dem HTTP-Standard (z. B. PUT für Erstellung, GET für Abruf).'}
