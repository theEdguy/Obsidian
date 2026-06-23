---
id: 58bf751a-255a-462b-8b87-2f9c6afd05ff
title: "Empathy"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - paradigma
  - draft
source: "software_engineering_kapitel_03"
---

# [[Empathy]]

- **Kernkonzept:** Empathy ist ein Mechanismus der Vererbung in der objektorientierten Programmierung, bei dem ein Objekt das Verhalten eines anderen Objekts nachahmt, ohne dessen Protokoll explizit neu zu definieren. Es ermöglicht die dynamische Weiterleitung von Nachrichten an ein anderes Objekt, falls das aufgerufene Objekt selbst keine entsprechende Methode implementiert.
- **Nutzen & Zweck:** Empathy löst das Problem der Redundanz und der starren Vererbungshierarchien, indem es Objekten erlaubt, Verhalten flexibel und dynamisch von anderen Objekten zu übernehmen. Dies fördert die Wiederverwendung von Code und ermöglicht eine lose Kopplung zwischen Klassen, was die Wartbarkeit und Erweiterbarkeit von Software verbessert. Es unterstützt insbesondere Szenarien, in denen Objekte zur Laufzeit ihr Verhalten anpassen oder erweitern müssen, ohne ihre Klassendefinition zu ändern.
- **Abgrenzung & Grenzen:** Empathy sollte nicht genutzt werden, wenn eine klare und statische Vererbungshierarchie ausreicht, da der Mechanismus zusätzlichen Overhead durch die dynamische Nachrichtenweiterleitung verursacht. Im Gegensatz zur klassischen Vererbung, bei der Methoden direkt in der Subklasse definiert werden, kann Empathy zu unvorhersehbarem Verhalten führen, wenn die Weiterleitungskette nicht sorgfältig geplant ist. Zudem ist es weniger intuitiv als explizite Vererbung oder Komposition und kann die Lesbarkeit des Codes beeinträchtigen, wenn es übermäßig eingesetzt wird. Alternativen wie Delegation oder Komposition sind oft besser geeignet, wenn klare Verantwortlichkeiten und eine bessere Kontrolle über das Verhalten gewünscht sind.
- **Beispiel / Code:** ```java
// Beispiel für Empathy-ähnliches Verhalten in Java (vereinfacht)
class A {
    void methode() {
        System.out.println("Verhalten von A");
    }
}

class B {
    private A a = new A();

    void methode() {
        // Nachahmung des Verhaltens von A, falls B keine eigene Implementierung hat
        a.methode();
    }
}

public class Main {
    public static void main(String[] args) {
        B b = new B();
        b.methode(); // Gibt "Verhalten von A" aus, obwohl B keine eigene Methode definiert
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3a
- **Vorgänger / Parent:** [[Vererbung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
