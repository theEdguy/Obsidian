---
id: 2c8205aa-7fdd-4dac-a5c1-c1d0e73500ed
title: "Objektmodell"
date: 2026-05-30
tags:
  - software_engineering
  - analyse
  - modellierung
  - oop
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Objektmodell]]

- **Kernkonzept:** Ein [[Modell]] der [[Problemdomäne]], das [[Klasse|Klassen]], deren [[Beziehung|Beziehungen]] und [[Verantwortlichkeit|Verantwortlichkeiten]] beschreibt. Dient der Abbildung der realen Welt in ein [[Softwaresystem]].
- **Nutzen & Zweck:** Löst das Problem der unklaren [[Struktur]] und [[Zuständigkeit]] in der [[Problemdomäne]] durch systematische Abbildung von [[Entität|Entitäten]] und deren Interaktionen. Grundlage für [[Datenbankdesign]] und [[Implementierung]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Verhaltensmodellierung]] oder [[Dynamische_Analyse]]. Bei zu komplexen [[Modell|Modellen]] kann die Wartbarkeit leiden. Erfordert regelmäßige [[Synchronisation]] mit anderen [[Modell|Modellen]].
- **Beispiel / Code:** ```java
// Beispiel für ein einfaches Objektmodell
class Mitglied {
    private String name;
    private Adresse adresse;
    private List<Beitrag> beitraege;

    public void aendereAdresse(Adresse neueAdresse) {
        this.adresse = neueAdresse;
    }
}

class Adresse {
    private String strasse;
    private String plz;
    private String ort;
}
```
