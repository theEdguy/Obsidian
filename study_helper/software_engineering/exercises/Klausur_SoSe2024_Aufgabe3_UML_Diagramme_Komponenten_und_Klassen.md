---
id: 8a5b3819-18f8-462e-9b89-6d3fa5397f28
title: "Klausur_SoSe2024_Aufgabe3_UML_Diagramme_Komponenten_und_Klassen"
date: 2026-05-30
tags:
  - software_engineering
  - sose2024
  - klausur_sose_2024
  - uml
  - komponentendiagramm
  - klassendiagramm
  - vererbung
  - schnittstellen
  - entwurfsmuster
  - exercise
  - draft
source: "SWE-SoSe-2024 - (Loesung).pdf"
---

# [[Klausur_SoSe2024_Aufgabe3_UML_Diagramme_Komponenten_und_Klassen]]

- **Aufgabenstellung:** 
  - **a:** Veranschaulichen Sie den folgenden Sachverhalt mithilfe eines [[Komponentendiagramm|Komponentendiagramms]]: Die Komponente A erwartet am Port P das [[Schnittstelle|Interface]] I, welches durch die Komponente B am Port Q bereitgestellt wird, nachdem B es über einen Delegation-Konnektor vom Port R der Komponente C bezogen hat.
  - **b:** Veranschaulichen Sie den folgenden Sachverhalt mithilfe eines [[Klassendiagramm|Klassendiagramms]]: Künstler erschaffen Kunstwerke. Jedes Kunstwerk lässt sich einem bestimmten Kunststil zuordnen und ist durch eine spezifische Technik charakterisiert. Techniken sind definiert durch die Methoden und Materialien, die zum Einsatz kommen, während sich Kunststile, wie z.B. Expressionismus oder Jugendstil, in unterschiedlichen Philosophien und Darstellungsformen manifestieren.
  - **c:**
  Vervollständigen Sie das abgebildete [[Klassendiagramm]] anhand des gegebenen Code-Fragments. Ergänzen Sie Attribute, Operationen und alle weiteren notwendigen Beziehungen.
  
  ```java
  class A extends B {
    private B myB;
    public A(B b) {
      this.myB = b;
    }
    @Override
    public C op1(C c) {
      return (this.myB != null) ? super.op1(this.myB) : this.op2(c);
    }
  }
  ```
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **beschreibung:**
  Das [[Komponentendiagramm]] zeigt drei Komponenten (A, B, C) mit folgenden Eigenschaften:
  - Komponente A hat einen Port P, der das [[Schnittstelle|Interface]] I **erwartet** (lollipop-Notation mit offener Kreis-Seite).
  - Komponente B hat einen Port Q, der das [[Schnittstelle|Interface]] I **bereitstellt** (lollipop-Notation mit gefülltem Kreis).
  - Komponente C hat einen Port R, der das [[Schnittstelle|Interface]] I bereitstellt.
  - Ein Delegation-Konnektor verbindet Port R von C mit Port Q von B (Pfeil von Q nach R).
  - Ein Assembly-Konnektor verbindet Port P von A mit Port Q von B (Pfeil von P nach Q).
    - **diagramm_hinweise:** Verwende die UML-Notation für Komponenten (Rechtecke mit <<component>>-Stereotyp), Ports (kleine Quadrate an den Komponentenrändern) und Konnektoren (Linien mit Pfeilspitzen). Das [[Schnittstelle|Interface]] I wird als Kreis dargestellt, der mit den Ports verbunden ist.
  - **b:**
  - **beschreibung:**
  Das [[Klassendiagramm]] enthält folgende Klassen und Beziehungen:
  - **Klasse `Künstler`**: Erschafft [[Kunstwerk|Kunstwerke]] (Assoziation mit Multiplizität * auf der Seite von `Kunstwerk`).
  - **Klasse `Kunstwerk`**: Hat eine Assoziation zu `Kunststil` (Multiplizität 1) und zu `Technik` (Multiplizität 1).
  - **Klasse `Kunststil`**: Enthält Attribute wie `philosophie: String` und `darstellungsform: String`. Beispiele für Instanzen: Expressionismus, Jugendstil.
  - **Klasse `Technik`**: Enthält Attribute wie `methoden: String` und `materialien: String`.
  
  Verwende eine **Aggregation** zwischen `Kunstwerk` und `Technik`/`Kunststil`, da ein Kunstwerk ohne Technik/Stil existieren kann (lose Kopplung).
    - **diagramm_hinweise:** Klassen werden als Rechtecke mit drei Abschnitten (Name, Attribute, Operationen) dargestellt. Assoziationen werden als Linien mit optionalen Multiplizitäten (z. B. 1, *) und Rollennamen gezeichnet. Aggregation wird durch eine leere Raute an der „Ganzes“-Seite gekennzeichnet.
  - **c:**
  - **beschreibung:**
  Das vervollständigte [[Klassendiagramm]] zeigt folgende Elemente:
  - **Klasse `A`** (erbt von `B`):
    - Attribut: `myB: B` (Sichtbarkeit `private`).
    - Operationen:
      - `A(b: B)` (Konstruktor).
      - `op1(c: C): C` (überschreibt die Methode von `B`).
      - `op2(c: C): C` (implizit, da im Code aufgerufen).
  - **Klasse `B`**:
    - Operation: `op1(c: C): C` (wird von `A` überschrieben).
  - **Klasse `C`**: Keine Attribute/Operationen im gegebenen Code, aber als Parameter/Return-Typ relevant.
  
  Beziehungen:
  - **Vererbung**: `A` erbt von `B` (durchgezogene Linie mit geschlossener, leerer Pfeilspitze).
  - **Assoziation**: `A` hat eine Assoziation zu `B` (Attribut `myB`), dargestellt als Linie mit Pfeil von `A` zu `B`.
  - **Abhängigkeit**: `A` und `B` hängen von `C` ab (gestrichelte Linie mit offener Pfeilspitze zu `C`).
    - **code_analyse:**
  Der Code zeigt:
  1. **Vererbung**: `A extends B` → `A` ist eine Spezialisierung von `B`.
  2. **Komposition**: `A` enthält eine Referenz auf `B` (`myB`) → Assoziation mit Kardinalität 1.
  3. **Polymorphie**: `op1` wird in `A` überschrieben und ruft `super.op1` auf.
  4. **Abhängigkeit**: `C` wird als Parameter/Return-Typ verwendet → `A` und `B` hängen von `C` ab.
