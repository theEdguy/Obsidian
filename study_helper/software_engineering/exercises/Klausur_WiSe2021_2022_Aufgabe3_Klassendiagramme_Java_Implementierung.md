---
id: 18dbeb8e-cddc-47c2-a99a-7a6cb5c98cec
title: "Klausur_WiSe2021_2022_Aufgabe3_Klassendiagramme_Java_Implementierung"
date: 2026-05-30
tags:
  - software_engineering
  - wise2021_2022
  - klausur_ws2021_2022
  - klassendiagramm
  - java_implementierung
  - assoziation
  - komposition
  - uml
  - entwurf
  - exercise
  - draft
source: "SWE 2021-2022 mit Loesung.pdf"
---

# [[Klausur_WiSe2021_2022_Aufgabe3_Klassendiagramme_Java_Implementierung]]

- **Aufgabenstellung:** 
  - **teil_1:**
  Gegeben ist ein Klassendiagramm, in dem die Klasse 'A' eine unidirektionale Assoziation zu vielen Instanzen der Klasse 'B' besitzt. Die Assoziation ist aus Sicht von 'B' nicht navigierbar.
  
  a) Implementieren Sie die Klasse 'A' in Java (Pseudo-Code genügt).
  b) Begründen Sie Ihre Implementierungsentscheidung.
  - **teil_2:**
  Gegeben ist ein Klassendiagramm, in dem die Klasse 'A' eine unidirektionale Assoziation zu vielen Instanzen der Klasse 'B' mit einem Qualifier 'id' besitzt. Die Assoziation ist aus Sicht von 'B' nicht navigierbar, und der Qualifier macht die Beziehung aus Sicht von 'A' eindeutig.
  
  c) Implementieren Sie die Klasse 'A' in Java (Pseudo-Code genügt).
  d) Begründen Sie Ihre Implementierungsentscheidung.
  - **teil_3:**
  Gegeben ist ein Klassendiagramm, in dem die Klasse 'A' eine Komposition mit genau zwei Instanzen der Klasse 'B' darstellt. Es besteht eine existentielle Abhängigkeit der 'B'-Instanzen von 'A'.
  
  e) Implementieren Sie die Klasse 'A' in Java (Pseudo-Code genügt).
  f) Begründen Sie Ihre Implementierungsentscheidung und gehen Sie auf die Besonderheiten der Komposition in Java ein.
  - **teil_4:**
  Gegeben ist ein Klassendiagramm, in dem die Assoziation zwischen den Klassen 'A' und 'B' bidirektional navigierbar ist. Beide Klassen können maximal zwei Instanzen der jeweils anderen Klasse referenzieren.
  
  g) Implementieren Sie die Klassen 'A' und 'B' sowie eine Hilfsklasse oder -methode, die die bidirektionale Beziehung herstellt (Pseudo-Code genügt).
  h) Begründen Sie Ihre Implementierungsentscheidung und gehen Sie auf die Herausforderungen der Größenbeschränkung ein.
