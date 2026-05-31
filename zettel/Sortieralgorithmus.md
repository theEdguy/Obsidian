---
id: f86aeddb-4882-4407-9786-db1bd3620b8c
title: "Sortieralgorithmus"
date: 2026-05-31
tags:
  - software_engineering
  - algorithmen
  - datenstrukturen
  - entwurfsmuster
  - uml
  - performance
  - draft
source: "Klausur_Referenz"
---

# [[Sortieralgorithmus]]

- **Kernkonzept:** Ein [[Sortieralgorithmus]] ist ein [[Algorithmus]], der eine gegebene Menge von Elementen (z. B. Zahlen, Strings oder komplexe Objekte) nach bestimmten Kriterien in eine definierte Reihenfolge bringt. Die Reihenfolge kann aufsteigend, absteigend oder benutzerdefiniert sein und basiert auf einem [[Vergleichsoperator]] oder einer [[Sortierfunktion]]. Sortieralgorithmen sind grundlegende Bausteine der Informatik und werden in nahezu allen Bereichen der Softwareentwicklung eingesetzt, von Datenbanken bis hin zu Benutzeroberflächen.
- **Nutzen & Zweck:** Sortieralgorithmen dienen primär der effizienten Organisation von Daten, um folgende Ziele zu erreichen:

1. **Schnellere Suche**: Sortierte Daten ermöglichen den Einsatz effizienter [[Suchalgorithmen]] wie [[Binäre_Suche]], die in logarithmischer Zeit (O(log n)) arbeiten.
2. **Datenanalyse**: Sortierte Daten vereinfachen statistische Auswertungen, Aggregationen oder die Erkennung von Mustern.
3. **Optimierung von Prozessen**: In [[Algorithmen]] wie [[Dijkstra_Algorithmus]] oder [[Greedy_Algorithmen]] ist eine sortierte Eingabe oft Voraussetzung für korrekte Ergebnisse.
4. **Benutzerfreundlichkeit**: Sortierte Listen (z. B. in Tabellen oder Dropdown-Menüs) verbessern die Usability von Anwendungen.
5. **Datenkompression**: Sortierte Daten lassen sich oft effizienter komprimieren (z. B. durch [[Run-Length_Encoding]]).

Die Wahl des passenden Sortieralgorithmus hängt von Faktoren wie Datenmenge, Speicherplatz, Stabilität (Erhalt der ursprünglichen Reihenfolge gleicher Elemente) und Zeitkomplexität ab.
- **Abgrenzung & Grenzen:** Sortieralgorithmen lassen sich nach verschiedenen Kriterien klassifizieren und abgrenzen:

1. **Zeitkomplexität**: 
   - **O(n²)**: Einfache Algorithmen wie [[Bubble_Sort]], [[Insertion_Sort]] oder [[Selection_Sort]] eignen sich nur für kleine Datenmengen.
   - **O(n log n)**: Effiziente Algorithmen wie [[Merge_Sort]], [[Quick_Sort]] oder [[Heap_Sort]] skalieren gut für große Datenmengen.
   - **O(n)**: Lineare Algorithmen wie [[Counting_Sort]], [[Radix_Sort]] oder [[Bucket_Sort]] setzen spezifische Voraussetzungen (z. B. begrenzte Schlüsselwerte) voraus.

2. **Speicherplatz**: 
   - **In-place**: Algorithmen wie [[Quick_Sort]] oder [[Heap_Sort]] sortieren die Daten im vorhandenen Speicherbereich (O(1) zusätzlicher Speicher).
   - **Out-of-place**: Algorithmen wie [[Merge_Sort]] benötigen zusätzlichen Speicher (O(n)).

3. **Stabilität**: 
   - **Stabile Algorithmen** (z. B. [[Merge_Sort]], [[Insertion_Sort]]) erhalten die relative Reihenfolge gleicher Elemente.
   - **Instabile Algorithmen** (z. B. [[Quick_Sort]], [[Heap_Sort]]) garantieren dies nicht.

4. **Vergleichsbasiert vs. Nicht-vergleichsbasiert**: 
   - Vergleichsbasierte Algorithmen (z. B. [[Quick_Sort]]) nutzen [[Vergleichsoperatoren]] und haben eine theoretische Untergrenze von O(n log n).
   - Nicht-vergleichsbasierte Algorithmen (z. B. [[Counting_Sort]]) nutzen spezifische Eigenschaften der Daten und können diese Grenze unterschreiten.

