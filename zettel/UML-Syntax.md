---
id: 71cacf21-c2d8-4c57-b542-835bc49646e3
title: "UML-Syntax"
date: 2026-06-24
tags:
  - software_engineering
  - modellierungssprache
  - uml
  - draft
source: "software_engineering_kapitel_15"
---

# [[UML-Syntax]]

- **Kernkonzept:** UML-Syntax bezeichnet die standardisierte Notation und Regeln der Unified Modeling Language (UML), mit der objektorientierte Systeme visuell modelliert werden. Sie umfasst Diagramme wie Klassendiagramme, Sequenzdiagramme oder Use-Case-Diagramme, die Struktur und Verhalten von Software beschreiben.
- **Nutzen & Zweck:** UML-Syntax existiert, um die Kommunikation und Dokumentation in der Softwareentwicklung zu vereinheitlichen. Sie löst das Problem uneinheitlicher Darstellungen von Systemen, indem sie eine klare, visuelle Sprache für Analyse, Design und Implementierung bereitstellt. Dadurch wird die Zusammenarbeit zwischen Entwicklern, Architekten und Stakeholdern verbessert und Missverständnisse reduziert.
- **Abgrenzung & Grenzen:** UML sollte nicht genutzt werden, wenn informelle oder textuelle Beschreibungen ausreichen, da der Aufwand für die Modellierung dann unnötig hoch ist. Im Vergleich zu alternativen Modellierungssprachen wie SysML oder BPMN ist UML weniger geeignet für domänenspezifische Anwendungen außerhalb der Softwareentwicklung, z. B. für Hardware- oder Geschäftsprozessmodellierung. Zudem kann eine übermäßige Nutzung von UML-Diagrammen zu unübersichtlichen Modellen führen, die schwer wartbar sind.
- **Beispiel / Code:** ```java
// Beispiel: UML-Klassendiagramm-Notation als Java-Code-Äquivalent
public class Mitglied {
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

// Assoziation: 1:n-Beziehung in UML
public class Verein {
    private List<Mitglied> mitglieder;
    
    public void hinzufuegenMitglied(Mitglied m) {
        mitglieder.add(m);
    }
}
```
