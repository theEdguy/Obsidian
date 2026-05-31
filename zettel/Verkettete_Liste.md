---
id: d1a22dfc-8c94-4ba2-b830-b4e9400ff339
title: "Verkettete_Liste"
date: 2026-05-31
tags:
  - software_engineering
  - datenstrukturen
  - algorithmen
  - java
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Verkettete_Liste]]

- **Kernkonzept:** Eine [[Dynamische_Datenstruktur]], bei der Elemente (Knoten) sequenziell durch Zeiger (Referenzen) miteinander verbunden sind. Jeder Knoten enthält typischerweise einen Datenwert und mindestens eine Referenz auf den nächsten Knoten (einfach verkettet) oder zusätzlich auf den vorherigen Knoten (doppelt verkettet). Im Gegensatz zu [[Arrays]] erfolgt der Zugriff nicht über Indizes, sondern durch Traversieren der Knotenfolge. Die Liste kann flexibel wachsen oder schrumpfen, da Speicher dynamisch allokiert wird.
- **Nutzen & Zweck:** Verkettete Listen eignen sich besonders für Szenarien mit häufigen Einfüge- oder Löschoperationen an beliebigen Positionen, da diese in O(1) Zeit (bei bekanntem Knoten) durchgeführt werden können. Sie vermeiden die Speicherverschwendung statischer Strukturen wie [[Arrays]] und ermöglichen effiziente Implementierungen von [[Abstrakten_Datentypen]] wie [[Stapel]] (LIFO) oder [[Warteschlange]] (FIFO). Zudem dienen sie als Grundlage für komplexere Strukturen wie [[Hash_Tabellen]] (für Kollisionsauflösung) oder [[Graphen]] (Adjazenzlisten).
- **Abgrenzung & Grenzen:** Im Vergleich zu [[Arrays]] ist der wahlfreie Zugriff auf Elemente in O(n) Zeit ineffizient, da die Liste sequenziell traversiert werden muss. Der Speicherbedarf ist höher, da zusätzlich zu den Daten Referenzen gespeichert werden. Typische Stolpersteine sind: (1) **Zeigerfehler** (z. B. verlorene Referenzen beim Löschen), (2) **Zyklen** (unbeabsichtigte Schleifen in der Liste), (3) **Cache-Ineffizienz** (keine räumliche Lokalität der Daten). Doppelt verkettete Listen ermöglichen bidirektionales Traversieren, erhöhen aber den Verwaltungsaufwand. Für sortierte Daten sind [[Suchbäume]] oft besser geeignet.
- **Beispiel / Code:** {'beschreibung': 'Einfach verkettete Liste in Java mit Grundoperationen (Einfügen, Löschen, Traversieren). Die UML-Klassendarstellung zeigt die Struktur mit Knoten und Liste.', 'java_code': 'public class VerketteteListe<T> {\n    private static class Knoten<T> {\n        T daten;\n        Knoten<T> naechster;\n\n        Knoten(T daten) {\n            this.daten = daten;\n            this.naechster = null;\n        }\n    }\n\n    private Knoten<T> kopf;\n    \n    public void einfuegenAmAnfang(T daten) {\n        Knoten<T> neuerKnoten = new Knoten<>(daten);\n        neuerKnoten.naechster = kopf;\n        kopf = neuerKnoten;\n    }\n\n    public void loeschen(T daten) {\n        if (kopf == null) return;\n        if (kopf.daten.equals(daten)) {\n            kopf = kopf.naechster;\n            return;\n        }\n        Knoten<T> aktuell = kopf;\n        while (aktuell.naechster != null) {\n            if (aktuell.naechster.daten.equals(daten)) {\n                aktuell.naechster = aktuell.naechster.naechster;\n                return;\n            }\n            aktuell = aktuell.naechster;\n        }\n    }\n\n    public void traversieren() {\n        Knoten<T> aktuell = kopf;\n        while (aktuell != null) {\n            System.out.print(aktuell.daten + " -> ");\n            aktuell = aktuell.naechster;\n        }\n        System.out.println("null");\n    }\n}', 'uml_klassendiagramm': 'classDiagram\n    class VerketteteListe~T~ {\n        -kopf: Knoten~T~\n        +einfuegenAmAnfang(daten: T): void\n        +loeschen(daten: T): void\n        +traversieren(): void\n    }\n    \n    class Knoten~T~ {\n        +daten: T\n        +naechster: Knoten~T~\n        +Knoten(daten: T)\n    }\n    \n    VerketteteListe "1" *-- "0..*" Knoten : enthält\n    Knoten "1" --> "0..1" Knoten : verweist auf'}
