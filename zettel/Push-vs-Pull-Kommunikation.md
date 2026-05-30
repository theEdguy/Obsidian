---
id: a246ea69-11f7-48f3-ae9f-2fc5d09c5f6c
title: "Push-vs-Pull-Kommunikation"
date: 2026-05-30
tags:
  - software_engineering
  - kommunikationsmuster
  - design_pattern
  - systemdesign
  - draft
source: "SWE Slides (Folien 211-225)"
---

# [[Push-vs-Pull-Kommunikation]]

- **Kernkonzept:** [[Push-vs-Pull-Kommunikation]] beschreibt zwei [[Kommunikationsmuster]] zwischen [[Komponente|Komponenten]]: Bei [[Push]] sendet die Quelle Daten aktiv an den Empfänger, bei [[Pull]] fragt der Empfänger die Daten aktiv ab.
- **Nutzen & Zweck:** [[Push]]-Kommunikation ist effizienter für [[Echtzeit]]-Updates (z. B. [[Event-gesteuertes_System|Event-gesteuerte Systeme]]), während [[Pull]] einfacher zu implementieren ist, aber [[Polling]] erfordert und [[Latenz]] verursachen kann.
- **Abgrenzung & Grenzen:** [[Pull]] ist ineffizient für häufige Updates, da es zu unnötiger [[Last]] führt. [[Push]] erfordert eine stärkere [[Kopplung]] zwischen [[Komponente|Komponenten]] und kann zu [[Skalierbarkeitsproblem|Skalierbarkeitsproblemen]] führen.
- **Beispiel / Code:** ```java
// Push-Beispiel (Observer-Pattern)
public interface Observer {
    void update(String data);
}

public class Subject {
    private List<Observer> observers = new ArrayList<>();
    
    public void addObserver(Observer observer) {
        observers.add(observer);
    }
    
    public void notifyObservers(String data) {
        for (Observer observer : observers) {
            observer.update(data);
        }
    }
}

// Pull-Beispiel
public class DataSource {
    public String getData() {
        return "Aktuelle Daten";
    }
}
```
