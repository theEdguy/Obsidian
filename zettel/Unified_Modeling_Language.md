---
id: dcf504a7-88ea-492a-b9be-eeeca39a94c5
title: "Unified Modeling Language"
date: 2026-06-23
tags:
  - software_engineering
  - modeling
  - language
  - draft
source: "software_engineering_kapitel_11"
---

# [[Unified Modeling Language]]

- **Kernkonzept:** Die Unified Modeling Language (UML) ist eine standardisierte Modellierungssprache zur Spezifikation, Visualisierung, Konstruktion und Dokumentation von Software-Systemen, insbesondere im objektorientierten Bereich. Sie bietet verschiedene Diagrammtypen, um strukturelle und verhaltensbezogene Aspekte eines Systems einheitlich darzustellen.
- **Nutzen & Zweck:** UML existiert, um die Kommunikation zwischen Entwicklern, Architekten und Stakeholdern zu vereinfachen und Missverständnisse in der Softwareentwicklung zu reduzieren. Sie löst das Problem der uneinheitlichen Darstellung von Systemen, indem sie eine gemeinsame Sprache für die Modellierung bereitstellt. Dadurch wird die Analyse, das Design und die Dokumentation komplexer Systeme strukturierter, nachvollziehbarer und weniger fehleranfällig.
- **Abgrenzung & Grenzen:** UML sollte nicht genutzt werden, wenn es um die direkte Implementierung oder detaillierte Code-Generierung geht, da es sich primär um eine Modellierungssprache handelt und keine vollständige Abbildung des Systems im Quellcode liefert. Alternativen wie domänenspezifische Sprachen (DSLs) oder textuelle Spezifikationen können in bestimmten Kontexten effizienter sein, insbesondere wenn es um sehr spezifische oder nicht-objektorientierte Systeme geht. Zudem ist UML weniger geeignet für agile Projekte mit stark iterativem Charakter, bei denen formale Dokumentation zugunsten schneller Anpassungen in den Hintergrund tritt.
- **Beispiel / Code:** ```java
// Beispiel: UML-Klassendiagramm als Java-Code-Äquivalent
class Mitglied {
    private String name;
    private int mitgliedsnummer;
    
    public Mitglied(String name, int mitgliedsnummer) {
        this.name = name;
        this.mitgliedsnummer = mitgliedsnummer;
    }
    
    public void aktualisiereDaten(String neuerName) {
        this.name = neuerName;
    }
}

class Vereinsverwaltung {
    private List<Mitglied> mitglieder;
    
    public void hinzufuegenMitglied(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }
}
```

// Das obige Beispiel entspricht einem UML-Klassendiagramm mit:
// - Klassen "Mitglied" und "Vereinsverwaltung"
// - Attributen (name, mitgliedsnummer, mitglieder)
// - Methoden (aktualisiereDaten, hinzufuegenMitglied)
// - Assoziation zwischen Vereinsverwaltung und Mitglied (1..*).

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 6
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Klassendiagramme]]
  - [[Use-Case-Diagramme]]
  - [[Sequenzdiagramme]]
- **Querverweise:**
  - [[Software-Modellierung]]
  - [[OMG-Standards]]
