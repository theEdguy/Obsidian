---
id: 9486b802-6992-4150-9d04-6f15a7188715
title: "Navigierbarkeit"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Navigierbarkeit]]

- **Kernkonzept:** Die [[Navigierbarkeit]] definiert, in welche Richtung eine [[Binäre_Assoziation|binäre Assoziation]] traversiert werden kann, d. h., welche [[Klasse]] auf die [[Instanz|Instanzen]] der anderen [[Klasse]] zugreifen darf.
- **Nutzen & Zweck:** Sie reduziert die [[Kopplung]] zwischen [[Klasse|Klassen]], indem sie den Zugriff auf [[Beziehung|Beziehungen]] einschränkt und die [[Kapselung]] von [[Datenstruktur|Datenstrukturen]] fördert.
- **Abgrenzung & Grenzen:** Nicht sinnvoll, wenn bidirektionale Zugriffe erforderlich sind oder wenn die [[Beziehung]] symmetrisch ist. In solchen Fällen sollte eine bidirektionale [[Assoziation]] oder eine [[Assoziationsklasse]] verwendet werden.
- **Beispiel / Code:** ```java
class Mitglied {
    private List<Sport> ausgeuebteSportarten;
    // Nur Mitglied kann auf Sport zugreifen, nicht umgekehrt
}
```
