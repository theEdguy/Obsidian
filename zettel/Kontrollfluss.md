---
id: 6794fab9-59d8-48b5-92ff-5c90c8261f48
title: "Kontrollfluss"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - algorithmen
  - modellierung
  - kontrollstrukturen
  - nebenläufigkeit
  - draft
source: "Klausur_Referenz"
---

# [[Kontrollfluss]]

- **Kernkonzept:** Der **Kontrollfluss** beschreibt die Reihenfolge, in der Anweisungen, Aktionen oder Prozesse in einem [[Algorithmus]] oder [[Programm]] ausgeführt werden. Er definiert, wie die Steuerung von einem Schritt zum nächsten übergeht, basierend auf Bedingungen, Schleifen oder Verzweigungen. In der [[Modellierung]] (z. B. mit [[Aktivitätsdiagramm]] oder [[Zustandsdiagramm]]) wird der Kontrollfluss durch Pfeile dargestellt, die den Übergang zwischen [[Aktion]]en oder [[Objektknoten]] regeln. Im Gegensatz zum [[Datenfluss]], der den Transport von Daten zwischen Komponenten abbildet, fokussiert der Kontrollfluss auf die logische Abfolge der Ausführung.
- **Nutzen & Zweck:** Der Kontrollfluss ist essenziell für:
- Die Strukturierung von [[Algorithmen]] und [[Programmablaufplan]]en, um komplexe Logik verständlich abzubilden.
- Die Modellierung von [[Geschäftsprozessen]] oder Workflows in der [[Softwarearchitektur]], z. B. zur Darstellung von Entscheidungsbäumen oder parallelen Abläufen.
- Die Implementierung von [[Kontrollstrukturen]] wie Schleifen (`for`, `while`), Verzweigungen (`if-else`) oder Ausnahmebehandlungen (`try-catch`).
- Die Analyse von [[Nebenläufigkeit]], indem parallele Pfade (z. B. in [[Swimlanes]]) oder Synchronisationspunkte definiert werden.

Vorteile:
- Klare Trennung von Logik und Datenfluss, was die Wartbarkeit und Nachvollziehbarkeit von Systemen erhöht.
- Ermöglicht die Modellierung von [[Nicht-funktionale_Anforderungen]] wie Performance (z. B. durch Parallelisierung) oder Fehlerbehandlung.
- **Abgrenzung & Grenzen:** Abgrenzung zu verwandten Konzepten:
- **[[Datenfluss]]**: Beschreibt den Transport von Daten zwischen Komponenten, während der Kontrollfluss die Ausführungsreihenfolge steuert. Beide können in [[Aktivitätsdiagramm]]en kombiniert werden (z. B. durch [[Objektknoten]] mit Bedingungen).
- **[[Zustandsübergang]]**: In [[Zustandsdiagramm]]en wird der Kontrollfluss durch Zustandswechsel abgebildet, während in Aktivitätsdiagrammen der Fokus auf Aktionen liegt.
- **[[Nebenläufigkeit]]**: Parallele Kontrollflüsse erfordern Mechanismen wie [[Synchronisation]] oder [[Thread]]-Sicherheit, um Race Conditions zu vermeiden.

Typische Stolpersteine:
- **Zyklische Abhängigkeiten**: Endlosschleifen oder rekursive Kontrollflüsse ohne Abbruchbedingung.
- **Unklare Bedingungen**: Mehrdeutige Verzweigungen (z. B. überlappende `if`-Bedingungen) führen zu undefiniertem Verhalten.
- **Performance-Engpässe**: Serielle Kontrollflüsse in parallelen Systemen (z. B. [[Deadlock]]s).
- **Modellierungsfehler**: Vermischung von Kontroll- und Datenfluss in Diagrammen, was die Lesbarkeit beeinträchtigt.
- **Beispiel / Code:** {'beschreibung': 'UML-Aktivitätsdiagramm (textuell mit Mermaid-Syntax) zur Veranschaulichung eines Kontrollflusses mit Verzweigungen und Parallelisierung:', 'mermaid_diagramm': '```mermaid\nflowchart TD\n    A[Action A] -->|Bedingung x| B[Action B in anderer Swimlane]\n    A -->|Bedingung not x| C[Action C]\n    C --> D[Action D]\n    D -->|Parallelisierung| E[Join-Knoten]\n    C -->|Parallelisierung| E\n    E --> A\n```', 'code_beispiel_java': '```java\npublic class KontrollflussBeispiel {\n    public static void main(String[] args) {\n        boolean x = false; // Beispielbedingung\n        \n        // Kontrollfluss mit Verzweigung\n        if (x) {\n            fuehreActionBAus(); // Bedingung \'x\' erfüllt\n        } else {\n            // Parallelisierung (simuliert durch Threads)\n            Thread threadC = new Thread(() -> fuehreActionCAus());\n            Thread threadD = new Thread(() -> fuehreActionDAus());\n            \n            threadC.start();\n            threadD.start();\n            \n            try {\n                threadC.join(); // Synchronisation\n                threadD.join();\n            } catch (InterruptedException e) {\n                e.printStackTrace();\n            }\n            \n            // Rekursiver Aufruf (simuliert Schleife)\n            main(args);\n        }\n    }\n    \n    private static void fuehreActionBAus() {\n        System.out.println("Action B ausgeführt");\n    }\n    \n    private static void fuehreActionCAus() {\n        System.out.println("Action C ausgeführt");\n    }\n    \n    private static void fuehreActionDAus() {\n        System.out.println("Action D ausgeführt");\n    }\n}\n```'}
