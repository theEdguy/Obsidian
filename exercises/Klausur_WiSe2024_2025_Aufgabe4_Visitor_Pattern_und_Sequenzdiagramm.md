---
id: 615d154d-835b-4f51-a1fe-98d5a833618b
title: "Klausur_WiSe2024_2025_Aufgabe4_Visitor_Pattern_und_Sequenzdiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - ws_2024_2025
  - klausur_ws_2024_2025
  - visitor_pattern
  - klassendiagramm
  - sequenzdiagramm
  - entwurfsmuster
  - rekursion
  - java
  - exercise
  - draft
source: "SWE-WS-2024-2025 - Loesung.pdf"
---

# [[Klausur_WiSe2024_2025_Aufgabe4_Visitor_Pattern_und_Sequenzdiagramm]]

- **Aufgabenstellung:** 
  - **a:**
  Veranschaulichen Sie die statischen Abhängigkeiten des gegebenen Java-Code-Fragments mithilfe eines [[Klassendiagramm|Klassendiagramms]]. Achten Sie dabei auf folgende Aspekte:
  - Attribute und deren Sichtbarkeit
  - Operationen (Methoden) und deren Sichtbarkeit
  - Beziehungen zwischen den Klassen (z. B. Assoziation, Implementierung, Abhängigkeit)
  - Gegebenenfalls Rollen und Multiplizitäten der Beziehungen.
  - **b:**
  Veranschaulichen Sie den dynamischen Vorgang der Summenbildung im gegebenen Code-Fragment. Vervollständigen Sie hierzu ein [[Sequenzdiagramm|Sequenzdiagramm]], das folgende Interaktionen darstellt:
  - Start der Summenbildung in der Methode `sum()` der Klasse `List`
  - Aufruf der `accept`-Methode und Weiterleitung an den `Visitor`
  - Rekursive Abarbeitung der Liste durch den `Sum`-Visitor
  - Rückgabe des Endergebnisses.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **beschreibung:**
  Das [[Klassendiagramm]] sollte folgende Elemente und Beziehungen enthalten:
  1. **Klassen und Schnittstellen:**
     - `List` mit Attribut `list: Elem` (private) und Methoden `insert(int x): void`, `sum(): int` (public).
     - `Elem` mit Attributen `value: int` (protected), `tail: Elem` (private) und Methoden `Elem(int val, Elem tail): Constructor`, `accept(Visitor v): void`, `getVal(): int`, `getNext(): Elem`, `isEmpty(): boolean`.
     - `Visitor` (Schnittstelle) mit Methode `visit(Elem e): void`.
     - `Sum` (implementiert `Visitor`) mit Attribut `sum: int` (private) und Methoden `Sum(Elem e): Constructor`, `visit(Elem e): void`, `sum(): int`.
  
  2. **Beziehungen:**
     - `List` **hat-ein** `Elem` (Assoziation mit Multiplizität 1 an `Elem`).
     - `Elem` **hat-ein** `Elem` (rekursive Assoziation mit Multiplizität 0..1 an `tail`).
     - `Sum` **implementiert** `Visitor` (Realisierungsbeziehung).
     - `Elem` **abhängig von** `Visitor` (Abhängigkeitsbeziehung durch `accept`-Methode).
     - `Sum` **abhängig von** `Elem` (Abhängigkeitsbeziehung durch `visit`-Methode).
  
  ```mermaid
  classDiagram
      class List {
          -list: Elem
          +insert(int x): void
          +sum(): int
      }
      
      class Elem {
          #value: int
          -tail: Elem
          +Elem(int val, Elem tail)
          +accept(Visitor v): void
          +getVal(): int
          +getNext(): Elem
          +isEmpty(): boolean
      }
      
      interface Visitor {
          +visit(Elem e): void
      }
      
      class Sum {
          -sum: int
          +Sum(Elem e)
          +visit(Elem e): void
          +sum(): int
      }
      
      List --> Elem : 1
      Elem --> Elem : 0..1 (tail)
      Sum ..|> Visitor
      Elem ..> Visitor : <<uses>>
      Sum ..> Elem : <<uses>>
  ```
    - **hinweis:** Achten Sie auf die korrekte Darstellung der Sichtbarkeiten (z. B. `+` für public, `-` für private) und die Verwendung von Pfeilen für Assoziationen (einfacher Pfeil) und Implementierungen (gestrichelter Pfeil mit geschlossenem Kopf).
  - **b:**
  - **beschreibung:**
  Das [[Sequenzdiagramm]] sollte folgende Interaktionen darstellen:
  1. **Akteure:** `List`, `Sum`, `Elem` (mehrere Instanzen für rekursive Aufrufe).
  2. **Ablauf:**
     - `List.sum()` ruft `Sum.sum()` auf (über `new Sum(this.list).sum()`).
     - Der Konstruktor `Sum(Elem e)` ruft `e.accept(this)` auf.
     - `Elem.accept(Visitor v)` ruft `v.visit(this)` auf (hier: `Sum.visit(Elem e)`).
     - `Sum.visit(Elem e)` addiert `e.getVal()` zu `sum` und prüft mit `e.isEmpty()`.
     - Falls `!e.isEmpty()`, ruft `e.getNext().accept(this)` auf (rekursiver Aufruf).
     - Nach Abarbeitung aller `Elem`-Instanzen gibt `Sum.sum()` das Ergebnis zurück.
  
  ```mermaid
  sequenceDiagram
      participant List
      participant Sum
      participant Elem1 as Elem (head)
      participant Elem2 as Elem (tail)
      
      List->>Sum: new Sum(list).sum()
      activate Sum
      Sum->>Elem1: accept(this)
      activate Elem1
      Elem1->>Sum: visit(this)
      activate Sum
      Sum->>Elem1: getVal()
      Elem1-->>Sum: value
      Sum->>Elem1: isEmpty()
      Elem1-->>Sum: false
      Sum->>Elem1: getNext()
      Elem1-->>Sum: Elem2
      deactivate Elem1
      
      Sum->>Elem2: accept(this)
      activate Elem2
      Elem2->>Sum: visit(this)
      Sum->>Elem2: getVal()
      Elem2-->>Sum: value
      Sum->>Elem2: isEmpty()
      Elem2-->>Sum: true
      deactivate Elem2
      deactivate Sum
      
      Sum-->>List: sum
      deactivate Sum
  ```
    - **hinweis:** Stellen Sie sicher, dass die rekursiven Aufrufe von `accept` und `visit` korrekt dargestellt werden. Nutzen Sie Aktivierungsbalken, um die Lebensdauer der Objekte zu verdeutlichen.
