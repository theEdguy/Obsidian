---
id: 6d585dd2-8959-4e54-b1af-bea54f45bad5
title: "Fassade_Pattern"
date: 2026-06-23
tags:
  - software_engineering
  - entwurfsmuster
  - architektur
  - design_pattern
  - schnittstelle
  - draft
source: "software_engineering_kapitel_12"
---

# [[Fassade_Pattern]]

- **Kernkonzept:** Das [[Fassade_Pattern]] ist ein [[Strukturmuster]], das eine vereinfachte [[Schnittstelle]] zu einem komplexen [[Subsystem]] bietet. Es kapselt die [[Komplexität]] des [[Subsystems]] und reduziert die [[Abhängigkeit|Abhängigkeiten]] zwischen [[Client|Clients]] und [[Subsystemkomponente|Subsystemkomponenten]], um die Nutzung zu erleichtern.
- **Nutzen & Zweck:** Das [[Fassade_Pattern]] existiert, um die [[Komplexität]] großer [[Softwaresystem|Softwaresysteme]] zu beherrschen, indem es die [[Kommunikation]] zwischen verschiedenen [[Komponente|Komponenten]] oder [[Subsystem|Subsystemen]] kanalisiert. Es löst das Problem der engen [[Kopplung]] zwischen [[Client|Client-Code]] und internen [[Systemdetail|Systemdetails]], indem es eine klare, einheitliche [[Schnittstelle]] anbietet. Dadurch werden die [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Testbarkeit]] verbessert, die [[Fehleranfälligkeit]] verringert und die Integration neuer [[Komponente|Komponenten]] erleichtert. Zudem überwacht die [[Fassade]] [[Zugriff|Zugriffe]] auf das [[Subsystem]], beispielsweise durch [[Zustandsprüfung|Zustandsprüfungen]] oder [[Nebenläufigkeitskontrolle|Nebenläufigkeitskontrollen]].
- **Abgrenzung & Grenzen:** Das [[Fassade_Pattern]] sollte nicht genutzt werden, wenn das [[Subsystem]] einfach strukturiert ist und keine komplexen [[Interaktion|Interaktionen]] zwischen [[Komponente|Komponenten]] erforderlich sind, da der zusätzliche [[Abstraktionslayer]] dann unnötigen [[Overhead]] erzeugt. Es unterscheidet sich von Alternativen wie dem [[Adapter_Pattern]], das bestehende [[Schnittstelle|Schnittstellen]] anpasst, oder dem [[Mediator_Pattern]], das die [[Kommunikation]] zwischen [[Objekt|Objekten]] zentralisiert. Im Gegensatz zu diesen [[Entwurfsmuster|Mustern]] dient die [[Fassade]] primär der Vereinfachung und [[Kapselung]], nicht der Anpassung oder Vermittlung zwischen gleichrangigen [[Komponente|Komponenten]]. Zudem kann eine [[Fassade]] zu einem [[Flaschenhals]] werden, wenn sie zu viele [[Verantwortung|Verantwortungen]] übernimmt oder direkte [[Zugriff|Zugriffe]] auf [[Subsystemkomponente|Subsystemkomponenten]] erforderlich sind.
- **Beispiel / Code:** ```java
// Beispiel 1: Einfache Fassade zur Kapselung eines Subsystems
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

// Beispiel 2: Fassade mit Zustandsprüfung und Nebenläufigkeitskontrolle
class ManagementFacade implements MemberManagement {
    private StateMachine stateMachine;
    private ManageMembers manager = new ManageMembers();

    public synchronized void manageMembers(Token token) {
        if (!this.stateMachine.getState().isSubStateOf(State.S.Initialized)) {
            return; // Zugriff nur im richtigen Zustand erlaubt
        }
        this.manager.manageMembers(token); // Delegation an Subsystem
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Fassaden-Interface]]
  - [[Fassaden-Implementierung]]
  - [[Schnittstellenverwaltung]]
- **Querverweise:**
  - [[Design_Patterns]]
  - [[Software-Architektur]]
