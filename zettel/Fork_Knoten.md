---
id: 27129b9f-e1a2-4c69-8608-8b4c78eaf71c
title: "Fork_Knoten"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - entwurfsmuster
  - nebenlaeufigkeit
  - aktivitaetsdiagramm
  - zustandsmaschine
  - softwarearchitektur
  - draft
source: "Klausur_Referenz"
---

# [[Fork_Knoten]]

- **Kernkonzept:** Ein **Fork_Knoten** ist ein spezieller Kontrollknoten in [[UML_2.0]]-Aktivitätsdiagrammen, der einen einzelnen Kontrollfluss in mehrere parallele Flüsse aufteilt. Er repräsentiert eine Verzweigung (Fork) in unabhängige, gleichzeitig ausführbare Pfade (sogenannte *Regionen* oder *Token*). Der Fork_Knoten ist das Gegenstück zum [[Join_Knoten]], der parallele Flüsse wieder synchronisiert. Im Kontext von [[Zustandsmaschinen]] oder [[Aktivitätsdiagrammen]] markiert er den Beginn paralleler Abläufe, die erst bei Erreichen eines Join-Knotens wieder zusammengeführt werden.
- **Nutzen & Zweck:** Der Fork_Knoten dient dazu:
- **Parallelität** in Prozessen oder Algorithmen explizit abzubilden, z. B. bei der Modellierung von [[Nebenläufigkeit]] in [[Softwarearchitektur]] oder Workflows.
- **Komplexe Abläufe** in überschaubare, parallel ausführbare Teilschritte zu zerlegen (z. B. in [[Mehrschichtige_Architektur]] oder [[Microservices]]).
- **Meilensteine** und Fortschrittsmessung zu unterstützen, indem klare Übergänge zwischen Abschnitten definiert werden (vgl. [[Meilenstein]] im Projektmanagement).
- **Anpassungsfähigkeit** zu erhöhen, indem Teilprozesse unabhängig voneinander modifiziert werden können, ohne den Kernablauf zu beeinflussen (vgl. [[Open-Closed_Principle]]).
- **Abgrenzung & Grenzen:** - **Keine bedingte Verzweigung**: Im Gegensatz zu einem [[Entscheidungsknoten]] (Decision Node) teilt ein Fork_Knoten den Fluss *immer* in alle ausgehenden Kanten auf – es gibt keine Bedingungen.
- **Keine Synchronisation**: Ein Fork_Knoten erzeugt parallele Flüsse, synchronisiert sie aber nicht. Dafür ist ein [[Join_Knoten]] erforderlich.
- **Stolpersteine**: 
  - *Deadlocks*: Wenn parallele Pfade nicht korrekt synchronisiert werden (z. B. fehlender Join-Knoten).
  - *Race Conditions*: Bei unklaren Abhängigkeiten zwischen parallelen Regionen.
  - *Übermodellierung*: Fork-Knoten sollten nur eingesetzt werden, wenn echte Parallelität vorliegt, nicht für sequenzielle Abläufe.
- **Einsatzgrenzen**: In [[Sequenzdiagrammen]] oder [[Klassendiagrammen]] nicht direkt anwendbar – hier sind andere Muster wie [[Asynchroner_Methodenaufruf]] relevant.
- **Beispiel / Code:** ```mermaid
%% UML-Aktivitätsdiagramm mit Fork- und Join-Knoten
flowchart TD
    A[Start] --> B[Fork_Knoten]
    B --> C[Teilprozess 1]
    B --> D[Teilprozess 2]
    C --> E[Join_Knoten]
    D --> E
    E --> F[Weiterer Prozess]
    F --> G[Ende]
    
    style B fill:#f9f,stroke:#333
    style E fill:#f9f,stroke:#333
```

**Java-ähnliches Pseudocode-Beispiel (parallele Threads):**
```java
public void mainProcess() {
    // Fork: Aufteilung in parallele Threads
    Thread thread1 = new Thread(() -> teilprozess1());
    Thread thread2 = new Thread(() -> teilprozess2());
    
    thread1.start();
    thread2.start();
    
    // Join: Synchronisation
    thread1.join();
    thread2.join();
    
    weiterfuehrenderProzess();
}
```
