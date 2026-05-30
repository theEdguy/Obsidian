---
id: 8fb4bbc8-602d-498e-b02b-e6363d78f663
title: "Erzeugungsmuster"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - erzeugungsmuster
  - software_architecture
  - oop
  - draft
source: "SWE Slides (Folien 331-345)"
---

# [[Erzeugungsmuster]]

- **Kernkonzept:** Eine [[Kategorie]] von [[Entwurfsmuster|Entwurfsmustern]], die sich mit der [[Erzeugung|Erstellung]] von [[Objekt|Objekten]] befassen, um [[Flexibilität]] und [[Wiederverwendbarkeit]] zu erhöhen. [[Erzeugungsmuster]] kapseln den [[Erstellungsprozess]] und machen ein [[System]] unabhängig davon, wie [[Objekt|Objekte]] konkret instanziiert werden, wodurch die Konzentration auf die [[Schnittstelle]] ermöglicht wird.
- **Nutzen & Zweck:** Der primäre [[Nutzen]] von [[Erzeugungsmuster|Erzeugungsmustern]] liegt in der Kapselung der [[Objekterzeugung]], um [[Abhängigkeit|Abhängigkeiten]] zu reduzieren und die [[Erweiterbarkeit]] des [[Systems]] zu verbessern. Sie lösen das [[Problem]] der starren [[Abhängigkeit]] von konkreten [[Klasse|Klassen]] und fördern [[Polymorphie]] bei der [[Objekterzeugung]]. Dadurch wird die [[Wiederverwendbarkeit]] im [[Design]] erhöht und die [[Kopplung]] verringert, was zu einer flexibleren und wartbareren [[Softwarearchitektur]] führt.
- **Abgrenzung & Grenzen:** [[Erzeugungsmuster]] sind nicht universell einsetzbar: Sie können zu [[Überkomplexität]] führen, wenn die [[Objekterzeugung]] trivial ist oder keine [[Variabilität]] in der Erstellung benötigt wird. Im Vergleich zu direkten [[Konstruktor|Konstruktoren]] erhöhen sie die [[Komplexität]] des [[Codes]] und erfordern zusätzlichen [[Boilerplate-Code]]. Alternativen wie [[Dependency_Injection]] oder [[Refactoring]]-Techniken können ähnliche Ziele mit weniger Aufwand erreichen. Zudem sind nicht alle [[Muster]] in jeder [[Programmiersprache]] gleich gut umsetzbar, insbesondere in Sprachen mit eingeschränkter [[Objektorientierung]] oder dynamischer [[Typisierung]].
- **Beispiel / Code:** ```java
// Beispiel für [[Factory_Method]] (ein [[Erzeugungsmuster]])
interface Fahrzeug {
    void fahren();
}

class Auto implements Fahrzeug {
    @Override
    public void fahren() {
        System.out.println("Auto fährt");
    }
}

class FahrzeugFactory {
    Fahrzeug erstellen(String typ) {
        if (typ.equals("Auto")) {
            return new Auto();
        }
        throw new IllegalArgumentException("Unbekannter Fahrzeugtyp");
    }
}

// Beispiel für [[Singleton]] (ein weiteres [[Erzeugungsmuster]])
public interface Component {
    Component COMPONENT = ComponentImpl.mkComponent();
}

public class ComponentImpl implements Component {
    private static ComponentImpl comp = null;

    protected ComponentImpl() { }

    public static Component mkComponent() {
        if (ComponentImpl.comp == null)
            ComponentImpl.comp = new ComponentImpl();
        return ComponentImpl.comp;
    }
}
```
