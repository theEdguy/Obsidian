---
id: 4d1991fb-e59e-4c20-91bf-72152efb8123
title: "Use_Case-spezifische_Komponente"
date: 2026-05-30
tags:
  - software_engineering
  - architektur
  - design_principle
  - draft
source: "SWE Slides (Folien 241-255)"
---

# [[Use_Case-spezifische_Komponente]]

- **Kernkonzept:** Eine [[Komponente]], die genau einen [[Use_Case]] oder [[Akteur]] in einem [[System]] realisiert. Sie kapselt alle [[Systemoperation|Systemoperationen]] und [[Logik]], die für diesen [[Use_Case]] benötigt werden.
- **Nutzen & Zweck:** Fördert die [[Kohäsion]] und [[Modularität]] durch die klare Zuordnung von [[Verantwortung|Verantwortlichkeiten]] zu [[Use_Case|Use Cases]]. Erleichtert die [[Wiederverwendbarkeit]] und [[Erweiterbarkeit]] des [[Systems]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Use_Case|Use Cases]], die stark miteinander verwoben sind. Unterscheidet sich von [[Fachliche_Komponente|fachlichen Komponenten]] durch den expliziten [[Use_Case]]-Bezug.
- **Beispiel / Code:** ```java
// Beispiel für eine use-case-spezifische Komponente
public class ManageMembersComponent {
    public void addMember(Member member) { /* ... */ }
    public void removeMember(MemberId id) { /* ... */ }
    public List<Member> listMembers() { /* ... */ }
}
```
