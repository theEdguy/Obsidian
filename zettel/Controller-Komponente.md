---
id: 55d72852-1aab-4023-81fd-024e0f3deb51
title: "Controller-Komponente"
date: 2026-06-23
tags:
  - software_engineering
  - mvc
  - steuerung
  - benutzereingabe
  - draft
source: "software_engineering_kapitel_12"
---

# [[Controller-Komponente]]

- **Kernkonzept:** Die Controller-Komponente im MVC-Muster (Model-View-Controller) fungiert als Vermittler zwischen Benutzereingaben und der Anwendungslogik. Sie verarbeitet Eingaben, steuert den Ablauf der Anwendung und aktualisiert Modell und Ansicht entsprechend, ohne selbst Geschäftslogik oder Darstellung zu enthalten.
- **Nutzen & Zweck:** Die Controller-Komponente existiert, um die Trennung von Verantwortlichkeiten in Software-Systemen zu gewährleisten. Sie löst das Problem der engen Kopplung zwischen Benutzeroberfläche und Geschäftslogik, indem sie Eingaben zentral verarbeitet und an die zuständigen Komponenten weiterleitet. Dadurch wird die Wartbarkeit, Testbarkeit und Erweiterbarkeit der Anwendung verbessert, da Änderungen an der Benutzeroberfläche oder der Logik unabhängig voneinander vorgenommen werden können.
- **Abgrenzung & Grenzen:** Die Controller-Komponente sollte nicht genutzt werden, wenn die Anwendung sehr einfach ist und keine komplexe Steuerungslogik erfordert, da der Overhead der Trennung von MVC dann unnötig ist. Sie unterscheidet sich von Alternativen wie dem MVP-Muster (Model-View-Presenter) dadurch, dass der Controller im MVC direkt mit der View interagiert, während im MVP der Presenter die View steuert und diese passiv bleibt. Bei Anwendungen mit hoher Parallelität oder Echtzeitanforderungen kann ein reaktives Programmiermodell besser geeignet sein.
- **Beispiel / Code:** ```java
public class MemberController {
    private MemberManagement memberManagement;
    private StateMachine stateMachine;
    
    public void handleAddMemberRequest(MemberData memberData) {
        if (!stateMachine.getState().isSubStateOf(State.S.ManageMembers)) {
            throw new IllegalStateException("Operation nicht erlaubt im aktuellen Zustand");
        }
        memberManagement.addMember(memberData);
    }
    
    public void setMemberManagement(MemberManagement memberManagement) {
        this.memberManagement = memberManagement;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a3
- **Vorgänger / Parent:** [[MVC-Architektur]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Observer-Pattern]]
  - [[MVC-Architektur]]
