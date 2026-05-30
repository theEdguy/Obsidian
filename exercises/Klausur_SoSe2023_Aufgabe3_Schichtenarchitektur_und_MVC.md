---
id: 9fe7acdd-cc43-4c18-9d5d-f132feefc2f3
title: "Klausur_SoSe2023_Aufgabe3_Schichtenarchitektur_und_MVC"
date: 2026-05-30
tags:
  - software_engineering
  - sose2023
  - klausur_sose_2023
  - software_architektur
  - mvc
  - schichtenmodell
  - entwurfsmuster
  - abhaengigkeitsmanagement
  - exercise
  - draft
source: "SWE 2023 mit Loesung.pdf"
---

# [[Klausur_SoSe2023_Aufgabe3_Schichtenarchitektur_und_MVC]]

- **Aufgabenstellung:** 
  - **a:**
  Nehmen Sie zu folgender Aussage Stellung: 
  'Im Architekturmuster MVC ist die View (V) für die Darstellung und Präsentation der Daten zuständig, während das Modell (M) die Daten hält und der Controller (C) die Geschäftslogik umsetzt.' 
  Bewerten Sie die Richtigkeit der Aussage und korrigieren Sie gegebenenfalls die falschen Aussagen mit präzisen Erläuterungen.
  - **b:**
  - **i:**
  Die beiden nachfolgenden Klassen A und B sind zwei unterschiedlichen Schichten einer Schichten-Architektur zugeordnet und verfügen jeweils über zwei Methoden op1 und op2. 
  
  Klasse A (Schicht 2):
  ```java
  package layer2; import layer1.B; public class A { public void op1(B b) { b.op2( this ); } public void op2(B b) { // ... } }
  ```
  
  Klasse B (Schicht 1):
  ```java
  package layer1; import layer2.A; public class B { public void op1(A a) { a.op2( this );} public void op2(A a) { //... } }
  ```
  
  Frage: Welche der beiden Klassendefinitionen verstößt gegen die Regeln einer Schichtenarchitektur, wenn die Klasse A zu der direkt über B liegenden Schicht gehört? Begründen Sie Ihre Antwort. Hinweis: Welche Zugriffe sind aufgrund der gewählten Schichtung verboten?
    - **ii:** Welche Möglichkeit sehen Sie, um die in i) angesprochene Problematik zu beseitigen, ohne die jeweilige Schichtenzugehörigkeit der beiden Klassen A und B aufzugeben? Beschreiben Sie Ihre Lösungsidee in Worten oder direkt in Form von Pseudocode.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **bewertung:** Die Aussage ist so nicht richtig.
    - **korrekturen:**
  - - **komponente:** Controller
        - **erlaeuterung:** Der Controller ist Teil der Präsentationsschicht. Er nimmt die Benutzereingaben entgegen und stößt die System-Operationen an. Er setzt nicht die Geschäftslogik um!
      - - **komponente:** Modell
        - **erlaeuterung:** Das Modell ist nicht primär für die Datenhaltung zuständig. Es realisiert vielmehr die Geschäftslogik.
  - **b:**
  - **i:**
  - **verstoss:** Die Definition der Klasse B verstößt gegen die Regeln einer Schichtenarchitektur.
      - **begruendung:** Da B die Klasse A nutzt, die zur höheren Schicht gehört, ist dies unzulässig. In einer Schichtenarchitektur darf eine tiefere Schicht (hier: Schicht 1) keine Abhängigkeiten zu einer höheren Schicht (hier: Schicht 2) haben.
    - **ii:**
  - **loesungsidee:** Die Abhängigkeit von B zu A muss aufgebrochen werden. Dies kann durch die Einführung eines [[Schnittstelle|Interfaces]] erreicht werden:
      - **pseudocode:**
  - **interface:**
  ```java
  package layer1;
  public interface I {
      void op2(B b);
  }
  ```
        - **klasse_b:**
  ```java
  package layer1;
  public class B {
      public void op1(I a) {
          a.op2(this);
      }
      public void op2(I a) {
          //...
      }
  }
  ```
        - **klasse_a:**
  ```java
  package layer2;
  import layer1.B;
  import layer1.I;
  
  public class A implements I {
      public void op1(B b) {
          b.op2(this);
      }
      public void op2(B b) {
          // ...
      }
  }
  ```
        - **erlaeuterung:**
  1. Definiere auf der Schicht von B ein Interface I, welches die Signaturen der benötigten Operation von A (mindestens op2) festlegt.
  2. Dieses Interface wird von A implementiert.
  3. In B wird jedes Vorkommen von A durch I ersetzt, um die Abhängigkeit zur höheren Schicht zu vermeiden.
- **Theoretischer Bezug:** 
  - [[MVC_Pattern|MVC-Architekturmuster]]
  - [[Schichtenarchitektur]]
  - [[Schnittstelle|Schnittstellen]]
  - [[Lose_Kopplung]]
  - [[Abhängigkeitsinversion]]
- **Stolpersteine / Fehlerquellen:** 
  - Verwechslung der Verantwortlichkeiten im [[MVC_Pattern|MVC-Muster]], insbesondere die Annahme, dass der Controller die Geschäftslogik implementiert oder das Modell nur Daten hält.
  - Missachtung der Schichtenregeln, insbesondere die unzulässige Abhängigkeit einer tieferen Schicht von einer höheren Schicht.
  - Unklare Trennung zwischen Präsentationslogik und Geschäftslogik, was zu falschen Zuordnungen von Methoden oder Klassen führt.
  - Fehlende Nutzung von [[Schnittstelle|Schnittstellen]] zur Entkopplung von Schichten, was zu starren und schwer wartbaren Architekturen führt.
