---
id: 0df28ef9-5055-4915-85dc-98f306ae67a5
title: "Binaere_Suche"
date: 2026-05-31
tags:
  - software_engineering
  - algorithmen
  - datenstrukturen
  - suchverfahren
  - divide_and_conquer
  - draft
source: "Klausur_Referenz"
---

# [[Binaere_Suche]]

- **Kernkonzept:** Die [[Binaere_Suche]] ist ein effizientes [[Suchalgorithmus|Suchverfahren]], das auf sortierten Datenstrukturen (z. B. Arrays oder Listen) operiert. Sie reduziert die Problemgröße in jedem Schritt um die Hälfte, indem sie das mittlere Element des Suchbereichs mit dem gesuchten Wert vergleicht und basierend auf dem Ergebnis entweder die linke oder rechte Hälfte des Suchraums weiter untersucht. Dies setzt voraus, dass die Daten nach einem definierten Kriterium (z. B. numerisch oder lexikografisch) [[Sortieralgorithmus|sortiert]] sind.
- **Nutzen & Zweck:** Die [[Binaere_Suche]] wird eingesetzt, um die Zeitkomplexität von Suchoperationen von O(n) (wie bei der [[Lineare_Suche]]) auf O(log n) zu reduzieren. Sie eignet sich besonders für große, statische oder selten veränderte Datensätze, bei denen der Overhead des Sortierens vernachlässigbar ist. Typische Anwendungsfälle sind:
- Suche in Datenbankindizes,
- Implementierung von [[Lookup-Tabellen]] (z. B. in Compilern oder Netzwerkroutern),
- Algorithmen wie [[Divide_and_Conquer]] (z. B. in [[Quickselect]]).

Der Vorteil liegt in der Skalierbarkeit: Selbst bei Millionen von Einträgen sind nur wenige Vergleichsoperationen nötig.
- **Abgrenzung & Grenzen:** Die [[Binaere_Suche]] ist **nicht** anwendbar auf:
- Unsortierte Daten (hier muss zunächst ein [[Sortieralgorithmus]] angewendet werden),
- Dynamische Datenstrukturen mit häufigen Einfüge-/Löschoperationen (z. B. [[Linked_List]]), da das Sortieren nach jeder Änderung ineffizient wäre.

Stolpersteine:
- **Off-by-One-Fehler**: Falsche Berechnung der mittleren Position oder der Suchgrenzen führt zu Endlosschleifen oder falschen Ergebnissen.
- **Datenintegrität**: Die Sortierreihenfolge muss während der Suche erhalten bleiben.
- **Duplikate**: Bei mehrfach vorkommenden Werten ist die Rückgabe des ersten/letzten Vorkommens nicht trivial (erfordert Anpassungen).

Abgrenzung zu ähnlichen Konzepten:
- [[Interpolationssuche]]: Schätzt die Position des gesuchten Elements basierend auf einer Verteilung (effizienter bei gleichverteilten Daten, aber komplexer).
- [[Exponentielle_Suche]]: Kombiniert lineare und binäre Suche für unbekannte Datengrenzen (z. B. in unendlichen Streams).
- **Beispiel / Code:** {'beschreibung': 'Implementierung der binären Suche in Java für ein sortiertes Array von Prozessen nach ihrer Ausführungszeit (Beispiel aus der Aufgabe zur Klasse `ShortestJobFirst`). Das Sequenzdiagramm aus der Aufgabe würde die Interaktion zwischen `ShortestJobFirst` und dem Array zeigen, wobei die Methode `binarySearch` rekursiv oder iterativ die Suche durchführt.', 'code': {'sprache': 'java', 'inhalt': 'public class ShortestJobFirst {\n    private Process[] processes;\n\n    // Binäre Suche (iterativ)\n    public int binarySearch(int targetBurstTime) {\n        int left = 0;\n        int right = processes.length - 1;\n\n        while (left <= right) {\n            int mid = left + (right - left) / 2; // Verhindert Überlauf\n            int currentBurstTime = processes[mid].getBurstTime();\n\n            if (currentBurstTime == targetBurstTime) {\n                return mid; // Gefunden\n            } else if (currentBurstTime < targetBurstTime) {\n                left = mid + 1; // Suche in der rechten Hälfte\n            } else {\n                right = mid - 1; // Suche in der linken Hälfte\n            }\n        }\n        return -1; // Nicht gefunden\n    }\n\n    // Alternative: Rekursive Implementierung\n    public int binarySearchRecursive(int targetBurstTime, int left, int right) {\n        if (left > right) {\n            return -1;\n        }\n        int mid = left + (right - left) / 2;\n        int currentBurstTime = processes[mid].getBurstTime();\n\n        if (currentBurstTime == targetBurstTime) {\n            return mid;\n        } else if (currentBurstTime < targetBurstTime) {\n            return binarySearchRecursive(targetBurstTime, mid + 1, right);\n        } else {\n            return binarySearchRecursive(targetBurstTime, left, mid - 1);\n        }\n    }\n}'}, 'uml_beschreibung': {'typ': 'Mermaid-Klassendiagramm', 'inhalt': 'classDiagram\n    class ShortestJobFirst {\n        -processes: Process[]\n        +binarySearch(targetBurstTime: int): int\n        +binarySearchRecursive(targetBurstTime: int, left: int, right: int): int\n    }\n    class Process {\n        -burstTime: int\n        +getBurstTime(): int\n    }\n    ShortestJobFirst "1" *-- "*" Process : enthält\n\n    note for ShortestJobFirst "Voraussetzung: processes[] ist nach burstTime sortiert!"'}}
