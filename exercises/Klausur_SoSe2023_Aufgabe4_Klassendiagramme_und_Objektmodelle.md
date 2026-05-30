---
id: 234bf6f8-7b77-4eb5-aaff-e9fb46486c57
title: "Klausur_SoSe2023_Aufgabe4_Klassendiagramme_und_Objektmodelle"
date: 2026-05-30
tags:
  - software_engineering
  - sose2023
  - klausur_sose_2023
  - klassendiagramm
  - uml
  - vererbung
  - schnittstelle
  - objektorientierter_entwurf
  - softwaremodellierung
  - exercise
  - draft
source: "SWE 2023 mit Loesung.pdf"
---

# [[Klausur_SoSe2023_Aufgabe4_Klassendiagramme_und_Objektmodelle]]

- **Aufgabenstellung:** 
  - **a:** Erstellen Sie zu folgendem Java-Code-Fragment ein [[Klassendiagramm]], das alle relevanten [[Klasse|Klassen]] und [[Schnittstelle|Interfaces]] sowie deren Beziehungen untereinander darstellt. Achten Sie darauf, dass jede [[Klasse]] und jedes [[Schnittstelle|Interface]] mindestens eine [[Operation]] bzw. eine [[Methode]] enthält. (Der konkrete Java-Code ist in der Originalaufgabe nicht vollständig angegeben, daher wird hier die allgemeine Anforderung beschrieben.)
  - **b:**
  Stellen Sie folgenden Sachverhalt mithilfe eines [[Klassendiagramm|Klassendiagramms]] dar:
  
  ```java
  class A extends B implements C {
      @Override
      public void op1() {
          super.op2();
      }
      @Override
      protected void op2() {
          this.op1();
      }
  }
  ```
  
  Zusätzlich soll der folgende Sachverhalt modelliert werden:
  
  'Uhren sind wie Barometer und Thermometer [[Messgerät|Messgeräte]]. Ihre zentrale Aufgabe ist die Angabe der aktuellen Zeit. Besondere Uhren sind analoge Uhren. Sie verfügen über ein mechanisches Räderwerk, das dafür sorgt, dass die in der Feder der Uhr gespeicherte Energie in eine Drehung der Uhrzeiger verwandelt wird.'
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **beschreibung:**
  1. Identifiziere alle [[Klasse|Klassen]] und [[Schnittstelle|Interfaces]] im gegebenen Java-Code-Fragment.
  2. Stelle die [[Vererbung|Vererbungsbeziehungen]] (extends) und [[Implementierung|Implementierungsbeziehungen]] (implements) dar.
  3. Füge mindestens eine [[Operation]] oder [[Methode]] pro [[Klasse]] und [[Schnittstelle|Interface]] hinzu.
  4. Nutze die UML-Notation für [[Klassendiagramm|Klassendiagramme]]:
     - [[Klasse|Klassen]] als Rechtecke mit drei Abschnitten (Name, Attribute, Methoden).
     - [[Schnittstelle|Interfaces]] mit dem Stereotyp `<<interface>>`.
     - [[Vererbung]] als durchgezogene Linie mit geschlossener, nicht ausgefüllter Pfeilspitze.
     - [[Implementierung]] als gestrichelte Linie mit geschlossener, nicht ausgefüllter Pfeilspitze.
  
  Beispiel (falls der Code `class X implements Y { void method() {} }` gegeben wäre):
  ```plantuml
  interface Y {
      + void operation()
  }
  
  class X {
      + void method()
  }
  
  X ..|> Y
  ```
    - **hinweis:** Da der konkrete Java-Code in der Aufgabenstellung fehlt, ist hier die allgemeine Vorgehensweise beschrieben. Für eine vollständige Lösung müsste der Code analysiert und alle [[Klasse|Klassen]], [[Schnittstelle|Interfaces]] und [[Methode|Methoden]] extrahiert werden.
  - **b:**
  - **teil1:**
  - **beschreibung:**
  Modellierung des Java-Code-Fragments:
  ```plantuml
  class B {
      + {abstract} void op2()
  }
  
  interface C {
      + void op1()
  }
  
  class A {
      + void op1()
      # void op2()
  }
  
  A --|> B
  A ..|> C
  ```
  
  Erläuterung:
  - [[Klasse]] `B` enthält die [[Methode]] `op2()`, die in `A` überschrieben wird.
  - [[Schnittstelle]] `C` definiert `op1()`, die in `A` implementiert wird.
  - Die Beziehungen zeigen [[Vererbung]] (`A extends B`) und [[Implementierung]] (`A implements C`).
  - Sichtbarkeiten: `+` für public, `#` für protected.
      - **stichpunkte:**
  - Vererbung von `B` zu `A` mit `extends`.
        - Implementierung von `C` durch `A` mit `implements`.
        - Überschreibung der [[Methode|Methoden]] `op1()` und `op2()`.
        - Aufruf von `super.op2()` und `this.op1()` zeigt Abhängigkeiten innerhalb der [[Klasse]].
    - **teil2:**
  - **beschreibung:**
  Modellierung des Uhren-Sachverhalts:
  ```plantuml
  abstract class Messgeraet {
      + {abstract} void messen()
  }
  
  class Uhr {
      + void aktuelleZeitAngeben()
  }
  
  class AnalogeUhr {
      - mechanischesRaederwerk: Raederwerk
      - feder: Feder
      + void zeigerDrehen()
  }
  
  class Barometer {
      + void luftdruckMessen()
  }
  
  class Thermometer {
      + void temperaturMessen()
  }
  
  class Raederwerk {
      + void energieUmwandeln()
  }
  
  class Feder {
      + energieSpeichern()
  }
  
  Uhr --|> Messgeraet
  Barometer --|> Messgeraet
  Thermometer --|> Messgeraet
  AnalogeUhr --|> Uhr
  AnalogeUhr *-- Raederwerk
  AnalogeUhr *-- Feder
  ```
  
  Erläuterung:
  - `Messgeraet` ist eine abstrakte [[Klasse]] mit der abstrakten [[Methode]] `messen()`.
  - `Uhr`, `Barometer` und `Thermometer` erben von `Messgeraet`.
  - `AnalogeUhr` ist eine Spezialisierung von `Uhr` und enthält ein [[Komposition|komponiertes]] `Raederwerk` und eine `Feder`.
  - [[Komposition]] wird durch eine ausgefüllte Raute dargestellt (starke Lebenszyklusabhängigkeit).
    - **stichpunkte:**
  - Abstrakte [[Klasse]] `Messgeraet` als Generalisierung für konkrete Messgeräte.
      - [[Vererbung]] von `Uhr`, `Barometer` und `Thermometer` von `Messgeraet`.
      - [[Vererbung]] von `AnalogeUhr` von `Uhr`.
      - [[Komposition]] zwischen `AnalogeUhr` und `Raederwerk`/`Feder` (Teile können nicht ohne das Ganze existieren).
      - Methoden wie `aktuelleZeitAngeben()` oder `zeigerDrehen()` spiegeln die fachliche Logik wider.
