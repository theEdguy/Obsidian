---
id: 457a6bbc-a001-4f2f-8617-1f7c32cf4a0e
title: "Klausur_SoSe2025_Aufgabe3_Speiseeis_Klassendiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - sose_2025
  - klausur_sose_2025
  - klassendiagramm
  - vererbung
  - objektorientierte_modellierung
  - software_analyse
  - exercise
  - draft
source: "SWE-SoSe-2025-Loesung.pdf"
---

# [[Klausur_SoSe2025_Aufgabe3_Speiseeis_Klassendiagramm]]

- **Aufgabenstellung:** 
  Veranschaulichen Sie den folgenden Sachverhalt mit einem [[Klassendiagramm|Klassendiagramm]]:
  
  Speiseeis lässt sich in vier Kategorien unterteilen: Milcheis, Fruchteis, Sorbet und Wassereis.
  - Milcheis besteht aus Milch und Sahne und enthält weder Wasser noch Fruchtstücke. Es enthält diverse Aromastoffe und reichlich Zucker. Es zeichnet sich durch eine sehr cremige Konsistenz aus. Auch Softeis zählt dazu.
  - Fruchteis kombiniert Fruchtpüree mit Milch, enthält aber keine Sahne. Es ist nur leicht cremig.
  - Sorbet besteht aus Fruchtpüree, enthält also weder Milch noch Sahne, sondern Wasser und Zucker. Es hat eine eher glatte Konsistenz.
  - Wassereis besteht nur aus Wasser, Aromen und Zucker. Es enthält keinerlei Fruchtanteile oder Milchprodukte. Es hat eine eher harte Konsistenz.
- **Lösungsweg / Musterlösung:** 
  ### Musterlösung: Klassendiagramm für Speiseeis-Kategorien
  
  ```mermaid
  classDiagram
      class Speiseeis {
          <<abstract>>
          +String aromastoffe
          +double zuckergehalt
          +String konsistenz
      }
  
      class Milcheis {
          +double milchgehalt
          +double sahnegehalt
      }
  
      class Fruchteis {
          +double fruchtpueree_gehalt
          +double milchgehalt
      }
  
      class Sorbet {
          +double fruchtpueree_gehalt
          +double wassergehalt
      }
  
      class Wassereis {
          +double wassergehalt
      }
  
      Speiseeis <|-- Milcheis
      Speiseeis <|-- Fruchteis
      Speiseeis <|-- Sorbet
      Speiseeis <|-- Wassereis
  
      class Softeis {
      }
  
      Milcheis <|-- Softeis
  ```
  
  **Erläuterung:**
  1. Die abstrakte Basisklasse `Speiseeis` enthält gemeinsame Attribute wie `aromastoffe`, `zuckergehalt` und `konsistenz`.
  2. Die vier Kategorien (`Milcheis`, `Fruchteis`, `Sorbet`, `Wassereis`) erben von `Speiseeis` und ergänzen spezifische Attribute (z. B. `milchgehalt` bei `Milcheis`).
  3. `Softeis` wird als Subklasse von `Milcheis` modelliert, da es eine spezielle Form von Milcheis darstellt.
  4. Die Vererbungshierarchie spiegelt die taxonomische Beziehung der Eissorten wider und ermöglicht die Nutzung von [[Polymorphie|Polymorphismus]] für gemeinsame Methoden (z. B. `berechneKalorien()`).
- **Theoretischer Bezug:** 
  Dieses Problem bezieht sich auf:
  - [[Klassendiagramm|Klassendiagramme]] zur Modellierung von [[Vererbung|Vererbungsbeziehungen]]
  - [[Abstrakte_Klasse|Abstrakte Klassen]] zur Definition gemeinsamer Schnittstellen
  - [[Generalisierung_Spezialisierung|Generalisierung/Spezialisierung]] in der [[Objektorientierte_Analyse_und_Design|objektorientierten Analyse]]
  - [[Liskovsches_Substitutionsprinzip|Liskovsches Substitutionsprinzip]] für konsistente Vererbungshierarchien
- **Stolpersteine / Fehlerquellen:** 
  - Falsche Modellierung der `Softeis`-Klasse: Sie darf nicht direkt von `Speiseeis` erben, sondern muss als Subklasse von `Milcheis` abgebildet werden, da es eine spezielle Form von Milcheis ist.
  - Vermischung von Attributen: Gemeinsame Attribute (z. B. `zuckergehalt`) müssen in der Basisklasse `Speiseeis` definiert werden, nicht in den Subklassen.
  - Fehlende Abstraktion: Die Basisklasse `Speiseeis` sollte als `abstract` markiert werden, da sie nicht direkt instanziiert werden soll.
  - Unklare Konsistenz-Attribute: Die `konsistenz` sollte als Attribut in der Basisklasse definiert werden, um [[Polymorphie|polymorphe]] Zugriffe zu ermöglichen.
  - Überflüssige Assoziationen: Es besteht keine Notwendigkeit für Aggregations- oder Kompositionsbeziehungen zwischen den Eissorten, da es sich um eine reine Vererbungshierarchie handelt.
