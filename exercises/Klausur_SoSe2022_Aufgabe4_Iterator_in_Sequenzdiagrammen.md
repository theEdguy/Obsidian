---
id: 92dbc1f9-97d0-4891-9cd3-47915d871b9f
title: "Klausur_SoSe2022_Aufgabe4_Iterator_in_Sequenzdiagrammen"
date: 2026-05-30
tags:
  - software_engineering
  - sose2022
  - klausur_sose_2022
  - iterator_pattern
  - sequenzdiagramm
  - warteschlange
  - uml
  - dynamische_modellierung
  - verkettete_liste
  - exercise
  - draft
source: "SWE 2022 mit Loesung.pdf"
---

# [[Klausur_SoSe2022_Aufgabe4_Iterator_in_Sequenzdiagrammen]]

- **Aufgabenstellung:** 
  - **a:** (4 Punkte) Implementieren Sie den Konstruktor der Klasse `Iter` gemäß der gegebenen Vorlage. Der Konstruktor soll den Iterator so initialisieren, dass er beim ersten Aufruf von `next()` das erste Element der Warteschlange zurückgibt.
  - **b:**
  (6 + 4 Punkte) Spezifizieren Sie die Operation `next` des Iterators, die die einzelnen Jobs sukzessive aufzählt, mittels eines Sequenzdiagramms und implementieren Sie die Operation gemäß der Vorlage. 
  - (6 Punkte) Sequenzdiagramm: Zeigen Sie die Interaktion zwischen dem Iterator (`Iter`), der Warteschlange (`FiFo`) und den Elementen (`Elem`) bei einem Aufruf von `next()`. 
  - (4 Punkte) Implementierung: Ergänzen Sie die Methode `next()` in der Klasse `Iter` so, dass sie das aktuelle Job-Objekt zurückgibt und den Iterator auf das nächste Element in der Warteschlange setzt.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **beschreibung:** Der Konstruktor der Klasse `Iter` muss den Iterator so initialisieren, dass er auf das erste Element der Warteschlange (`FiFo`) zeigt. Dafür wird das erste Element der Warteschlange (`fifo.getFirst()`) abgerufen und im Iterator als Startpunkt gesetzt (`this.setNext(e)`).
    - **code:**
  ```java
  private Iter(FiFo fifo) {
      Elem e = fifo.getFirst();
      this.setNext(e);
  }
  ```
  - **b:**
  - **sequenzdiagramm:**
  - **beschreibung:**
  Das Sequenzdiagramm zeigt folgende Interaktionen:
  1. Der Aufrufer (z. B. `Client`) ruft `next()` auf dem Iterator (`Iter`) auf.
  2. Der Iterator (`Iter`) greift auf das aktuelle Element (`this.next`) zu und ruft `getJob()` auf, um das `Job`-Objekt zu erhalten.
  3. Der Iterator ruft `getNext()` auf dem aktuellen Element auf, um das nächste Element in der Warteschlange zu ermitteln.
  4. Der Iterator setzt seinen internen Zeiger (`this.next`) auf das nächste Element.
  5. Der Iterator gibt das `Job`-Objekt an den Aufrufer zurück.
  
  Hinweis: Die Warteschlange (`FiFo`) selbst ist an der Interaktion nicht direkt beteiligt, da der Iterator bereits eine Referenz auf das erste Element hält und sich selbstständig durch die verkettete Liste bewegt.
      - **diagramm_elemente:**
  - Teilnehmer: `Client`, `Iter`, `Elem` (als Instanz von `this.next`)
        - Nachrichten: `next()`, `getJob()`, `getNext()`, `setNext(Elem)`
        - Rückgabewerte: `Job`-Objekt
    - **implementierung:**
  - **beschreibung:**
  Die Methode `next()` muss zwei Aufgaben erfüllen:
  1. Das aktuelle `Job`-Objekt zurückgeben.
  2. Den Iterator auf das nächste Element in der Warteschlange setzen.
  
  Beide in der Aufgabenstellung gegebenen Implementierungsvarianten sind korrekt. Die erste Variante ist jedoch prägnanter, da sie direkt auf die Methodenaufrufe verzichtet und die Attribute direkt manipuliert.
      - **code_variante1:**
  ```java
  public Job next() {
      Job current = this.next.getJob();
      this.next = this.next.getNext();
      return current;
  }
  ```
      - **code_variante2:**
  ```java
  public Job next() {
      Job current = this.next.getJob();
      Elem e = this.next.getNext();
      this.setNext(e);
      return current;
  }
  ```
- **Theoretischer Bezug:** 
  - Die Aufgabe bezieht sich auf das [[Iterator_Pattern|Iterator-Muster]], das eine einheitliche Schnittstelle zum Durchlaufen von Aggregatobjekten (hier: [[Warteschlange|Warteschlangen]]) bereitstellt.
  - Das Sequenzdiagramm veranschaulicht die [[Dynamische_Modellierung|dynamische Modellierung]] von Objektinteraktionen in der UML.
  - Die Implementierung nutzt eine [[Verkettete_Liste|verkettete Liste]] zur Speicherung der Elemente in der Warteschlange.
  - Die Methode `next()` muss das [[Null_Objekt_Pattern|Null-Objekt-Problem]] berücksichtigen (z. B. durch vorherigen Aufruf von `hasNext()`).
- **Stolpersteine / Fehlerquellen:** 
  - Vergessen, den Iterator im Konstruktor zu initialisieren, führt zu einer `NullPointerException` beim ersten Aufruf von `next()`.
  - Die Methode `next()` darf nicht einfach `this.next.getNext()` aufrufen, ohne das aktuelle `Job`-Objekt zu speichern, da es sonst verloren geht.
  - Im Sequenzdiagramm wird oft fälschlicherweise die `FiFo`-Klasse als direkter Teilnehmer dargestellt, obwohl der Iterator bereits eine Referenz auf das erste Element hält.
  - Verwechslung von `next()` (Iterator-Methode) und `getNext()` (Methode der Klasse `Elem`) kann zu logischen Fehlern führen.
  - Fehlende Prüfung auf `null` (z. B. durch `hasNext()`) kann zu Laufzeitfehlern führen, wenn der Iterator am Ende der Warteschlange angelangt ist.
