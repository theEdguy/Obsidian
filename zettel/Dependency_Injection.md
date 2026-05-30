---
id: f520ac12-41a0-424f-ac85-78c1cafbe352
title: "Dependency_Injection"
date: 2026-05-30
tags:
  - software_engineering
  - entwurfsmuster
  - software_architektur
  - dependency_management
  - draft
source: "SWE Slides (Folien 286-300)"
---

# [[Dependency_Injection]]

- **Kernkonzept:** [[Dependency_Injection]] ist ein [[Entwurfsmuster|Muster]], bei dem die [[Abhängigkeit|Abhängigkeiten]] einer [[Klasse]] von außen injiziert werden, anstatt sie selbst zu erzeugen.
- **Nutzen & Zweck:** Es fördert die [[Lose_Kopplung|lose Kopplung]] und [[Testbarkeit]] von [[Klasse|Klassen]], indem [[Abhängigkeit|Abhängigkeiten]] austauschbar und [[Mock|mockbar]] werden.
- **Abgrenzung & Grenzen:** Nicht geeignet für einfache [[Anwendung|Anwendungen]], in denen die [[Komplexität]] von [[Dependency_Injection]]-Frameworks überflüssig ist. Unterscheidet sich von [[Service_Locator]], bei dem [[Klasse|Klassen]] ihre [[Abhängigkeit|Abhängigkeiten]] selbst anfordern.
- **Beispiel / Code:** ```java
@Component
@ApplicationScope
class ManagementFacade implements MemberManagement {
    @Autowired
    private StateMachine stateMachine;
    
    // ...
}
```
