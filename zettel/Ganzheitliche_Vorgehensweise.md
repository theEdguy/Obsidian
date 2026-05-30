---
id: ec926cf9-53fc-42a6-a3a5-62f26c9f91bb
title: "Ganzheitliche_Vorgehensweise"
date: 2026-05-30
tags:
  - software_engineering
  - systemdenken
  - draft
source: "SWE Slides (Folien 61-75)"
---

# [[Ganzheitliche_Vorgehensweise]]

- **Kernkonzept:** Die [[Ganzheitliche_Vorgehensweise]] betrachtet [[Daten]], [[Funktion|Funktionen]] und deren [[Zusammenhang|Zusammenhänge]] als untrennbare Einheit im [[Softwareentwicklungsprozess]]. Sie betont die [[Modellierung]] der realen Welt in ihrer Komplexität, ohne [[Abstraktion|irrelevante Details]] zu vernachlässigen.
- **Nutzen & Zweck:** Sie löst das Problem der [[Reduktionismus|reduktionistischen]] [[Sichtweise]] in der [[Softwareentwicklung]], indem sie [[Systemkomplexität]] durch integrierte [[Modellierung]] von [[Daten]], [[Funktion|Funktionen]] und [[Beziehung|Beziehungen]] beherrschbar macht.
- **Abgrenzung & Grenzen:** Nicht sinnvoll bei stark isolierten [[Teilsystem|Teilsystemen]] oder wenn [[Performance]]-Optimierungen lokale [[Code]]-Anpassungen erfordern. Unterscheidet sich von [[Funktionale_Dekomposition]] durch die Betonung von [[Daten]]- und [[Beziehung|Beziehungsmodellierung]].
- **Beispiel / Code:** ```java
// Beispiel: Modellierung eines Vereins mit Mitgliedern und Disziplinen
class Verein {
    private List<Mitglied> mitglieder;
    private List<Disziplin> disziplinen;
    
    public void aktivBei(Mitglied mitglied, Disziplin disziplin) {
        // Logik zur Verknüpfung
    }
}
```
