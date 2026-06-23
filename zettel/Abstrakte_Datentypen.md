---
id: ec7720cd-1453-43e0-837b-6f670e76e872
title: "Abstrakte Datentypen"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - programmierung
  - draft
source: "software_engineering_kapitel_03"
---

# [[Abstrakte Datentypen]]

- **Kernkonzept:** Abstrakte Datentypen (ADTs) sind ein Konzept der Objektorientierung, bei dem Datenstrukturen zusammen mit den darauf definierten Operationen gekapselt werden. Der interne Zustand eines Objekts ist verborgen und kann nur über eine festgelegte Schnittstelle manipuliert werden.
- **Nutzen & Zweck:** Abstrakte Datentypen lösen das Problem der unkontrollierten Datenmanipulation, indem sie die Implementierungsdetails verbergen und eine klare, konsistente Schnittstelle bereitstellen. Dadurch wird die Wartbarkeit, Sicherheit und Wiederverwendbarkeit von Code verbessert, da Änderungen an der internen Struktur keine Auswirkungen auf den nutzenden Code haben. Zudem fördern sie eine klare Trennung zwischen Interface und Implementierung, was die Modularität von Software erhöht.
- **Abgrenzung & Grenzen:** Abstrakte Datentypen sollten nicht genutzt werden, wenn eine direkte, performanzkritische Manipulation von Daten erforderlich ist, da die Kapselung zusätzlichen Overhead verursachen kann. Im Gegensatz zu prozeduralen Ansätzen, bei denen Daten und Funktionen getrennt sind, erfordern ADTs eine stärkere Abstraktion, was in einfachen oder hochoptimierten Systemen unnötig komplex sein kann. Zudem sind sie weniger geeignet, wenn die Datenstruktur dynamisch und flexibel ohne feste Schnittstelle sein muss, wie z. B. in Skriptsprachen oder bei explorativer Programmierung.
- **Beispiel / Code:** ```java
// Beispiel für einen abstrakten Datentyp in Java: Eine Klasse 'Rectangle' mit gekapselten Attributen
// und einer definierten Schnittstelle.
public class Rectangle {
    private double width;
    private double height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    // Öffentliche Methode zur Berechnung der Fläche (Schnittstelle)
    public double calculateArea() {
        return width * height;
    }

    // Öffentliche Methode zum Ändern der Dimensionen (Schnittstelle)
    public void resize(double newWidth, double newHeight) {
        this.width = newWidth;
        this.height = newHeight;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2c
- **Vorgänger / Parent:** [[Säulen_der_Objektorientierung]]
- **Folgezettel / Unterzettel:**
  - [[Eiffel]]
  - [[Bertrand_Meyer]]
- **Querverweise:** keine
