---
id: dcacf665-de9c-478a-8e85-495069615b37
title: "Objektidentität"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - datenmodellierung
  - programmierung
  - draft
source: "software_engineering_kapitel_03"
---

# [[Objektidentität]]

- **Kernkonzept:** [[Objektidentität]] bezeichnet das Prinzip, dass jedes [[Objekt]] in der [[Objektorientierte_Programmierung|objektorientierten Programmierung]] eine eindeutige, unveränderliche [[Identität]] besitzt, die unabhängig von seinen [[Attribut|Attributwerten]] existiert. Zwei [[Objekt|Objekte]] können identische [[Attribut|Attributwerte]] haben, bleiben aber dennoch eigenständige [[Entität|Entitäten]] mit unterschiedlichen [[Identität|Identitäten]].
- **Nutzen & Zweck:** [[Objektidentität]] löst das Problem der eindeutigen [[Referenzierung]] und [[Vergleichbarkeit]] von [[Objekt|Objekten]], selbst wenn diese inhaltlich gleich sind. Sie ermöglicht es, [[Objekt|Objekte]] in [[Datenstruktur|Datenstrukturen]] wie [[Liste|Listen]] oder [[Menge|Mengen]] zu verwalten, ohne dass deren [[Gleichheit]] zu Verwechslungen führt. Zudem ist sie essenziell für die korrekte Implementierung von [[Beziehung|Beziehungen]] zwischen [[Objekt|Objekten]], z. B. in [[Graph|Graphen]] oder bei der Modellierung von [[Assoziation|Assoziationen]]. In [[Verteilte_Systeme|verteilten Systemen]] und bei [[Datenbank]]-Anbindungen stellt sie sicher, dass [[Objekt|Objekte]] konsistent referenziert und unterschieden werden können.
- **Abgrenzung & Grenzen:** [[Objektidentität]] sollte nicht genutzt werden, wenn lediglich der inhaltliche Vergleich von [[Objekt|Objekten]] relevant ist, z. B. bei der Prüfung auf [[Gleichheit]] von Werten. In solchen Fällen ist ein expliziter Vergleich der [[Attribut|Attribute]] (z. B. mittels `equals()` in Java) vorzuziehen. In der [[Funktionale_Programmierung|funktionalen Programmierung]] ist [[Objektidentität]] nicht relevant, da [[Objekt|Objekte]] dort unveränderlich sind und stattdessen strukturelle [[Gleichheit]] im Vordergrund steht. Alternativen wie [[Wertetyp|Wertetypen]] (z. B. primitive [[Datentyp|Datentypen]] oder [[Immutable-Objekt|Immutable-Objekte]]) verzichten bewusst auf [[Identität]] und setzen auf strukturelle [[Gleichheit]]. [[Objektidentität]] kann zudem zu [[Performance]]-Problemen führen, wenn [[Identität|Identitätsvergleiche]] häufig durchgeführt werden, z. B. in [[Schleifen]]. Ein weiterer Nachteil ist das Risiko unerwarteten Verhaltens, wenn [[Objekt|Objekte]] versehentlich als [[Referenz|Referenzen]] statt als Werte behandelt werden.
- **Beispiel / Code:** ```java
// Beispiel 1: Grundlegende Objektidentität
String text1 = new String("Hallo");
String text2 = new String("Hallo");
String text3 = text1;

// Vergleich der Identität (Referenzgleichheit)
System.out.println(text1 == text2);      // false (unterschiedliche Objekte)
System.out.println(text1 == text3);      // true (gleiche Referenz)

// Vergleich der Gleichheit (Attributwerte)
System.out.println(text1.equals(text2)); // true (gleicher Inhalt)

// Beispiel 2: Objektidentität in Datenstrukturen
import java.util.HashSet;
import java.util.Set;

class Person {
    private String name;
    
    public Person(String name) {
        this.name = name;
    }
    
    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Person person = (Person) obj;
        return name.equals(person.name);
    }
    
    @Override
    public int hashCode() {
        return name.hashCode();
    }
}

public class Main {
    public static void main(String[] args) {
        Set<Person> people = new HashSet<>();
        Person p1 = new Person("Alice");
        Person p2 = new Person("Alice");
        Person p3 = p1;
        
        people.add(p1);
        people.add(p2);
        people.add(p3);
        
        System.out.println(people.size()); // 2 (p1 und p2 sind unterschiedliche Objekte, p3 ist eine Referenz auf p1)
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1b1
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
