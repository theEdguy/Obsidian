---
id: a95a5f3a-a6ea-401e-a5ba-f224f4127677
title: "Wert"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Wert]]

- **Kernkonzept:** Im Kontext der objektorientierten Analyse beschreibt 'Wert' ein Konzept oder Objekt der Problemdomäne, das eine quantifizierbare oder qualitative Eigenschaft darstellt, jedoch keine eigenständige Identität besitzt. Es dient als Attribut oder Datencontainer für Entitäten und wird oft durch primitive Datentypen oder einfache Wertklassen repräsentiert.
- **Nutzen & Zweck:** Das Konzept 'Wert' existiert, um zwischen eigenständigen Entitäten (mit Identität) und reinen Datenwerten zu unterscheiden. Es löst das Problem der klaren Trennung von Domänenobjekten und ihren beschreibenden Eigenschaften, was die Modellierung vereinfacht und Missverständnisse in der Analysephase vermeidet. Durch die Identifikation von Werten als separate Kategorie wird die Konsistenz des Objektmodells sichergestellt und die spätere Implementierung erleichtert.
- **Abgrenzung & Grenzen:** Das Konzept 'Wert' sollte nicht genutzt werden, wenn es sich um ein Objekt mit eigenständiger Identität oder komplexem Verhalten handelt. Es unterscheidet sich von Entitäten dadurch, dass es keine eindeutige Identität besitzt und nicht über Lebenszyklen oder Zustände verfügt. Alternativen wie Attribute oder primitive Datentypen sind oft ausreichend, wenn keine zusätzliche Logik oder Validierung benötigt wird. Zudem sollte 'Wert' nicht mit Konzepten verwechselt werden, die zwar einfach erscheinen, aber domänenspezifische Regeln oder Operationen erfordern (z. B. Geldbeträge oder Zeitstempel).
- **Beispiel / Code:** ```java
// Beispiel für eine Wertklasse (Value Object) in Java
public final class Adresse {
    private final String strasse;
    private final String plz;
    private final String ort;

    public Adresse(String strasse, String plz, String ort) {
        this.strasse = strasse;
        this.plz = plz;
        this.ort = ort;
    }

    // Getter-Methoden (keine Setter, da unveränderlich)
    public String getStrasse() { return strasse; }
    public String getPlz() { return plz; }
    public String getOrt() { return ort; }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Adresse adresse = (Adresse) o;
        return strasse.equals(adresse.strasse) && 
               plz.equals(adresse.plz) && 
               ort.equals(adresse.ort);
    }

    @Override
    public int hashCode() {
        return Objects.hash(strasse, plz, ort);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3a2
- **Vorgänger / Parent:** [[Fachkonzept]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Problemdomäne]]
  - [[Attribut]]
