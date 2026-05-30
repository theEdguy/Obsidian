---
id: e1c97dff-e255-479c-9a5d-c18ced32ea90
title: "MVC_Architektur"
date: 2026-05-30
tags:
  - software_engineering
  - architekturmuster
  - software_architektur
  - design_pattern
  - draft
source: "SWE Slides (Folien 256-270)"
---

# [[MVC_Architektur]]

- **Kernkonzept:** Die [[MVC_Architektur]] (Model-View-Controller) ist ein [[Architekturmuster]], das die Trennung von [[Datenmodell]], [[Präsentation]] und [[Benutzerinteraktion]] in drei [[Komponente|Komponenten]] vorsieht: [[Model]], [[View]] und [[Controller]].
- **Nutzen & Zweck:** Sie fördert die [[Modularität]] und [[Wartbarkeit]] von [[Anwendung|Anwendungen]], indem sie die Verantwortlichkeiten klar trennt. Das [[Model]] verwaltet die [[Daten]] und [[Geschäftslogik]], die [[View]] die [[Präsentation]], und der [[Controller]] die [[Benutzerinteraktion]].
- **Abgrenzung & Grenzen:** Nicht geeignet für sehr einfache [[Anwendung|Anwendungen]], bei denen die Trennung von [[Model]], [[View]] und [[Controller]] zu Overhead führt. Alternativen sind [[MVP_Architektur]] oder [[MVVM_Architektur]].
- **Beispiel / Code:** ```java
// Model
public class MemberModel {
    private List<Member> members;
    
    public List<Member> getMembers() {
        return members;
    }
    
    public void addMember(Member member) {
        members.add(member);
    }
}

// View
public class MemberView {
    public void displayMembers(List<Member> members) {
        for (Member member : members) {
            System.out.println(member);
        }
    }
}

// Controller
public class MemberController {
    private MemberModel model;
    private MemberView view;
    
    public void updateView() {
        view.displayMembers(model.getMembers());
    }
}
```
