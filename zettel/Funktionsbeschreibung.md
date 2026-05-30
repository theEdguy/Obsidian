---
id: 3448874e-90a8-4365-b918-c292e2a44d75
title: "Funktionsbeschreibung"
date: 2026-05-30
tags:
  - software_engineering
  - dokumentation
  - design_principle
  - draft
source: "SWE Slides (Folien 241-255)"
---

# [[Funktionsbeschreibung]]

- **Kernkonzept:** Eine formale Beschreibung einer [[Systemoperation]], die [[Parameter]], [[Rückgabewert|Rückgabewerte]], [[Ausnahme|Ausnahmen]], Vor- und Nachbedingungen sowie den Zweck der [[Operation]] dokumentiert.
- **Nutzen & Zweck:** Schafft Klarheit über die [[Verantwortung]] einer [[Systemoperation]] und dient als Vertrag zwischen [[Komponente|Komponenten]]. Unterstützt die [[Testbarkeit]] und [[Wartbarkeit]] des [[Systems]].
- **Abgrenzung & Grenzen:** Keine Implementierungsdetails, sondern eine abstrakte Beschreibung der [[Funktionalität]]. Unterscheidet sich von [[Kommentar|Kommentaren]] im [[Code]] durch ihre formale Struktur und [[Use_Case]]-Bezug.
- **Beispiel / Code:** ```markdown
# Funktionsbeschreibung: addMember
- **Parameter**: name (String), email (String)
- **Rückgabewert**: MemberId (UUID)
- **Ausnahmen**: InvalidEmailException, DuplicateMemberException
- **Vorbedingung**: Benutzer ist authentifiziert
- **Nachbedingung**: Neues Mitglied ist im System registriert
```
