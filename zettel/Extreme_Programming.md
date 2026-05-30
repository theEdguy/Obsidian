---
id: 5de14f28-0a18-485b-9334-e3c72dc74991
title: "Extreme_Programming"
date: 2026-05-30
tags:
  - software_engineering
  - agile_methoden
  - test_driven_development
  - pair_programming
  - kontinuierliche_integration
  - refactoring
  - user_stories
  - softwareentwicklungsprozess
  - draft
source: "Klausur_Referenz"
---

# [[Extreme_Programming]]

- **Kernkonzept:** Extreme Programming (XP) ist ein agiles [[Softwareentwicklungsprozess]]-Modell, das auf enge Zusammenarbeit, schnelle Feedbackschleifen und kontinuierliche Verbesserung setzt. Es betont technische Exzellenz durch Praktiken wie [[Test_Driven_Development]], [[Pair_Programming]], kontinuierliche [[Integration]] und [[Refactoring]]. XP entstand als Reaktion auf schwerfällige, dokumentenlastige Prozesse und orientiert sich am [[Spiralmodell]], indem es Risiken durch frühe und häufige Iterationen minimiert. Kernprinzipien sind Kommunikation, Einfachheit, Feedback, Mut und Respekt.
- **Nutzen & Zweck:** XP wird eingesetzt, um Software in dynamischen Umgebungen mit unklaren oder sich ändernden Anforderungen effizient zu entwickeln. Vorteile umfassen:
- **Schnelle Anpassungsfähigkeit**: Kurze [[Iteration|Iterationen]] (1–4 Wochen) ermöglichen rasche Reaktion auf Änderungen.
- **Hohe Codequalität**: Durch [[Test_Driven_Development]] und [[Pair_Programming]] entstehen weniger Fehler und besser wartbarer Code.
- **Risikominimierung**: Kontinuierliche [[Integration]] und frühes Feedback reduzieren technische Schulden und Projektausfallrisiken.
- **Kundenorientierung**: Der Kunde ist Teil des Teams (z. B. durch [[User_Stories]] und regelmäßige Reviews).
- **Nachhaltiges Tempo**: XP vermeidet Überstunden durch realistische Planung und Priorisierung.
- **Abgrenzung & Grenzen:** XP unterscheidet sich von anderen agilen Methoden wie [[Scrum]] durch seinen starken Fokus auf technische Praktiken (z. B. [[Test_Driven_Development]]). Grenzen und Stolpersteine:
- **Kulturelle Hürden**: [[Pair_Programming]] und offene Kommunikation erfordern Vertrauen und Akzeptanz im Team.
- **Skalierbarkeit**: XP eignet sich primär für kleine bis mittelgroße Teams (ideal: 5–12 Entwickler). Bei größeren Projekten müssen zusätzliche Strukturen (z. B. [[SAFe]] oder [[LeSS]]) ergänzt werden.
- **Dokumentation**: XP priorisiert funktionierenden Code über ausführliche Dokumentation, was bei regulatorischen Anforderungen (z. B. Medizinsoftware) problematisch sein kann.
- **Kundenverfügbarkeit**: Der Erfolg hängt stark von der aktiven Beteiligung des Kunden ab – fehlende Verfügbarkeit führt zu Verzögerungen.
- **Technische Schulden**: Ohne diszipliniertes [[Refactoring]] können kurzfristige Lösungen langfristig zu Wartungsproblemen führen.
- **Beispiel / Code:** {'beschreibung': 'Beispiel für [[Test_Driven_Development]] (TDD) in XP: Ein einfacher Taschenrechner mit Addition. Der Ablauf folgt dem TDD-Zyklus: *Red* (Test schreiben) → *Green* (Code implementieren) → *Refactor* (Code verbessern).', 'java_test': '// 1. Red: Test schreiben (fällt zunächst fehl)\nimport org.junit.jupiter.api.Test;\nimport static org.junit.jupiter.api.Assertions.*;\n\nclass CalculatorTest {\n    @Test\n    void testAdd() {\n        Calculator calculator = new Calculator();\n        assertEquals(5, calculator.add(2, 3));\n    }\n}\n\n// 2. Green: Minimale Implementierung\nclass Calculator {\n    public int add(int a, int b) {\n        return a + b;\n    }\n}\n\n// 3. Refactor: Code verbessern (hier trivial, aber z. B. Exception-Handling ergänzen)\nclass Calculator {\n    public int add(int a, int b) {\n        if (a < 0 || b < 0) {\n            throw new IllegalArgumentException("Negative Zahlen nicht erlaubt");\n        }\n        return a + b;\n    }\n}', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Calculator {\n        +add(int a, int b) int\n    }\n    class CalculatorTest {\n        +testAdd() void\n    }\n    CalculatorTest --> Calculator : testet\n```'}
