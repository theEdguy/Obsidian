---
id: 5c3c0d06-aef0-41b4-86b8-c90c85d68821
title: "Join_Knoten"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - aktivitaetsdiagramm
  - nebenlaeufigkeit
  - workflow_modellierung
  - entwurfsmuster_parallelitaet
  - draft
source: "Klausur_Referenz"
---

# [[Join_Knoten]]

- **Kernkonzept:** Ein **Join_Knoten** ist ein spezieller [[Kontrollknoten]] in [[UML]]-Aktivitätsdiagrammen, der mehrere parallele [[Kontrollflüsse]] oder [[Objektflüsse]] synchronisiert und zu einem einzigen Fluss zusammenführt. Er wird verwendet, um die Beendigung aller eingehenden Flüsse abzuwarten, bevor der ausgehende Fluss fortgesetzt wird. Im Gegensatz zu einem [[Merge_Knoten]] (der alternative Pfade zusammenführt) erzwingt der Join_Knoten eine *UND*-Semantik: Alle eingehenden Kanten müssen aktiv sein, bevor der nächste Schritt ausgeführt wird.
- **Nutzen & Zweck:** Der Join_Knoten dient der Modellierung von **Parallelität** und **Synchronisation** in Prozessen, insbesondere in:
- **Workflow-Modellierung**: Abbildung von Geschäftsprozessen, bei denen mehrere Teilaufgaben abgeschlossen sein müssen, bevor der nächste Schritt beginnt (z. B. Bestellabwicklung mit paralleler Zahlungs- und Lagerprüfung).
- **Software-Design**: Darstellung von [[Nebenläufigkeit]] in Algorithmen oder Systemarchitekturen (z. B. Thread-Synchronisation).
- **Fehlervermeidung**: Explizite Kennzeichnung von Abhängigkeiten zwischen parallelen Pfaden, um Race Conditions oder Deadlocks frühzeitig zu erkennen.

Vorteile:
- Klare Visualisierung von Synchronisationspunkten.
- Unterstützung der [[Modularität]] durch Trennung paralleler und sequenzieller Logik.
- **Abgrenzung & Grenzen:** - **Keine Entscheidung**: Im Gegensatz zu einem [[Entscheidungsknoten]] (z. B. `if-else`) trifft der Join_Knoten keine Auswahl, sondern wartet auf alle eingehenden Flüsse.
- **Keine Schleifen**: Join-Knoten sind nicht für iterative Prozesse geeignet (hierfür werden [[Schleifenknoten]] verwendet).
- **Stolpersteine**: 
  - **Deadlocks**: Falsche Platzierung kann zu Blockaden führen, wenn nicht alle eingehenden Flüsse aktiviert werden.
  - **Performance**: Unnötige Join-Knoten können parallele Ausführung ungewollt verlangsamen.
  - **Semantik**: In manchen UML-Tools wird die *UND*-Logik nicht automatisch validiert – die korrekte Modellierung liegt in der Verantwortung des Entwicklers.
- **Abgrenzung zu [[Fork_Knoten]]**: Während ein Fork-Knoten einen Fluss in mehrere parallele Pfade aufteilt, führt der Join-Knoten diese wieder zusammen.
- **Beispiel / Code:** {'uml_beschreibung': '```mermaid\nflowchart TD\n    A[Start] --> B[Aufgabe 1]\n    A --> C[Aufgabe 2]\n    A --> D[Aufgabe 3]\n    B --> E[Join_Knoten]\n    C --> E\n    D --> E\n    E --> F[Weiterer Prozess]\n```', 'java_analogie': '// Beispiel: Synchronisation von Threads mit Join (analog zur UML-Semantik)\npublic class JoinBeispiel {\n    public static void main(String[] args) throws InterruptedException {\n        Thread thread1 = new Thread(() -> System.out.println("Aufgabe 1 abgeschlossen"));\n        Thread thread2 = new Thread(() -> System.out.println("Aufgabe 2 abgeschlossen"));\n        \n        thread1.start();\n        thread2.start();\n        \n        // Join-Knoten-Semantik: Warten auf beide Threads\n        thread1.join();\n        thread2.join();\n        \n        System.out.println("Alle Aufgaben abgeschlossen – nächster Schritt");\n    }\n}', 'erlaeuterung_kontext': 'Im gegebenen Klausurauszug (1->2: 2,4,5 und 6->7: 7,10,8,5) deutet die Notation auf eine Bewertung von Join-Knoten in Aktivitätsdiagrammen hin. Die Zahlen könnten:\n- **Kosten** (z. B. Zeitaufwand) der Pfade vor dem Join darstellen,\n- **Strafpunkte** (-0,5) bei falscher Modellierung (z. B. fehlende Synchronisation) symbolisieren.\nDie Tabelle könnte eine Übungsaufgabe zur Berechnung der Gesamtkosten paralleler Pfade vor einem Join-Knoten sein.'}