- **Lösungsweg / Musterlösung:** 
  - **teil_1:**
  - **a:**
  ```java
  class A {
      private List<B> myBs = new ArrayList<>();
      
      public void addB(B b) {
          myBs.add(b);
      }
  }
  ```
    - **b:** Die Implementierung nutzt eine `List<B>`, um die unidirektionale Assoziation zu vielen Instanzen von 'B' abzubilden. Da die Assoziation aus Sicht von 'B' nicht navigierbar ist, wird keine Rückreferenz in 'B' benötigt. Eine Liste ist hier die einfachste Lösung, um mehrere 'B'-Instanzen zu verwalten.
  - **teil_2:**
  - **c:**
  ```java
  class A {
      private Map<ID, B> myBs = new HashMap<>();
      
      public void addB(ID id, B b) {
          myBs.put(id, b);
      }
  }
  ```
    - **d:** Die Implementierung nutzt eine `Map<ID, B>`, um den Qualifier 'id' abzubilden, der die Beziehung aus Sicht von 'A' eindeutig macht. Da die Assoziation aus Sicht von 'B' nicht navigierbar ist, wird keine Rückreferenz benötigt. Eine Map ermöglicht den effizienten Zugriff auf 'B'-Instanzen über den Qualifier.
  - **teil_3:**
  - **e:**
  ```java
  class A {
      private B[] myBs = new B[]{new B(), new B()};
      
      public A() {
          // Initialisierung der B-Instanzen im Konstruktor
      }
  }
  ```
  
  Alternativ mit Navigierbarkeit:
  
  ```java
  class A {
      private B[] myBs = new B[]{new B(this), new B(this)};
  }
  ```
    - **f:** Die Komposition wird durch die Erzeugung der 'B'-Instanzen im Konstruktor von 'A' realisiert, da 'B' existentiell von 'A' abhängig ist. In Java kann die existentielle Abhängigkeit nicht vollständig erzwungen werden, aber die Initialisierung im Konstruktor stellt sicher, dass 'B'-Instanzen nur im Kontext von 'A' existieren. Falls Navigierbarkeit erforderlich ist, wird 'this' an die 'B'-Konstruktoren übergeben.
  - **teil_4:**
  - **g:**
  ```java
  class A {
      private Set<B> myBs = new HashSet<>();
      
      public void addB(B b) {
          if (myBs.size() < 2) {
              myBs.add(b);
          }
      }
  }
  
  class B {
      private Set<A> myAs = new HashSet<>();
      
      public void addA(A a) {
          if (myAs.size() < 2) {
              myAs.add(a);
          }
      }
  }
  
  class Assigner {
      public void assign(A a, B b) {
          if (a.myBs.size() < 2 && b.myAs.size() < 2) {
              a.addB(b);
              b.addA(a);
          }
      }
  }
  ```
    - **h:** Die bidirektionale Assoziation wird durch wechselseitige Referenzen in 'A' und 'B' realisiert. Eine separate `Assigner`-Klasse oder -methode stellt sicher, dass die Größenbeschränkung (max. 2 Referenzen) eingehalten wird. Die Verwendung von `Set` verhindert Duplikate und ermöglicht einfache Größenprüfungen. Die Herausforderung liegt in der konsistenten Verwaltung der bidirektionalen Beziehung, um Inkonsistenzen zu vermeiden.
- **Theoretischer Bezug:** 
  - [[Klassendiagramm|Klassendiagramme]]
  - [[Assoziation_(UML)|Assoziationen]]
  - [[Komposition_(UML)|Komposition]]
  - [[Navigierbarkeit|Navigierbarkeit]]
  - [[Qualifier_(UML)|Qualifier]]
  - [[Bidirektionale_Assoziation|Bidirektionale Assoziationen]]
  - [[Entwurfsmuster|Entwurfsmuster]] (z. B. für die `Assigner`-Klasse)
- **Stolpersteine / Fehlerquellen:** 
  - Verwechslung von [[Aggregation_(UML)|Aggregation]] und [[Komposition_(UML)|Komposition]] (existenzielle Abhängigkeit wird oft falsch umgesetzt).
  - Fehlende Berücksichtigung der Navigierbarkeit, insbesondere bei bidirektionalen Assoziationen.
  - Unklare Handhabung von Qualifiern: Oft wird fälschlicherweise eine Assoziationsklasse statt einer `Map` verwendet.
  - Größenbeschränkungen in bidirektionalen Assoziationen werden nicht konsistent geprüft, was zu Inkonsistenzen führen kann.
  - Vernachlässigung der Initialisierung von Komponenten im Konstruktor bei Kompositionen.
  - Unnötige Komplexität durch übermäßige Verwendung von Assoziationsklassen, obwohl einfache Datenstrukturen wie `List` oder `Map` ausreichen.