- **Theoretischer Bezug:** 
  - [[Visitor_Pattern|Visitor-Pattern]] zur Trennung von Datenstruktur und Operationen.
  - [[Klassendiagramm]] zur Darstellung statischer Strukturen.
  - [[Sequenzdiagramm]] zur Modellierung dynamischer Interaktionen.
  - [[Rekursion]] als Mechanismus zur Abarbeitung der Liste.
  - [[Schnittstelle|Schnittstellen]] zur Definition des `Visitor`-Vertrags.
  - [[Abhängigkeitsbeziehung|Abhängigkeiten]] zwischen Klassen im [[Klassendiagramm]].
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von statischen und dynamischen Diagrammen: Teilaufgabe (a) erfordert ein [[Klassendiagramm]], Teilaufgabe (b) ein [[Sequenzdiagramm]].
  - Falsche Darstellung der rekursiven Aufrufe im [[Sequenzdiagramm]]: Rekursion muss durch verschachtelte Aktivierungsbalken oder separate `Elem`-Instanzen dargestellt werden.
  - Vergessen der Sichtbarkeiten (z. B. `private`, `protected`) im [[Klassendiagramm]].
  - Unklare Beziehungen im [[Klassendiagramm]]: `Sum` implementiert `Visitor`, aber `Elem` hängt von `Visitor` ab (nicht umgekehrt).
  - Fehlende Multiplizitäten bei Assoziationen (z. B. `List` hat genau ein `Elem`, `Elem` hat 0..1 `tail`).
  - Falsche Annahme, dass `Sum` direkt auf `Elem`-Attribute zugreift: Der Zugriff erfolgt immer über Methoden (`getVal()`, `getNext()`).
