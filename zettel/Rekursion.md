---
id: 7eb16037-6626-4d17-98a3-51f54ea62fea
title: "Rekursion"
date: 2026-05-30
tags:
  - software_engineering
  - algorithmen
  - datenstrukturen
  - funktionale_programmierung
  - dynamische_programmierung
  - draft
source: "Klausur_Referenz"
---

# [[Rekursion]]

- **Kernkonzept:** Rekursion ist ein fundamentales Programmierkonzept, bei dem eine Funktion sich selbst direkt oder indirekt aufruft, um ein Problem in kleinere, strukturell ähnliche Teilprobleme zu zerlegen. Die Lösung des Gesamtproblems ergibt sich durch die Kombination der Lösungen dieser Teilprobleme. Rekursion basiert auf einer [[Rekursive_Definition]], die einen Basisfall (Abbruchbedingung) und einen rekursiven Fall umfasst, um unendliche Aufrufe zu vermeiden.
- **Nutzen & Zweck:** Rekursion wird eingesetzt, um komplexe Probleme elegant und lesbar zu lösen, insbesondere wenn diese natürlicherweise in kleinere, gleichartige Teilprobleme zerlegbar sind. Typische Anwendungsfälle sind:
- Traversierung von [[Baumstruktur|Baumstrukturen]] (z. B. [[Tiefensuche]]),
- Berechnung mathematischer Folgen (z. B. Fibonacci-Zahlen),
- Divide-and-Conquer-Algorithmen (z. B. [[Quicksort]] oder [[Mergesort]]).

Vorteile sind die intuitive Modellierung rekursiver Problemstellungen und die Reduktion von Code-Komplexität. Nachteile können jedoch hoher Speicherbedarf (durch [[Aufrufstapel]]) oder ineffiziente Laufzeit sein, wenn Teilprobleme mehrfach berechnet werden (vgl. [[Dynamische_Programmierung]]).
- **Abgrenzung & Grenzen:** Rekursion grenzt sich von iterativen Lösungen (z. B. Schleifen) durch ihre deklarative Natur ab, ist jedoch nicht immer die effizienteste Wahl. Typische Stolpersteine sind:
- Fehlende oder falsche Abbruchbedingungen, die zu [[Stack_Overflow]] führen,
- Unnötige Neuberechnungen von Teilproblemen (z. B. bei Fibonacci), die durch [[Memoization]] oder [[Dynamische_Programmierung]] vermieden werden können,
- Hoher Speicherbedarf bei tiefen Rekursionen, der durch [[Endrekursion]] (Tail Recursion) optimiert werden kann (sofern vom Compiler unterstützt).

Rekursion ist besonders effektiv für Probleme mit [[Selbstähnlichkeit]], aber ungeeignet für lineare oder sequentielle Aufgaben, die effizienter iterativ gelöst werden.
- **Beispiel / Code:** {'beschreibung': 'Berechnung der Fibonacci-Zahlen mit Rekursion (naiv vs. optimiert mit Memoization).', 'code_naiv': {'sprache': 'Java', 'inhalt': 'public int fibonacci(int n) {\n    if (n <= 1) {\n        return n; // Basisfall\n    }\n    return fibonacci(n - 1) + fibonacci(n - 2); // Rekursiver Fall\n}'}, 'code_optimiert': {'sprache': 'Java', 'inhalt': 'import java.util.HashMap;\nimport java.util.Map;\n\npublic class Fibonacci {\n    private Map<Integer, Integer> memo = new HashMap<>();\n\n    public int fibonacci(int n) {\n        if (n <= 1) {\n            return n;\n        }\n        if (memo.containsKey(n)) {\n            return memo.get(n); // Zwischenergebnis nutzen\n        }\n        int result = fibonacci(n - 1) + fibonacci(n - 2);\n        memo.put(n, result); // Ergebnis speichern\n        return result;\n    }\n}'}, 'diagramm': {'typ': 'Mermaid', 'inhalt': 'graph TD\n    A[fib(4)] --> B[fib(3)]\n    A --> C[fib(2)]\n    B --> D[fib(2)]\n    B --> E[fib(1)]\n    C --> F[fib(1)]\n    C --> G[fib(0)]\n    D --> H[fib(1)]\n    D --> I[fib(0)]\n    \n    style A fill:#f9f,stroke:#333\n    style E fill:#9f9,stroke:#333\n    style F fill:#9f9,stroke:#333\n    style G fill:#9f9,stroke:#333\n    style H fill:#9f9,stroke:#333\n    style I fill:#9f9,stroke:#333'}}
