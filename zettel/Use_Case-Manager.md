---
id: 55d9389d-ef9e-46e7-844e-f49c79ac0491
title: "Use_Case-Manager"
date: 2026-05-30
tags:
  - software_engineering
  - softwarearchitektur
  - use_case
  - design_principle
  - draft
source: "SWE Slides (Folien 316-330)"
---

# [[Use_Case-Manager]]

- **Kernkonzept:** Ein [[Use_Case-Manager]] ist ein zentraler [[Akteur|Akteur]] in der [[Softwarearchitektur]], der alle [[Operation|Operationen]] eines spezifischen [[Use_Case|Use Cases]] bündelt und verantwortet. Er dient als Schnittstelle zwischen dem [[System]] und den [[Komponente|Komponenten]], die den [[Use_Case]] umsetzen.
- **Nutzen & Zweck:** Der [[Use_Case-Manager]] löst das Problem der verteilten Verantwortung in [[System|Systemen]] und fördert die [[Kohäsion]] durch die zentrale Steuerung aller [[Operation|Operationen]] eines [[Use_Case|Use Cases]]. Dies vereinfacht die [[Wartbarkeit]] und [[Erweiterbarkeit]] des [[Systems]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Use_Case|Use Cases]] stark voneinander abhängen oder wenn die [[Komplexität]] des [[Systems]] durch zu viele [[Manager]] unnötig erhöht wird. Alternativ können [[Fassade|Fassaden]] oder [[Mediator_Pattern|Mediatoren]] eingesetzt werden, um ähnliche Ziele zu erreichen.
- **Beispiel / Code:** ```java
public class ManageMembers {
    private Vereinsmanager manager;
    
    public void addMember(Member member) {
        manager.validate(member);
        manager.persist(member);
    }
    
    public void removeMember(Member member) {
        manager.remove(member);
    }
}
```