- **Theoretischer Bezug:** 
  - [[Komponentendiagramm]]
  - [[Klassendiagramm]]
  - [[Schnittstelle]]
  - [[Delegation_Konnektor]]
  - [[Vererbung]]
  - [[Polymorphie]]
  - [[Assoziation]]
  - [[Aggregation]]
  - [[Liskovsches_Substitutionsprinzip|Liskovsche Substitutionsprinzip]]
  - [[UML_Notation]]
- **Stolpersteine / Fehlerquellen:** 
  - a) **Falsche Konnektor-Typen**: Verwechslung von Assembly- und Delegation-Konnektoren. Ein Delegation-Konnektor verbindet **interne** Ports einer Komponente, während ein Assembly-Konnektor **externe** Ports verschiedener Komponenten verbindet.
  - a) **Schnittstellen-Notation**: Falsche Darstellung des [[Schnittstelle|Interfaces]] (z. B. als Klasse statt als Kreis).
  - b) **Beziehungsarten**: Verwechslung von [[Aggregation]] und [[Komposition]] (z. B. Komposition für `Kunstwerk` und `Technik` statt Aggregation).
  - b) **Multiplizitäten**: Fehlende oder falsche Multiplizitäten (z. B. `*` für `Künstler` zu `Kunstwerk` statt `1..*`).
  - c) **Vererbung vs. Assoziation**: Vermischung der Vererbungsbeziehung (`A extends B`) mit der Assoziation (`A` enthält `B`).
  - c) **Sichtbarkeiten**: Vergessen von `private` für das Attribut `myB`.
  - c) **Operationen**: Fehlende Angabe der Parameter- und Return-Typen (z. B. `op1(c: C): C`).
