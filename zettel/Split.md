---
id: 56f154b2-9313-4d95-83ac-672a2c66811a
title: "Split"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_08"
---

# [[Split]]

- **Kernkonzept:** Ein 'Split' in UML-Aktivitätsdiagrammen ist ein Kontrollknoten, der einen einzelnen Kontrollfluss in mehrere parallele Flüsse aufteilt. Dadurch können mehrere Aktionen gleichzeitig oder unabhängig voneinander ausgeführt werden.
- **Nutzen & Zweck:** Das 'Split'-Konzept existiert, um parallele Abläufe in Prozessen oder Algorithmen modellieren zu können. Es löst das Problem, dass sequenzielle Darstellungen komplexe, gleichzeitig ablaufende Vorgänge nicht adäquat abbilden können. Besonders in verteilten Systemen, Workflows oder bei der Beschreibung von Geschäftsprozessen ermöglicht es die klare Visualisierung von Nebenläufigkeit und verbessert das Verständnis für Abhängigkeiten und Synchronisationspunkte.
- **Abgrenzung & Grenzen:** Ein 'Split' sollte nicht genutzt werden, wenn die modellierten Abläufe strikt sequenziell sind oder keine echte Parallelität erfordern, da dies die Komplexität unnötig erhöht. Es unterscheidet sich von einer 'Entscheidung' (Decision), die alternative Pfade basierend auf Bedingungen modelliert, während ein 'Split' mehrere Pfade gleichzeitig aktiviert. Zudem sollte es vermieden werden, wenn die Zielplattform keine parallele Ausführung unterstützt oder wenn die Synchronisation der parallelen Pfade (z. B. durch einen 'Join') nicht klar definiert ist.
- **Beispiel / Code:** ```java
// Beispiel: Parallele Verarbeitung in einem Aktivitätsdiagramm mit Split/Join
// Pseudocode zur Illustration der Parallelität
public void verarbeiteBestellung(Bestellung bestellung) {
    // Split: Parallele Ausführung von Lagerprüfung und Zahlungsabwicklung
    Thread lagerThread = new Thread(() -> pruefeLagerbestand(bestellung));
    Thread zahlungThread = new Thread(() -> verarbeiteZahlung(bestellung));
    
    lagerThread.start();
    zahlungThread.start();
    
    // Join: Warten auf Abschluss beider Threads
    try {
        lagerThread.join();
        zahlungThread.join();
    } catch (InterruptedException e) {
        e.printStackTrace();
    }
    
    versendeBestellung(bestellung);
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a3
- **Vorgänger / Parent:** [[Aktivitätsdiagramm_Bausteine]]
- **Folgezettel / Unterzettel:**
  - [[Join]]
- **Querverweise:**
  - [[Aktivitätsdiagramm]]
