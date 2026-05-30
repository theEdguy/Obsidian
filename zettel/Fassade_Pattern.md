---
id: 824da34d-277d-4718-8c93-03aa3f82f4af
title: "Fassade_Pattern"
date: 2026-05-30
tags:
  - software_engineering
  - entwurfsmuster
  - architektur
  - draft
source: "SWE Slides (Folien 271-285)"
---

# [[Fassade_Pattern]]

- **Kernkonzept:** Das [[Fassade_Pattern]] ist ein [[Strukturmuster]], das eine vereinfachte [[Schnittstelle]] zu einem komplexen [[Subsystem]] bietet. Es kapselt die [[Komplexität]] des [[Subsystems]] und reduziert die [[Abhängigkeit|Abhängigkeiten]] zwischen [[Client|Clients]] und [[Subsystemkomponente|Subsystemkomponenten]].
- **Nutzen & Zweck:** Es löst das Problem der hohen [[Kopplung]] zwischen [[Client|Clients]] und [[Subsystemen]], indem es eine einheitliche [[Schnittstelle]] bereitstellt. Dadurch wird die [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Testbarkeit]] des [[Systems]] verbessert.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn das [[Subsystem]] einfach ist oder direkte [[Zugriff|Zugriffe]] auf [[Subsystemkomponente|Subsystemkomponenten]] erforderlich sind. Zudem kann eine [[Fassade]] zu einem [[Flaschenhals]] werden, wenn sie zu viele [[Verantwortung|Verantwortungen]] übernimmt.
- **Beispiel / Code:** ```java
public interface MemberManagement {
    void addMember(Member member);
    void removeMember(Member member);
}

public class ManagementFacade implements MemberManagement {
    private MemberManagementImpl impl;
    
    public void addMember(Member member) {
        impl.addMember(member);
    }
    
    public void removeMember(Member member) {
        impl.removeMember(member);
    }
}
```
