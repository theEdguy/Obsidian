---
id: 62c8243d-40c7-4499-ad9f-365444b3319e
title: "Detailliertes_Sequenzdiagramm"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - softwaremodellierung
  - algorithmen
  - systemdesign
  - interaktionsdiagramme
  - draft
source: "Klausur_Referenz"
---

# [[Detailliertes_Sequenzdiagramm]]

- **Kernkonzept:** Ein **detailliertes_Sequenzdiagramm** ist eine spezifische Ausprägung eines [[Sequenzdiagramms]] in der [[UML]], das den zeitlichen Ablauf von Nachrichten und Interaktionen zwischen Objekten oder [[Akteuren]] in einem System präzise und schrittweise darstellt. Es visualisiert nicht nur die Reihenfolge der Nachrichten, sondern auch deren Parameter, Rückgabewerte, Schleifen, Bedingungen (z. B. `alt`, `opt`, `loop`) und interne Aufrufe (z. B. Selbstdelegation). Im Gegensatz zu einem groben Sequenzdiagramm werden hier auch technische Details wie Lebenslinien (`lifelines`), Aktivierungsbalken (`execution specifications`) und Synchronisationspunkte (z. B. `sync`/`async`) explizit modelliert, um komplexe Algorithmen oder Systemverhalten nachvollziehbar zu dokumentieren.
- **Nutzen & Zweck:** Detaillierte_Sequenzdiagramme dienen primär der **Verfeinerung von Systemdesigns** und der **Kommunikation zwischen Entwicklern, Architekten und Testern**. Sie werden eingesetzt, um:
- **Algorithmen** (z. B. rekursive Aufrufe wie bei der Fibonacci-Berechnung) oder **Protokolle** (z. B. Authentifizierungsabläufe) zu spezifizieren.
- **Fehlerquellen** in der Interaktion zwischen Komponenten zu identifizieren (z. B. Race Conditions oder Deadlocks).
- **Testfälle** abzuleiten, indem sie die erwarteten Nachrichtenflüsse und Zustandsänderungen vorgeben.
- **Legacy-Code** oder undokumentierte Systeme zu analysieren, indem sie das tatsächliche Laufzeitverhalten rekonstruieren.

Im Vergleich zu [[Klassendiagrammen]] oder [[Zustandsdiagrammen]] liegt der Fokus auf der **dynamischen Perspektive** und der **zeitlichen Abfolge**, nicht auf statischen Strukturen oder Zustandsübergängen.
- **Abgrenzung & Grenzen:** 1. **Komplexität vs. Lesbarkeit**: Detaillierte_Sequenzdiagramme können schnell unübersichtlich werden, wenn sie zu viele Objekte, verschachtelte Schleifen oder parallele Abläufe abbilden. Hier empfiehlt sich eine Aufteilung in Teilsequenzen oder die Verwendung von [[Referenzdiagrammen]] (`ref`).

2. **Statische vs. dynamische Aspekte**: Während ein [[Klassendiagramm]] die Struktur eines Systems zeigt, bildet ein Sequenzdiagramm nur einen **spezifischen Szenario-Ablauf** ab. Es ist nicht geeignet, um alle möglichen Interaktionen eines Systems darzustellen (hierfür eignen sich [[Kommunikationsdiagramme]] oder [[Aktivitätsdiagramme]] besser).

3. **Technische Grenzen**: 
   - **Nicht-deterministische Abläufe** (z. B. Thread-Scheduling) lassen sich nur schwer abbilden.
   - **Performance-Analysen** erfordern zusätzliche Werkzeuge (z. B. Profiler), da Sequenzdiagramme keine Zeitmessungen unterstützen.
   - **Implizite Annahmen**: Fehlende Details (z. B. Ausnahmebehandlung) können zu Missverständnissen führen. Hier hilft die Kombination mit [[Use_Case_Diagrammen]] oder [[Fehlerbäumen]].

4. **Werkzeugabhängigkeit**: Die Darstellung von Bedingungen (`alt`, `opt`) oder Schleifen (`loop`) ist nicht in allen UML-Tools einheitlich implementiert. Zudem unterstützen manche Tools keine dynamische Simulation der Diagramme.
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel zeigt ein detailliertes Sequenzdiagramm für die Berechnung der n-ten Fibonacci-Zahl unter Verwendung eines `FiboStore` (Cache). Das Diagramm modelliert rekursive Aufrufe, Bedingungen und die Interaktion mit dem Cache.', 'uml_mermaid': '```mermaid\nsequenceDiagram\n    participant Client as Client\n    participant Fibo as Fibonacci\n    participant Store as FiboStore\n\n    Client->>Fibo: calculate(n)\n    activate Fibo\n    \n    alt n <= 1\n        Fibo-->>Client: n\n    else\n        Fibo->>Store: get(n)\n        activate Store\n        Store-->>Fibo: value (null oder Zahl)\n        deactivate Store\n        \n        alt value != null\n            Fibo-->>Client: value\n        else\n            Fibo->>Fibo: calculate(n-1)\n            activate Fibo\n            Fibo-->>Fibo: fib_n1\n            deactivate Fibo\n            \n            Fibo->>Fibo: calculate(n-2)\n            activate Fibo\n            Fibo-->>Fibo: fib_n2\n            deactivate Fibo\n            \n            Fibo->>Store: set(n, fib_n1 + fib_n2)\n            activate Store\n            Store-->>Fibo: -\n            deactivate Store\n            \n            Fibo-->>Client: fib_n1 + fib_n2\n        end\n    end\n    deactivate Fibo\n```', 'hinweise': ['1. **Lebenslinien**: Jedes Objekt (`Client`, `Fibo`, `Store`) hat eine eigene Lebenslinie, die seine Existenz während der Interaktion darstellt.', '2. **Aktivierungsbalken**: Die blauen Balken zeigen, wann ein Objekt aktiv ist (z. B. während der Berechnung von `calculate`).', '3. **Bedingungen**: Das `alt`-Fragment modelliert die Fallunterscheidung für `n <= 1` und den Cache-Zugriff.', '4. **Rekursion**: Die Selbstaufrufe von `Fibo` zeigen die rekursive Berechnung von `fib(n-1)` und `fib(n-2)`.', '5. **Cache-Interaktion**: Der `FiboStore` wird genutzt, um bereits berechnete Werte zu speichern und wiederzuverwenden.']}
