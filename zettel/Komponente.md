---
id: 217effea-0453-4bdf-9a76-7e57b9cfce5b
title: "Komponente"
date: 2026-05-30
tags:
  - software_engineering
  - architektur
  - design
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Komponente]]

- **Kernkonzept:** Eine [[Komponente]] ist eine modulare, wiederverwendbare Einheit in der [[Systemarchitektur]], die eine dedizierte [[Funktionalität]] kapselt. Sie besitzt eine definierte [[Schnittstelle]] und ist unabhängig von anderen [[Komponente|Komponenten]].
- **Nutzen & Zweck:** Sie fördert die [[Modularität]], [[Wiederverwendbarkeit]] und [[Wartbarkeit]] des Systems. [[Komponente|Komponenten]] ermöglichen die Zerlegung komplexer Systeme in beherrschbare Teile.
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Klasse|Klassen]] oder [[Funktion|Funktionen]] auf Code-Ebene. [[Komponente|Komponenten]] sind größer und beschreiben die [[Architektur]]-Ebene. Im Gegensatz zu [[Modul|Modulen]] sind sie oft mit klaren [[Schnittstelle|Schnittstellen]] definiert.
- **Beispiel / Code:** ```java
// Beispiel einer Komponente in Java (Spring Boot)
@Component
public class BestellService {
    public Bestellung erstelleBestellung(Warenkorb warenkorb) {
        // Logik zur Bestellungserstellung
    }
}
```
