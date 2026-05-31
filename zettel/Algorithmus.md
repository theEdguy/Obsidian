---
id: a5574ab3-746e-4128-895f-8c62b74e99b2
title: "Algorithmus"
date: 2026-05-31
tags:
  - software_engineering
  - datenstrukturen
  - komplexitätsanalyse
  - entwurfsmuster
  - algorithmen_und_datenstrukturen
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Algorithmus]]

- **Kernkonzept:** Ein [[Algorithmus]] ist eine endliche, deterministische und präzise formulierte Handlungsvorschrift zur Lösung eines Problems oder einer Klasse von Problemen. Er besteht aus einer Folge von klar definierten Schritten, die Eingabedaten verarbeiten und in eine definierte Ausgabe überführen. Algorithmen bilden die Grundlage für die [[Implementierung]] von [[Softwarekomponenten]] und sind unabhängig von einer spezifischen [[Programmiersprache]] oder Hardware. Sie müssen terminieren (d. h. nach endlich vielen Schritten abbrechen) und korrekt sein, um die gewünschte Lösung zu liefern.
- **Nutzen & Zweck:** Algorithmen dienen der strukturierten Problemlösung in der [[Softwareentwicklung]] und ermöglichen:
- Effiziente Verarbeitung von Daten (z. B. durch [[Sortieralgorithmen]] wie [[QuickSort]] oder [[MergeSort]]).
- Automatisierung repetitiver Aufgaben (z. B. [[Suchalgorithmen]] wie [[Binäre_Suche]]).
- Grundlage für [[Datenstrukturen]] (z. B. [[Bäume]], [[Graphen]]) und komplexe Systeme (z. B. [[Künstliche_Intelligenz]], [[Datenbanken]]).
- Vergleichbarkeit von Lösungsansätzen durch [[Komplexitätsanalyse]] (z. B. [[O-Notation]]).
- Wiederverwendbarkeit und Modularität im [[Software_Design]], da Algorithmen oft als [[Funktionen]] oder [[Methoden]] gekapselt werden.
- **Abgrenzung & Grenzen:** 1. **Kein Algorithmus**: Eine unendliche Schleife oder eine nicht-terminierende Vorschrift (z. B. "Wiederhole, bis die Lösung gefunden ist") ist kein Algorithmus.
2. **Abgrenzung zu [[Heuristiken]]**: Algorithmen garantieren eine korrekte Lösung, während Heuristiken Näherungslösungen für Probleme liefern, die exakt nicht oder nur mit hohem Aufwand lösbar sind (z. B. [[Genetische_Algorithmen]]).
3. **Abgrenzung zu [[Pseudocode]]**: Pseudocode ist eine informelle Notation zur Beschreibung von Algorithmen, kein ausführbarer Code.
4. **Stolpersteine**:
   - **Effizienz vs. Korrektheit**: Ein Algorithmus kann korrekt, aber ineffizient sein (z. B. [[BubbleSort]] mit O(n²)).
   - **Eingabeabhängigkeit**: Manche Algorithmen (z. B. [[QuickSort]]) verhalten sich bei bestimmten Eingaben (z. B. bereits sortierte Daten) suboptimal.
   - **Implementierungsfehler**: Selbst korrekte Algorithmen können durch fehlerhafte [[Implementierung]] (z. B. Off-by-One-Fehler) falsche Ergebnisse liefern.
   - **Anforderungsanalyse**: Ein Algorithmus löst nur das Problem, für das er entworfen wurde – falsche [[Requirements]] führen zu nutzlosen Lösungen (vgl. [[Codieren_und_Verbessern_naiver_Ansatz]]).
- **Beispiel / Code:** {'beschreibung': 'Beispiel eines einfachen Algorithmus zur Berechnung der Fakultät einer Zahl (n!) in Java. Der Algorithmus zeigt die Grundprinzipien: Eingabe (n), Verarbeitung (Schleife oder Rekursion) und Ausgabe (Ergebnis).', 'code': 'public class Fakultät {\n    // Iterative Implementierung des Algorithmus\n    public static long berechneFakultät(int n) {\n        if (n < 0) {\n            throw new IllegalArgumentException("Eingabe muss nicht-negativ sein.");\n        }\n        long ergebnis = 1;\n        for (int i = 2; i <= n; i++) {\n            ergebnis *= i;\n        }\n        return ergebnis;\n    }\n    \n    // Rekursive Implementierung (alternativer Algorithmus)\n    public static long berechneFakultätRekursiv(int n) {\n        if (n < 0) {\n            throw new IllegalArgumentException("Eingabe muss nicht-negativ sein.");\n        }\n        if (n == 0 || n == 1) {\n            return 1;\n        }\n        return n * berechneFakultätRekursiv(n - 1);\n    }\n}', 'uml_diagramm': {'typ': 'Aktivitätsdiagramm', 'beschreibung': 'Veranschaulicht den iterativen Algorithmus zur Fakultätsberechnung als UML-Aktivitätsdiagramm (textuell beschrieben):', 'mermaid_syntax': 'graph TD\n    A[Start] --> B{n < 0?}\n    B -->|Ja| C[Fehler werfen]\n    B -->|Nein| D[Initialisiere ergebnis = 1, i = 2]\n    D --> E{i <= n?}\n    E -->|Ja| F[ergebnis = ergebnis * i]\n    F --> G[i = i + 1]\n    G --> E\n    E -->|Nein| H[Gib ergebnis zurück]\n    H --> I[Ende]'}}
