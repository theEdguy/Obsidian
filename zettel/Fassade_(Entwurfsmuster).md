---
id: 1c61365b-9c27-44c0-946a-a316f18c28e5
title: "Fassade_(Entwurfsmuster)"
date: 2026-05-30
tags:
  - software_engineering
  - entwurfsmuster
  - software_architektur
  - design_pattern
  - draft
source: "SWE Slides (Folien 286-300)"
---

# [[Fassade_(Entwurfsmuster)]]

- **Kernkonzept:** Die [[Fassade_(Entwurfsmuster)|Fassade]] ist ein [[Strukturmuster|Strukturmuster]], das eine vereinfachte [[Schnittstelle]] zu einem komplexen [[Subsystem|Subsystem]] bietet. Sie kapselt die Interaktion mit mehreren [[Klasse|Klassen]] hinter einer einzigen [[Schnittstelle]].
- **Nutzen & Zweck:** Sie reduziert die [[Komplexität]] für [[Client|Clients]], indem sie die direkte Abhängigkeit von vielen [[Klasse|Klassen]] eines [[Subsystem|Subsystems]] vermeidet und fördert die [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn das [[Subsystem]] einfach ist oder wenn [[Client|Clients]] direkten Zugriff auf spezifische [[Funktionalität|Funktionalitäten]] benötigen. Unterscheidet sich von [[Adapter_(Entwurfsmuster)|Adaptern]], die [[Schnittstelle|Schnittstellen]] anpassen, während [[Fassade_(Entwurfsmuster)|Fassaden]] diese vereinfachen.
- **Beispiel / Code:** ```java
class ManagementFacade implements MemberManagement {
    private StateMachine stateMachine;
    private ManageMembers manager = new ManageMembers(...);

    public synchronized void manageMembers(Token token) {
        if (!this.stateMachine.getState().isSubStateOf(State.S.Initialized)) {
            return;
        }
        this.manager.manageMembers(token);
    }
}
```
