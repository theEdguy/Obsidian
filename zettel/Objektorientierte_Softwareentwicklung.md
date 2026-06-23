---
id: 6bc816c9-aeda-4119-a472-3ee7ddba972a
title: "Objektorientierte Softwareentwicklung"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - draft
source: "software_engineering_kapitel_03"
---

# [[Objektorientierte Softwareentwicklung]]

- **Kernkonzept:** Objektorientierte Softwareentwicklung ist ein durchgängiger Entwicklungsansatz, der reale oder abstrakte Entitäten als Objekte mit Eigenschaften (Attribute) und Verhalten (Operationen) modelliert. Diese Objekte werden in Klassen organisiert, die Struktur und Verhalten gleichartiger Objekte definieren und durch Mechanismen wie Vererbung, Polymorphie und Kapselung wiederverwendbar und erweiterbar gemacht werden.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der Komplexitätsbewältigung in der Softwareentwicklung, indem es eine natürliche Abbildung der realen Welt in den Code ermöglicht. Es fördert die Wiederverwendbarkeit, Wartbarkeit und Skalierbarkeit von Software durch klare Strukturierung, Modularität und methodische Durchgängigkeit von der Analyse bis zur Implementierung. Zudem verbessert es die Kommunikation zwischen Entwicklern und Anwendern durch intuitive Modellierung und Simulation von Problemdomänen.
- **Abgrenzung & Grenzen:** Objektorientierte Softwareentwicklung sollte nicht genutzt werden, wenn die Problemdomäne stark prozedural oder funktional geprägt ist, z. B. bei mathematischen Algorithmen oder datenstromorientierten Anwendungen, wo funktionale Programmierung effizienter sein kann. Alternativen wie prozedurale Programmierung eignen sich besser für kleine, lineare Aufgaben ohne komplexe Datenstrukturen. Zudem kann der Overhead durch Objektverwaltung bei performancekritischen Systemen (z. B. Echtzeitsysteme) nachteilig sein. Im Vergleich zu komponentenbasierten Ansätzen fehlt有时 eine klare Trennung von technischen und fachlichen Aspekten.
- **Beispiel / Code:** ```java
// Definition einer Klasse 'Mitglied' mit Attributen und einer Operation
class Mitglied {
    private String name;
    private String adresse;
    private int alter;
    private int leistungspunkte;

    // Konstruktor
    public Mitglied(String name, String adresse, int alter) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
        this.leistungspunkte = 0;
    }

    // Operation zur Leistungsprognose
    public int leistungsprognose(int tage) {
        return this.leistungspunkte + (tage * 10); // Beispielberechnung
    }

    // Getter-Methode
    public String getName() {
        return name;
    }
}

// Nutzung der Klasse
public class Main {
    public static void main(String[] args) {
        Mitglied mitglied = new Mitglied("Max Mustermann", "Musterstraße 1", 30);
        System.out.println(mitglied.getName() + " hat eine prognostizierte Leistung von: " +
                          mitglied.leistungsprognose(7) + " Punkten.");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Agile_Softwareentwicklung]]
  - [[Iterative_Entwicklung]]
  - [[Architekturorientierte_Entwicklung]]
  - [[Objektorientierung_als_durchgängiges_Stilmittel]]
- **Querverweise:** keine
