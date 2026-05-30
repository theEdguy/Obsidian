---
id: 69f9cc11-d99c-4870-8aa5-45d7c4e2ef5b
title: "Komposition_UML"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - entwurfsmuster
  - objektorientierung
  - klassendiagramm
  - softwaremodellierung
  - draft
source: "Klausur_Referenz"
---

# [[Komposition_UML]]

- **Kernkonzept:** Die **Komposition** in [[UML]] ist eine spezielle Form der [[Assoziation]], die eine starke **Ganzes-Teil-Beziehung** zwischen Objekten modelliert. Sie drückt aus, dass ein Teil-Objekt (Komponente) **existenzabhängig** vom Ganzen (Kompositum) ist: Wird das Kompositum zerstört, werden auch alle seine Komponenten zerstört. Die Komposition wird im [[Klassendiagramm]] durch eine ausgefüllte Raute am Ende der Assoziationslinie beim Kompositum dargestellt. Im Gegensatz zur [[Aggregation_UML]] (leere Raute) ist die Lebensdauer der Komponenten strikt an das Kompositum gebunden.
- **Nutzen & Zweck:** Die Komposition wird verwendet, um **starke Besitzverhältnisse** und **exklusive Zugehörigkeit** in der Softwarearchitektur abzubilden. Typische Anwendungsfälle sind:
- **Modellierung von physischen oder logischen Containern** (z. B. ein `Auto` enthält `Motor` und `Räder`, die ohne das Auto nicht existieren).
- **Sicherstellung der Konsistenz**: Da Komponenten nicht unabhängig existieren können, vermeidet man *dangling references* (veraltete Verweise).
- **Unterstützung des [[Single_Responsibility_Principle]]**: Das Kompositum übernimmt die Verantwortung für die Verwaltung seiner Komponenten (Erzeugung, Zerstörung, Koordination).
- **Vereinfachung des Speichermanagements** in Sprachen ohne automatische Speicherbereinigung (z. B. C++).
- **Abgrenzung & Grenzen:** - **Abgrenzung zur Aggregation**: Während die Aggregation eine *schwache* Beziehung darstellt (Teile können unabhängig existieren, z. B. `Student` in einer `Universität`), ist die Komposition *stark* und impliziert Existenzabhängigkeit.
- **Keine Zyklen**: Kompositionen dürfen keine zyklischen Abhängigkeiten enthalten (z. B. `A` enthält `B`, das wiederum `A` enthält), da dies zu unendlichen Rekursionen bei der Zerstörung führen würde.
- **Keine Mehrfachzugehörigkeit**: Eine Komponente darf nicht gleichzeitig zu mehreren Komposita gehören (im Gegensatz zur Aggregation).
- **Stolperstein *Shallow Copy***: Bei Kopieroperationen muss entschieden werden, ob nur Referenzen oder die gesamten Komponenten kopiert werden (vgl. [[Deep_Copy_vs_Shallow_Copy]]).
- **Nicht für Schnittstellen geeignet**: Kompositionen modellieren konkrete Implementierungsdetails, keine [[Schnittstelle|Schnittstellen]] (hierfür eignen sich [[Delegation]] oder [[Vererbung]]).
- **Beispiel / Code:** {'beschreibung': 'Ein UML-Klassendiagramm in Mermaid-Notation, das die Komposition zwischen `Buch` und `Kapitel` zeigt:', 'mermaid_diagramm': 'classDiagram\n    class Buch {\n        -titel: String\n        -kapitel: Kapitel[1..*]\n        +hinzufuegenKapitel(kapitel: Kapitel)\n        +entfernenKapitel(kapitel: Kapitel)\n    }\n    class Kapitel {\n        -ueberschrift: String\n        -inhalt: String\n    }\n    Buch *-- Kapitel : Komposition\n    note for Buch "Ein Buch besteht aus mindestens einem Kapitel.\\nKapitel existieren nur innerhalb eines Buches."', 'java_implementation': 'public class Buch {\n    private String titel;\n    private List<Kapitel> kapitel = new ArrayList<>();\n    \n    public Buch(String titel) {\n        this.titel = titel;\n    }\n    \n    public void hinzufuegenKapitel(String ueberschrift, String inhalt) {\n        this.kapitel.add(new Kapitel(ueberschrift, inhalt));\n    }\n    \n    // Kapitel werden automatisch mit dem Buch zerstört\n    public void close() {\n        this.kapitel.clear(); // Explizite Zerstörung (in Java nicht zwingend nötig)\n    }\n    \n    private class Kapitel {\n        private String ueberschrift;\n        private String inhalt;\n        \n        public Kapitel(String ueberschrift, String inhalt) {\n            this.ueberschrift = ueberschrift;\n            this.inhalt = inhalt;\n        }\n    }\n}'}
