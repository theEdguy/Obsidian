---
id: 51ca3364-3130-4139-a1cc-893c97adf213
title: "Qualifier"
date: 2026-05-30
tags:
  - software_engineering
  - modellierung
  - datenstruktur
  - uml
  - draft
source: "SWE Slides (Folien 106-120)"
---

# [[Qualifier]]

- **Kernkonzept:** Ein [[Qualifier]] ist ein [[Attribut]] einer [[Assoziation]], das die Menge der [[Instanz|Instanzen]] auf der gegenüberliegenden Seite der [[Assoziation]] partitioniert und den Zugriff auf eine Teilmenge ermöglicht.
- **Nutzen & Zweck:** Er reduziert die [[Stelligkeit]] einer [[Assoziation]] von n auf 1, indem er den Zugriff auf [[Objekt|Objekte]] über einen eindeutigen Schlüssel ermöglicht, ähnlich wie ein [[Index]] in [[Datenbank|Datenbanken]].
- **Abgrenzung & Grenzen:** Nicht sinnvoll, wenn die [[Assoziation]] keine partitionierbare Menge von [[Instanz|Instanzen]] hat oder wenn die [[Stelligkeit]] bereits 1 ist. Kann die [[Modellkomplexität]] erhöhen.
- **Beispiel / Code:** ```java
class Team {
    private Map<Integer, Mitglied> mitgliederNachPosition;
    // Zugriff über Qualifier (teamPos)
}
```
