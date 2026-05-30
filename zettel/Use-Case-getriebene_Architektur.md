---
id: 8986c3b8-ca08-44d3-8c2b-7f8c30ad9337
title: "Use-Case-getriebene_Architektur"
date: 2026-05-30
tags:
  - software_engineering
  - softwareentwurf
  - anforderungsanalyse
  - architektur
  - draft
source: "SWE Slides (Folien 211-225)"
---

# [[Use-Case-getriebene_Architektur]]

- **Kernkonzept:** [[Use-Case-getriebene_Architektur]] ist ein [[Entwurfsansatz]], bei dem die [[Systemarchitektur]] basierend auf den identifizierten [[Use-Case|Use-Cases]] und [[Akteur|Akteuren]] entwickelt wird.
- **Nutzen & Zweck:** Sie stellt sicher, dass die [[Architektur]] die funktionalen Anforderungen des Systems direkt unterstützt und vermeidet [[Over-Engineering]].
- **Abgrenzung & Grenzen:** Kann zu einer zu starken Fokussierung auf einzelne [[Use-Case|Use-Cases]] führen und [[Nicht-funktionale_Anforderung|nicht-funktionale Anforderungen]] (z. B. [[Performance]], [[Sicherheit]]) vernachlässigen.
- **Beispiel / Code:** ```uml
@startuml
actor User

User -> (Manage Members)
User -> (Authenticate User)

component "MemberManagement" as mm
component "Authentication" as auth

(Manage Members) --> mm
(Authenticate User) --> auth
@enduml
```
