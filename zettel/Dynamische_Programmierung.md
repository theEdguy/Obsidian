---
id: 9168f587-324f-4d08-b377-f59fb4a040a2
title: "Dynamische_Programmierung"
date: 2026-05-31
tags:
  - software_engineering
  - algorithmen
  - optimierung
  - rekursion
  - memoization
  - zeitkomplexität
  - draft
source: "Klausur_Referenz"
---

# [[Dynamische_Programmierung]]

- **Kernkonzept:** Dynamische_Programmierung (DP) ist ein algorithmisches Paradigma zur Lösung komplexer Probleme durch Zerlegung in überlappende Teilprobleme. Dabei werden Zwischenergebnisse systematisch gespeichert (z. B. in Tabellen oder Arrays), um redundante Berechnungen zu vermeiden. Dies basiert auf den Prinzipien der [[Optimalitätsstruktur]] und [[Überlappende_Teilprobleme]]. DP eignet sich besonders für Probleme mit rekursiver Struktur, bei denen naive Rekursion zu exponentieller Zeitkomplexität führen würde.
- **Nutzen & Zweck:** DP wird eingesetzt, um die Effizienz von Algorithmen drastisch zu verbessern, insbesondere bei Problemen mit hoher Zeitkomplexität (z. B. O(2^n) → O(n)). Typische Anwendungsfälle sind:
- Optimierungsprobleme (z. B. [[Rucksackproblem]], kürzeste Pfade in Graphen wie [[Dijkstra_Algorithmus]]).
- Sequenzvergleiche (z. B. [[Editierdistanz]]).
- Kombinatorische Probleme (z. B. Fibonacci-Folge, Binomialkoeffizienten).

Vorteile:
- Reduktion der Zeitkomplexität durch Memoization oder Tabellierung.
- Einfache Implementierung durch iterative oder rekursive Ansätze mit Zwischenspeicherung.
- **Abgrenzung & Grenzen:** DP ist **nicht** geeignet für:
- Probleme ohne überlappende Teilprobleme (z. B. [[Divide_and_Conquer]]-Algorithmen wie [[Quicksort]]).
- Probleme mit nicht-optimaler Teilstruktur (z. B. Greedy-Algorithmen wie [[Huffman_Kodierung]]).

Stolpersteine:
- Hoher Speicherbedarf bei Tabellierung (Trade-off zwischen Zeit und Speicher).
- Komplexität der Problemzerlegung (korrekte Definition der Teilprobleme ist entscheidend).
- Nicht alle rekursiven Probleme lassen sich mit DP optimieren (z. B. wenn Teilprobleme nicht überlappen).
- **Beispiel / Code:** {'beschreibung': 'Berechnung der n-ten Fibonacci-Zahl mit DP (iterativ vs. rekursiv mit Memoization).', 'java_memoization': 'import java.util.HashMap;\nimport java.util.Map;\n\npublic class Fibonacci {\n    private static Map<Integer, Long> memo = new HashMap<>();\n    \n    public static long fibMemo(int n) {\n        if (n <= 1) return n;\n        if (memo.containsKey(n)) return memo.get(n);\n        long result = fibMemo(n - 1) + fibMemo(n - 2);\n        memo.put(n, result);\n        return result;\n    }\n    \n    public static long fibIterativ(int n) {\n        if (n <= 1) return n;\n        long a = 0, b = 1, c;\n        for (int i = 2; i <= n; i++) {\n            c = a + b;\n            a = b;\n            b = c;\n        }\n        return b;\n    }\n}', 'uml_skizze': '```mermaid\nflowchart TD\n    A[Problem: fib(n)] --> B{n <= 1?}\n    B -->|Ja| C[Rückgabe n]\n    B -->|Nein| D[Prüfe Cache]\n    D -->|Treffer| E[Rückgabe gespeichertes Ergebnis]\n    D -->|Kein Treffer| F[Berechne fib(n-1) + fib(n-2)]\n    F --> G[Speichere Ergebnis in Cache]\n    G --> H[Rückgabe Ergebnis]\n```'}
