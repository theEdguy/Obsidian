---
id: 2de3376c-6a9a-47cf-a653-d6fbcdf6aa1f
title: "System-Use_Case"
date: 2026-05-30
tags:
  - software_engineering
  - requirements_engineering
  - design
  - draft
source: "SWE Slides (Folien 241-255)"
---

# [[System-Use_Case]]

- **Kernkonzept:** Ein [[Use_Case]], der im [[Design]] konkretisiert wird und die [[Systemoperation|Systemoperationen]] sowie [[Interaktion]] mit dem [[System]] auf technischer Ebene beschreibt. Basiert auf [[Analyse|Analyse]]-Ergebnissen, aber mit Fokus auf [[Implementierung]].
- **Nutzen & Zweck:** Überbrückt die Lücke zwischen [[Anforderung|Anforderungen]] und [[Implementierung]], indem [[Use_Case|Use Cases]] aus der [[Analyse]] in technische [[Spezifikation|Spezifikationen]] überführt werden. Unterstützt die [[Kommunikation]] zwischen [[Stakeholder|Stakeholdern]] und Entwicklern.
- **Abgrenzung & Grenzen:** Keine reine [[Anforderung|Anforderungs]]-Beschreibung, sondern eine technische Verfeinerung. Unterscheidet sich von [[Geschäfts-Use_Case|Geschäfts-Use Cases]] durch den Fokus auf [[System]]-Interaktion.
- **Beispiel / Code:** ```markdown
# System-Use Case: Manage Members
- **Akteur**: Administrator
- **Systemoperationen**:
  - addMember(name, email)
  - removeMember(memberId)
  - listMembers()
- **Erweiterungen**: Technische Use Cases wie "Mitglied exportieren"
```
