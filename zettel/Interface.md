---
id: 908ce232-2931-493d-873b-c92a514fb520
title: "Interface"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - uml
  - draft
source: "software_engineering_kapitel_04"
---

# [[Interface]]

- **Kernkonzept:** Ein Interface in der objektorientierten Programmierung und UML ist ein Modellelement, das die externe Sichtbarkeit von Operationen einer Klasse definiert, ohne deren interne Struktur oder Implementierung festzulegen. Es spezifiziert einen Vertrag, den implementierende Klassen erfüllen müssen, und ermöglicht so die Trennung von Schnittstelle und Implementierung.
- **Nutzen & Zweck:** Interfaces existieren, um die lose Kopplung zwischen Softwarekomponenten zu fördern und die Austauschbarkeit von Implementierungen zu ermöglichen. Sie lösen das Problem der Abhängigkeit von konkreten Klassen, indem sie eine standardisierte Schnittstelle bereitstellen, die von verschiedenen Klassen implementiert werden kann. Dadurch wird Polymorphismus unterstützt, und Systeme lassen sich flexibler erweitern oder anpassen, ohne bestehende Abhängigkeiten zu brechen.
- **Abgrenzung & Grenzen:** Interfaces sollten nicht genutzt werden, wenn eine konkrete Implementierung mit Attributen oder Zuständen erforderlich ist, da Interfaces keine Attribute oder Assoziationen zu anderen Klassen besitzen sollten. Im Gegensatz zu abstrakten Klassen, die sowohl Schnittstellen als auch teilweise Implementierungen definieren können, sind Interfaces rein deklarativ. Zudem sind sie ungeeignet, wenn eine enge Kopplung zwischen Komponenten gewünscht oder unvermeidbar ist, da sie explizit auf Entkopplung abzielen.
- **Beispiel / Code:** ```java
// Definition eines Interfaces in Java
public interface Leistungsbewertung {
    int berechnePunkte();
    void aktualisiereLeistung(int neuePunkte);
}

// Implementierung des Interfaces durch eine Klasse
public class Mitglied implements Leistungsbewertung {
    private int leistung;
    
    @Override
    public int berechnePunkte() {
        return this.leistung;
    }
    
    @Override
    public void aktualisiereLeistung(int neuePunkte) {
        this.leistung = neuePunkte;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Abstrakte_Klasse]]
  - [[Vererbung]]