- **Theoretischer Bezug:** 
  - [[Klassendiagramm]]
  - [[Vererbung]]
  - [[Schnittstelle|Interfaces]]
  - [[Implementierung]]
  - [[Abstrakte_Klasse|Abstrakte Klassen]]
  - [[Methode|Methodenüberschreibung]]
  - [[Komposition]]
  - [[Aggregation]]
  - [[UML]]
  - [[Liskovsches_Substitutionsprinzip|Liskovsches Substitutionsprinzip]]
  - [[SOLID_Prinzipien]]
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von [[Vererbung]] und [[Implementierung]] in der UML-Notation (durchgezogene vs. gestrichelte Linie).
  - Falsche Darstellung von [[Sichtbarkeit|Sichtbarkeiten]] (z. B. `private` als `-` statt `#` für `protected`).
  - Unklare Trennung zwischen [[Komposition]] und [[Aggregation]] (ausgefüllte vs. nicht ausgefüllte Raute).
  - Vergessen von [[Methode|Methoden]] oder [[Attribut|Attributen]] in den [[Klasse|Klassen]] oder [[Schnittstelle|Interfaces]].
  - Falsche Modellierung von `super.op2()` und `this.op1()`: Diese zeigen Abhängigkeiten innerhalb der [[Klasse]], müssen aber nicht explizit im [[Klassendiagramm]] dargestellt werden.
  - Unnötige Modellierung von trivialen [[Klasse|Klassen]] (z. B. `String` oder primitive Typen).
  - Fehlende Abstraktion: `Messgeraet` sollte als abstrakte [[Klasse]] modelliert werden, da es keine konkreten Instanzen gibt.
