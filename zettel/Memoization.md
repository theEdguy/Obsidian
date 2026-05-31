---
id: 5e83706a-4232-48ef-95a8-97f13c4e844c
title: "Memoization"
date: 2026-05-31
tags:
  - software_engineering
  - algorithmen
  - optimierung
  - dynamische_programmierung
  - caching
  - performance
  - draft
source: "Klausur_Referenz"
---

# [[Memoization]]

- **Kernkonzept:** Memoization ist eine Optimierungstechnik in der Softwareentwicklung, bei der die Ergebnisse teurer Funktionsaufrufe zwischengespeichert werden, um wiederholte Berechnungen derselben Eingabeparameter zu vermeiden. Sie wird häufig in [[Rekursion]] und [[Dynamische_Programmierung]] eingesetzt, um die Performance von Algorithmen signifikant zu verbessern, indem redundante Berechnungen eliminiert werden.
- **Nutzen & Zweck:** Memoization dient primär der Effizienzsteigerung von Programmen, insbesondere bei Funktionen mit hohen Rechenkosten oder wiederholten Aufrufen identischer Parameter. Typische Anwendungsfälle sind:
- Optimierung rekursiver Algorithmen (z. B. Fibonacci-Folge, [[Backtracking]]).
- Reduktion der Zeitkomplexität von O(2^n) auf O(n) in vielen Fällen.
- Verbesserung der Antwortzeiten in [[Caching]]-Strategien oder [[API]]-Aufrufen.

Der Vorteil liegt in der einfachen Implementierung (oft durch [[Dekorator]]-Muster oder Hash-Tabellen) bei gleichzeitig hohem Performance-Gewinn.
- **Abgrenzung & Grenzen:** Memoization ist **kein Allheilmittel** und hat klare Grenzen:
- **Speicherbedarf**: Die Zwischenspeicherung kann zu hohem [[Speicherverbrauch]] führen, besonders bei großen Eingabebereichen oder vielen unterschiedlichen Parametern.
- **Seiteneffekte**: Funktionen mit [[Seiteneffekte|Seiteneffekten]] (z. B. Datenbankzugriffe) sind ungeeignet, da Memoization reine Funktionen voraussetzt.
- **Dynamische Parameter**: Bei häufig wechselnden Eingabewerten (z. B. Zeitstempel) ist der Nutzen gering.
- **Thread-Safety**: In [[Multithreading]]-Umgebungen muss der Cache synchronisiert werden, um Race Conditions zu vermeiden.

Abzugrenzen ist Memoization von [[Tabellierung]] (Bottom-Up-Ansatz in [[Dynamische_Programmierung]]) und generischem [[Caching]], das oft auf Systemebene (z. B. Datenbank-Caches) eingesetzt wird.
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer memoisierten Fibonacci-Funktion in Java (mit HashMap als Cache):', 'code': 'import java.util.HashMap;\nimport java.util.Map;\n\npublic class Fibonacci {\n    private static Map<Integer, Long> cache = new HashMap<>();\n    \n    public static long fibonacci(int n) {\n        if (n <= 1) return n;\n        \n        // Prüfe, ob Ergebnis bereits im Cache liegt\n        if (cache.containsKey(n)) {\n            return cache.get(n);\n        }\n        \n        // Berechne und speichere das Ergebnis\n        long result = fibonacci(n - 1) + fibonacci(n - 2);\n        cache.put(n, result);\n        return result;\n    }\n    \n    public static void main(String[] args) {\n        System.out.println(fibonacci(50)); // Ohne Memoization: extrem langsam\n    }\n}', 'uml_diagramm': {'beschreibung': 'Aktivitätsdiagramm zur Veranschaulichung des memoisierten Ablaufs (vereinfacht):', 'mermaid': 'flowchart TD\n    A[Start: fib(n)] --> B{n <= 1?}\n    B -->|Ja| C[Return n]\n    B -->|Nein| D{Cache enthält n?}\n    D -->|Ja| E[Return cache[n]]\n    D -->|Nein| F[Berechne fib(n-1) + fib(n-2)]\n    F --> G[Speichere Ergebnis in Cache]\n    G --> H[Return Ergebnis]'}}
