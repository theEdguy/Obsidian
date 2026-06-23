---
id: e2e1c6e5-1768-41e6-a4d6-c95cd86dfff6
title: "Sharing"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - paradigma
  - draft
source: "software_engineering_kapitel_03"
---

# [[Sharing]]

- **Kernkonzept:** Sharing bezeichnet in der Objektorientierung das Prinzip, dass Objekte gemeinsame Eigenschaften und Verhaltensweisen teilen, um Redundanzen zu vermeiden und eine effiziente Wiederverwendung von Code zu ermöglichen. Dies erfolgt durch Mechanismen wie Vererbung oder Delegation, wobei der Zugriff auf gemeinsame Ressourcen über Konzepte wie 'super' und 'self' gesteuert wird.
- **Nutzen & Zweck:** Sharing löst das Problem der Code-Duplikation und fördert die Wartbarkeit sowie Erweiterbarkeit von Software. Durch die gemeinsame Nutzung von Eigenschaften und Methoden in einer Klassenhierarchie wird die Konsistenz des Systems verbessert, und Änderungen müssen nur an einer zentralen Stelle vorgenommen werden. Dies reduziert Fehlerquellen und beschleunigt die Entwicklung, insbesondere bei komplexen Systemen mit vielen ähnlichen Objekten.
- **Abgrenzung & Grenzen:** Sharing sollte nicht genutzt werden, wenn Objekte stark unterschiedliche Verantwortlichkeiten oder unabhängige Lebenszyklen haben, da dies zu unnötiger Kopplung oder unklaren Abhängigkeiten führen kann. Alternativen wie Komposition oder Interfaces sind vorzuziehen, wenn Flexibilität und lose Kopplung im Vordergrund stehen. Zudem kann übermäßiges Sharing die Verständlichkeit des Codes beeinträchtigen, insbesondere wenn tiefe Vererbungshierarchien entstehen (sogenanntes 'Fragile Base Class Problem').
- **Beispiel / Code:** ```java
// Beispiel für Sharing durch Vererbung in Java
class Tier {
    protected String name;
    
    public Tier(String name) {
        this.name = name;
    }
    
    public void essen() {
        System.out.println(name + " isst.");
    }
}

class Hund extends Tier {
    public Hund(String name) {
        super(name); // Zugriff auf gemeinsame Eigenschaft via 'super'
    }
    
    public void bellen() {
        System.out.println(name + " bellt.");
    }
}

public class Main {
    public static void main(String[] args) {
        Hund meinHund = new Hund("Bello");
        meinHund.essen(); // Geerbte Methode von Tier
        meinHund.bellen(); // Eigene Methode von Hund
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2b
- **Vorgänger / Parent:** [[Säulen_der_Objektorientierung]]
- **Folgezettel / Unterzettel:**
  - [[Smalltalk-80]]
  - [[super]]
  - [[self]]
- **Querverweise:** keine