**Typische Stolpersteine**:
- **Performance-Fallen**: Die Wahl eines ungeeigneten Algorithmus (z. B. [[Bubble_Sort]] für große Datenmengen) führt zu schlechter Performance.
- **Stabilität**: Bei mehrstufigen Sortierungen (z. B. erst nach Name, dann nach Alter) ist Stabilität entscheidend.
- **Datenverteilung**: Algorithmen wie [[Quick_Sort]] können bei bereits sortierten Daten im Worst-Case O(n²) erreichen.
- **Parallelisierung**: Nicht alle Algorithmen lassen sich effizient parallelisieren (z. B. [[Merge_Sort]] ist besser geeignet als [[Quick_Sort]]).
- **Beispiel / Code:** {'uml_klassendiagramm': {'beschreibung': 'Das folgende [[Klassendiagramm]] veranschaulicht eine abstrakte Struktur für Sortieralgorithmen unter Verwendung des [[Strategie_Patterns]]. Dies ermöglicht die flexible Austauschbarkeit von Sortierstrategien zur Laufzeit.', 'mermaid_syntax': 'classDiagram\n    class Sortieralgorithmus {\n        <<interface>>\n        +sortiere(daten: List~T~): List~T~\n    }\n\n    class BubbleSort {\n        +sortiere(daten: List~T~): List~T~\n    }\n\n    class QuickSort {\n        +sortiere(daten: List~T~): List~T~\n    }\n\n    class MergeSort {\n        +sortiere(daten: List~T~): List~T~\n    }\n\n    class Sortierkontext {\n        -strategie: Sortieralgorithmus\n        +setSortierstrategie(strategie: Sortieralgorithmus)\n        +führeSortierungAus(daten: List~T~): List~T~\n    }\n\n    Sortieralgorithmus <|-- BubbleSort\n    Sortieralgorithmus <|-- QuickSort\n    Sortieralgorithmus <|-- MergeSort\n    Sortierkontext --> Sortieralgorithmus: nutzt\n'}, 'java_beispiel': {'beschreibung': 'Implementierung des [[Strategie_Patterns]] für Sortieralgorithmen in Java. Der `Sortierkontext` delegiert die Sortierung an eine konkrete Strategie (z. B. `QuickSort`).', 'code': 'public interface Sortieralgorithmus<T extends Comparable<T>> {\n    List<T> sortiere(List<T> daten);\n}\n\npublic class QuickSort<T extends Comparable<T>> implements Sortieralgorithmus<T> {\n    @Override\n    public List<T> sortiere(List<T> daten) {\n        if (daten.size() <= 1) {\n            return daten;\n        }\n        T pivot = daten.get(daten.size() / 2);\n        List<T> kleiner = new ArrayList<>();\n        List<T> gleich = new ArrayList<>();\n        List<T> größer = new ArrayList<>();\n\n        for (T element : daten) {\n            int vergleich = element.compareTo(pivot);\n            if (vergleich < 0) {\n                kleiner.add(element);\n            } else if (vergleich == 0) {\n                gleich.add(element);\n            } else {\n                größer.add(element);\n            }\n        }\n\n        List<T> sortiert = new ArrayList<>();\n        sortiert.addAll(sortiere(kleiner));\n        sortiert.addAll(gleich);\n        sortiert.addAll(sortiere(größer));\n        return sortiert;\n    }\n}\n\npublic class Sortierkontext<T extends Comparable<T>> {\n    private Sortieralgorithmus<T> strategie;\n\n    public void setSortierstrategie(Sortieralgorithmus<T> strategie) {\n        this.strategie = strategie;\n    }\n\n    public List<T> führeSortierungAus(List<T> daten) {\n        return strategie.sortiere(daten);\n    }\n}\n\n// Verwendung:\nSortierkontext<Integer> kontext = new Sortierkontext<>();\nkontext.setSortierstrategie(new QuickSort<>());\nList<Integer> sortierteDaten = kontext.führeSortierungAus(Arrays.asList(5, 2, 9, 1, 5));\nSystem.out.println(sortierteDaten); // Ausgabe: [1, 2, 5, 5, 9]'}}
