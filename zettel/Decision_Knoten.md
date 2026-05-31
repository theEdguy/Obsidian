---
id: c265896d-e238-4462-88fb-4194d438bddc
title: "Decision_Knoten"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - modellierung
  - aktivitaetsdiagramm
  - zustandsdiagramm
  - kontrollfluss
  - draft
source: "Klausur_Referenz"
---

# [[Decision_Knoten]]

- **Kernkonzept:** Ein **Decision_Knoten** (auch Entscheidungs- oder Verzweigungsknoten) ist ein Element in [[Aktivitätsdiagrammen]] oder [[Zustandsdiagrammen]] der [[UML]], das den Kontrollfluss basierend auf einer Bedingung (Guard) in alternative Pfade aufteilt. Er repräsentiert eine explizite Entscheidung im Prozessablauf und wird durch eine Raute (◇) symbolisiert. Die ausgehenden Kanten sind mit Bedingungen annotiert, von denen genau eine zur Laufzeit erfüllt sein muss (exklusives Oder).
- **Nutzen & Zweck:** Decision_Knoten dienen der Modellierung von Verzweigungen in Abläufen, um:
- **Komplexe Logik** in [[Aktivitätsdiagrammen]] strukturiert darzustellen (z. B. Fallunterscheidungen in Algorithmen oder Geschäftsprozessen).
- **Bedingte Ausführung** von Aktionen zu spezifizieren, ohne den Code vorwegzunehmen (z. B. in der Analysephase).
- **Nicht-deterministische Entscheidungen** in [[Zustandsautomaten]] zu modellieren (z. B. bei Ereignisverarbeitung).

Sie erhöhen die Lesbarkeit von Diagrammen, indem sie Entscheidungen explizit machen und von sequenziellen Schritten abgrenzen.
- **Abgrenzung & Grenzen:** - **Keine Parallelität**: Im Gegensatz zu [[Fork_Knoten]] (Gabelung) repräsentiert ein Decision_Knoten *keine* parallele Ausführung, sondern eine exklusive Auswahl.
- **Keine Datenflusssteuerung**: Decision_Knoten operieren auf Kontrollfluss-Ebene; für Datenflussverzweigungen werden [[Objektknoten]] oder [[Pins]] verwendet.
- **Stolpersteine**: 
  - Mehrdeutige Guards (überlappende Bedingungen) führen zu undefiniertem Verhalten.
  - Fehlende `else`-Bedingung kann zu Deadlocks im Diagramm führen.
  - In [[Zustandsdiagrammen]] werden Decision_Knoten oft mit [[Transitionen]] kombiniert, die eigene Guards besitzen – hier ist die Abgrenzung kritisch.
- **Beispiel / Code:** {'uml_aktivitaetsdiagramm': '```mermaid\nflowchart TD\n    A[Start] --> B[Daten prüfen]\n    B --> C{Decision_Knoten:\n    Daten gültig?}\n    C -->|Ja| D[Verarbeiten]\n    C -->|Nein| E[Fehler melden]\n    D --> F[Ende]\n    E --> F\n```', 'java_entsprechung': '// Beispiel: Decision-Knoten als if-else in Java\npublic void verarbeiteDaten(Daten daten) {\n    if (daten.sindGueltig()) {  // Guard-Bedingung des Decision_Knotens\n        verarbeiten(daten);\n    } else {\n        fehlerMelden();\n    }\n}', 'hinweis_klausurkontext': "In den gegebenen Tabellen (z. B. A.3: '4 / 7') könnte ein Decision_Knoten die Auswahl zwischen zwei Pfaden steuern, wobei die Zahlen die Gewichtung oder Wahrscheinlichkeit der Pfade angeben (z. B. 4 von 11 Fällen für Pfad 1). Die Notation '-0,5 bei zu viel/zu wenig' deutet auf Abzüge bei falscher Pfadauswahl hin – typisch für Entscheidungsbäume in Prüfungsszenarien."}
