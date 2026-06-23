---
id: e582d04d-4a66-428a-b63e-61b1e4e99ecb
title: "Hohe Kohäsion"
date: 2026-06-23
tags:
  - software_engineering
  - designprinzip
  - architektur
  - draft
source: "software_engineering_kapitel_13"
---

# [[Hohe Kohäsion]]

- **Kernkonzept:** Hohe Kohäsion ist ein Designprinzip in der Softwareentwicklung, das besagt, dass die Verantwortlichkeiten einer Klasse oder Komponente eng miteinander verwandt und auf einen klar definierten Zweck fokussiert sein sollen. Eine Klasse mit hoher Kohäsion erfüllt eine spezifische Aufgabe und enthält nur die dafür notwendigen Methoden und Attribute.
- **Nutzen & Zweck:** Das Prinzip der hohen Kohäsion existiert, um die Wartbarkeit, Verständlichkeit und Wiederverwendbarkeit von Software zu verbessern. Es löst das Problem, dass Klassen mit zu vielen unterschiedlichen Verantwortlichkeiten schwer zu pflegen, zu testen und zu erweitern sind. Durch die Konzentration auf einen klaren Zweck wird die Komplexität reduziert, und Änderungen an einer Klasse haben weniger unerwartete Auswirkungen auf andere Teile des Systems.
- **Abgrenzung & Grenzen:** Hohe Kohäsion sollte nicht angewendet werden, wenn dadurch eine übermäßige Fragmentierung des Codes entsteht, die die Lesbarkeit oder Performance beeinträchtigt. Es unterscheidet sich von loser Kopplung, die die Abhängigkeiten zwischen Klassen minimiert, während hohe Kohäsion die innere Struktur einer Klasse optimiert. In Fällen, in denen eine Klasse mehrere eng verwandte Aufgaben übernimmt (z. B. Utility-Klassen), kann eine moderate Kohäsion akzeptabel sein, solange die Verantwortlichkeiten logisch gruppiert sind.
- **Beispiel / Code:** ```java
// Beispiel für hohe Kohäsion: Eine Klasse mit klar abgegrenztem Zweck
public class MitgliedVerwaltung {
    private List<Mitglied> mitglieder;

    public void mitgliedHinzufuegen(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }

    public void mitgliedEntfernen(Mitglied mitglied) {
        mitglieder.remove(mitglied);
    }

    public Mitglied mitgliedSuchen(String name) {
        return mitglieder.stream()
                .filter(m -> m.getName().equals(name))
                .findFirst()
                .orElse(null);
    }
}

// Beispiel für niedrige Kohäsion: Eine Klasse mit zu vielen unterschiedlichen Verantwortlichkeiten
public class MitgliedUndZahlungVerwaltung {
    private List<Mitglied> mitglieder;
    private List<Zahlung> zahlungen;

    public void mitgliedHinzufuegen(Mitglied mitglied) { /* ... */ }
    public void zahlungBuchen(Zahlung zahlung) { /* ... */ }
    public void berichtGenerieren() { /* ... */ }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a4
- **Vorgänger / Parent:** [[Objektorientierte_Analyse_und_Design]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
