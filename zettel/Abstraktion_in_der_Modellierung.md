---
id: 2b36d3f8-24f4-4451-88e5-ac0cbb02f967
title: "Abstraktion_in_der_Modellierung"
date: 2026-05-30
tags:
  - software_engineering
  - modellierung
  - objektorientierung
  - draft
source: "SWE Slides (Folien 61-75)"
---

# [[Abstraktion_in_der_Modellierung]]

- **Kernkonzept:** [[Abstraktion_in_der_Modellierung]] reduziert die [[Komplexität]] realer [[Systeme]] durch Fokussierung auf [[Problem]]-relevante [[Eigenschaft|Eigenschaften]], während irrelevante Details ignoriert werden. Sie ist Grundlage für [[Klassifikation]] und [[Modellierung]] in der [[Objektorientierung]].
- **Nutzen & Zweck:** Sie löst das Problem der [[Informationsüberflutung]] bei der [[Modellierung]] komplexer [[Systeme]], indem sie [[Kognitiver_Aufwand|kognitiven Aufwand]] reduziert und die [[Wiederverwendbarkeit]] von [[Modell]]-Elementen erhöht.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn alle [[Eigenschaft|Eigenschaften]] eines [[Systems]] gleich relevant sind (z. B. in [[Sicherheitskritische_Systeme|sicherheitskritischen Systemen]]). Unterscheidet sich von [[Detaillierung]] durch bewusste Auslassung von [[Information|Informationen]].
- **Beispiel / Code:** ```java
// Abstraktion: Nur relevante Attribute eines Mitglieds
class Mitglied {
    private String name;
    private int leistung;  // Irrelevante Details (z. B. Blutgruppe) weggelassen
    
    public int leistungsprognose() {
        return leistung * 2;  // Vereinfachte Logik
    }
}
```
