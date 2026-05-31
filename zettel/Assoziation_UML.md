---
aliases:
- Assoziation_(UML)
date: 2026-05-30
id: ed5743a6-a916-4ab7-9d06-6bf82389054a
source: Klausur_Referenz
tags:
- software_engineering
- uml
- objektorientierter_entwurf
- modellierung
- klassendiagramm
- softwarearchitektur
- draft
title: Assoziation_UML
---

# [[Assoziation_UML]]

- **Kernkonzept:** Eine [[Assoziation_UML]] ist eine strukturelle Beziehung in der [[UML]] (Unified Modeling Language), die beschreibt, wie Instanzen von [[Klasse|Klassen]] miteinander in Verbindung stehen und kommunizieren können. Sie modelliert eine semantische Verbindung zwischen Objekten, die über einen bestimmten Zeitraum besteht. Assoziationen können unidirektional oder bidirektional sein, mit Multiplizitäten (z. B. 1, 0..*, 1..5) versehen werden und optional Namen, Rollen oder Attribute tragen. Sie sind ein zentrales Element in [[Klassendiagramm|Klassendiagrammen]] und ermöglichen die Abbildung von Beziehungen wie "hat-ein" oder "kennt-ein" in der objektorientierten Analyse und Design.
- **Nutzen & Zweck:** Assoziationen dienen dazu, die statische Struktur eines Systems zu modellieren und die Zusammenarbeit zwischen Objekten zu definieren. Sie ermöglichen:

1. **Klare Kommunikation**: Durch die Visualisierung von Beziehungen wird die Zusammenarbeit zwischen Entwicklern, Architekten und Stakeholdern verbessert.
2. **Flexibilität im Design**: Assoziationen erlauben die Abbildung komplexer Beziehungen (z. B. [[n-stellige_Assoziation]]) und unterstützen die Trennung von Verantwortlichkeiten ([[Single_Responsibility_Principle]]).
3. **Wiederverwendbarkeit**: Durch die Modellierung von Assoziationen können Komponenten unabhängig voneinander entwickelt und später verknüpft werden (z. B. in [[Komponentenbasierte_Entwicklung]]).
4. **Dokumentation**: Sie dienen als Grundlage für die Generierung von Code (z. B. via [[Forward_Engineering]]) oder die Erstellung von Datenbankschemata.
5. **Analyse von Abhängigkeiten**: Assoziationen helfen, zyklische Abhängigkeiten ([[Zyklomatische_Komplexität]]) oder unerwünschte Kopplungen ([[Lose_Kopplung]]) frühzeitig zu erkennen.
- **Abgrenzung & Grenzen:** Assoziationen sind abzugrenzen von anderen UML-Beziehungen:

- **[[Vererbung_UML]] (Generalisierung)**: Beschreibt eine "ist-ein"-Beziehung (z. B. ein `Student` ist eine `Person`), während Assoziationen "hat-ein" oder "kennt-ein" modellieren.
- **[[Abhängigkeit_UML]]**: Eine lose Beziehung, die keine strukturelle Verbindung darstellt (z. B. ein Parameter in einer Methode). Assoziationen sind dagegen dauerhafte Beziehungen.
- **[[Aggregation_UML]] und [[Komposition_UML]]**: Spezialformen von Assoziationen mit zusätzlicher Semantik (Teil-Ganzes-Beziehung). Eine Aggregation impliziert eine schwache Bindung (z. B. ein `Team` hat `Mitglieder`), während eine Komposition eine starke Bindung mit Lebenszeitabhängigkeit beschreibt (z. B. ein `Auto` hat `Räder`).

**Stolpersteine**:
- **Übermodellierung**: Zu viele Assoziationen können ein [[Klassendiagramm]] unübersichtlich machen. Es gilt, nur relevante Beziehungen zu modellieren.
- **Falsche Multiplizitäten**: Unklare Multiplizitäten (z. B. `0..*` vs. `1..*`) können zu Implementierungsfehlern führen.
- **Gerichtete vs. ungerichtete Assoziationen**: Eine ungerichtete Assoziation impliziert bidirektionale Navigation, was in der Implementierung zu höherer Kopplung führen kann.
- **Rekursive Assoziationen**: Assoziationen einer Klasse mit sich selbst (z. B. `Mitarbeiter` leitet `Mitarbeiter`) erfordern klare Rollenbezeichnungen, um Missverständnisse zu vermeiden.
- **N-stellige Assoziationen**: Assoziationen mit mehr als zwei beteiligten Klassen sind schwer zu implementieren und sollten nach Möglichkeit in binäre Assoziationen zerlegt werden.
- **Beispiel / Code:** {'uml_beschreibung': '```mermaid\nclassDiagram\n    class Verein {\n        -name: String\n        +getMitglieder(): List~Mitglied~\n    }\n    \n    class Mitglied {\n        -name: String\n        -mitgliedsNr: int\n        +getVereine(): List~Verein~\n    }\n    \n    Verein "1" -- "*" Mitglied : aktiv-bei\n    note for Verein "Assoziation mit Multiplizität: Ein Verein hat 0..* Mitglieder"\n    note for Mitglied "Assoziation mit Attribut: Mitgliedsnummer ist Teil der Beziehung"\n```', 'java_implementation': '// Beispiel für eine bidirektionale Assoziation mit Multiplizität\nimport java.util.ArrayList;\nimport java.util.List;\n\nclass Verein {\n    private String name;\n    private List<Mitglied> mitglieder = new ArrayList<>();\n    \n    public void addMitglied(Mitglied mitglied) {\n        mitglieder.add(mitglied);\n        mitglied.addVerein(this);\n    }\n    \n    public List<Mitglied> getMitglieder() {\n        return new ArrayList<>(mitglieder);\n    }\n}\n\nclass Mitglied {\n    private String name;\n    private int mitgliedsNr;\n    private List<Verein> vereine = new ArrayList<>();\n    \n    public void addVerein(Verein verein) {\n        vereine.add(verein);\n    }\n    \n    public List<Verein> getVereine() {\n        return new ArrayList<>(vereine);\n    }\n}\n// Beispiel für eine gerichtete Assoziation (unidirektional)\nclass Professor {\n    private String name;\n    private List<Vorlesung> vorlesungen;\n    \n    public Professor(String name) {\n        this.name = name;\n        this.vorlesungen = new ArrayList<>();\n    }\n    \n    public void addVorlesung(Vorlesung vorlesung) {\n        vorlesungen.add(vorlesung);\n    }\n}\n\nclass Vorlesung {\n    private String titel;\n    // Keine Referenz zurück zum Professor (gerichtete Assoziation)\n}\n```'}
