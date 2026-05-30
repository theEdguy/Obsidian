---
id: 64f6c95d-e274-4021-90a0-d9c9bd778acd
title: "Modellierung_von_Beziehungen"
date: 2026-05-30
tags:
  - software_engineering
  - modellierung
  - objektorientierung
  - draft
source: "SWE Slides (Folien 61-75)"
---

# [[Modellierung_von_Beziehungen]]

- **Kernkonzept:** [[Modellierung_von_Beziehungen]] beschreibt die [[Abstraktion]] von [[Zusammenhang|Zusammenhängen]] zwischen [[Klasse|Klassen]] oder [[Objekt|Objekten]] in [[Software]]-Systemen, z. B. durch [[Assoziation]], [[Aggregation]] oder [[Komposition]].
- **Nutzen & Zweck:** Sie löst das Problem der [[Komplexitätsbeherrschung]] in [[Systemdesign|Systemdesigns]], indem sie [[Abhängigkeit|Abhängigkeiten]] explizit macht und [[Kopplung]] zwischen [[Komponente|Komponenten]] steuert.
- **Abgrenzung & Grenzen:** Nicht sinnvoll bei trivialen [[Systeme|Systemen]] mit wenigen [[Klasse|Klassen]] oder in [[Skript|Skripten]] mit linearer [[Logik]]. Unterscheidet sich von [[Datenmodellierung]] durch Fokus auf [[Verhalten]] und [[Struktur]] statt reiner [[Daten]]-Organisation.
- **Beispiel / Code:** ```java
// Modellierung einer Assoziation: Verein hat Mitglieder
class Verein {
    private List<Mitglied> mitglieder;  // 1:n-Beziehung
    
    public void addMitglied(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }
}
```
