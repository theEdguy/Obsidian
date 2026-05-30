---
id: 351234d5-c522-4f21-ae7a-d82034131144
title: "Klausur_WiSe2023_2024_Aufgabe2_Komponenten_und_Klassendiagramme"
date: 2026-05-30
tags:
  - software_engineering
  - wise2023_2024
  - klausur_ws_2023_2024
  - komponentendiagramm
  - klassendiagramm
  - uml
  - vererbung
  - schnittstellen
  - entwurfsmuster
  - exercise
  - draft
source: "SWE 2023-2024 mit Loesung.pdf"
---

# [[Klausur_WiSe2023_2024_Aufgabe2_Komponenten_und_Klassendiagramme]]

- **Aufgabenstellung:** 
  - **a:** Erstellen Sie ein [[Komponentendiagramm|Komponentendiagramm]] für folgende Aussage: Eine Komponente A verfügt über zwei Ports B und C. Am Port B stellt sie die [[Schnittstelle|Schnittstellen]] D und E bereit und am Port C das [[Schnittstelle|Interface]] F. F bezieht sie über einen Delegation-Konnektor vom Port G der Komponente H.
  - **b:** Erstellen Sie ein [[Klassendiagramm|Klassendiagramm]] für folgende Aussage: Die abstrakte Klasse A implementiert das [[Schnittstelle|Interface]] I und ist eine Spezialisierung der Klasse B.
  - **c:** Erstellen Sie ein [[Klassendiagramm|Klassendiagramm]] für folgende Aussage: Bei Fahrzeugen unterscheidet man zwischen Land- und Wasserfahrzeugen. Während Automobile, Fahrräder und Kutschen zu den Landfahrzeugen zählen und über Räder verfügen, gehören Boote und Yachten zu den Wasserfahrzeugen und haben im Allgemeinen keine Räder. Fahrzeuge, die die Eigenschaften von Land- und Wasserfahrzeugen in sich vereinigen, bezeichnet man als Amphibienfahrzeuge. Während schwimmfähige Automobile Boote mit Rädern sind, schweben Luftkissenfahrzeuge und benötigen deshalb keine Räder, weder an Land noch zu Wasser.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  ```plantuml
  @startuml
  component A {
    port B
    port C
    interface D as "D"
    interface E as "E"
    interface F as "F"
    
    B - [D]
    B - [E]
    C - [F]
  }
  
  component H {
    port G
    interface F as "F"
    G - [F]
  }
  
  A::C --> H::G : Delegation-Konnektor
  @enduml
  ```
  
  **Erläuterung:**
  - Komponente A hat zwei Ports (B und C).
  - Port B stellt die [[Schnittstelle|Schnittstellen]] D und E bereit.
  - Port C stellt das [[Schnittstelle|Interface]] F bereit, das über einen Delegation-Konnektor von Port G der Komponente H bezogen wird.
  - **b:**
  ```plantuml
  @startuml
  abstract class A {
  }
  
  class B {
  }
  
  interface I {
  }
  
  A ..|> B
  A ..|> I
  @enduml
  ```
  
  **Erläuterung:**
  - Die abstrakte Klasse A erbt von Klasse B (Generalisierung).
  - Klasse A implementiert das [[Schnittstelle|Interface]] I (Realisierung).
  - **c:**
  ```plantuml
  @startuml
  class Fahrzeug {
  }
  
  class Landfahrzeug {
    + hatRäder: Boolean
  }
  
  class Wasserfahrzeug {
  }
  
  class Automobil {
  }
  
  class Fahrrad {
  }
  
  class Kutsche {
  }
  
  class Boot {
  }
  
  class Yacht {
  }
  
  class Amphibienfahrzeug {
  }
  
  class SchwimmfaehigesAutomobil {
  }
  
  class Luftkissenfahrzeug {
  }
  
  Fahrzeug <|-- Landfahrzeug
  Fahrzeug <|-- Wasserfahrzeug
  Landfahrzeug <|-- Automobil
  Landfahrzeug <|-- Fahrrad
  Landfahrzeug <|-- Kutsche
  Wasserfahrzeug <|-- Boot
  Wasserfahrzeug <|-- Yacht
  Landfahrzeug <|-- Amphibienfahrzeug
  Wasserfahrzeug <|-- Amphibienfahrzeug
  Amphibienfahrzeug <|-- SchwimmfaehigesAutomobil
  Fahrzeug <|-- Luftkissenfahrzeug
  
  note right of Landfahrzeug::hatRäder
    Standardmäßig true,
    außer bei Luftkissenfahrzeugen
  end note
  @enduml
  ```
  
  **Erläuterung:**
  - Die Basisklasse `Fahrzeug` wird in `Landfahrzeug` und `Wasserfahrzeug` spezialisiert.
  - `Landfahrzeug` hat das Attribut `hatRäder` (Standard: `true`).
  - `Amphibienfahrzeug` erbt von beiden (`Landfahrzeug` und `Wasserfahrzeug`).
  - `SchwimmfaehigesAutomobil` ist ein spezielles `Amphibienfahrzeug`.
  - `Luftkissenfahrzeug` erbt direkt von `Fahrzeug` und hat keine Räder (Attribut `hatRäder` wird überschrieben oder ignoriert).
- **Theoretischer Bezug:** 
  - [[Komponentendiagramm]]
  - [[Klassendiagramm]]
  - [[Schnittstelle|Schnittstellen]]
  - [[Delegation_Konnektor]]
  - [[Generalisierung_(Vererbung)|Generalisierung]]
  - [[Realisierung_(Implementierung)|Realisierung]]
  - [[Abstrakte_Klasse]]
  - [[Mehrfachvererbung]]
  - [[Liskovsches_Substitutionsprinzip]]
- **Stolpersteine / Fehlerquellen:** 
  - Bei Teilaufgabe a) wird oft der Delegation-Konnektor falsch dargestellt (z. B. als direkte Assoziation statt als Konnektor zwischen Ports).
  - Bei Teilaufgabe b) wird die [[Generalisierung_(Vererbung)|Generalisierung]] (Vererbung) mit der [[Realisierung_(Implementierung)|Realisierung]] (Implementierung eines [[Schnittstelle|Interfaces]]) verwechselt.
  - Bei Teilaufgabe c) wird die [[Mehrfachvererbung]] für `Amphibienfahrzeug` nicht korrekt modelliert oder das `Luftkissenfahrzeug` fälschlicherweise als `Landfahrzeug` klassifiziert.
  - Das Attribut `hatRäder` wird nicht konsistent für alle Unterklassen von `Landfahrzeug` berücksichtigt (z. B. bei `Luftkissenfahrzeug`).
  - Die Unterscheidung zwischen [[Aggregation]] und [[Komposition]] ist hier nicht relevant, wird aber oft fälschlicherweise eingebaut.
