---
id: fb42abcf-84ba-4b9b-ab9f-92e66df29493
title: "Zusicherung_in_der_Objektorientierung"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - datenmodellierung
  - draft
source: "SWE Slides (Folien 61-75)"
---

# [[Zusicherung_in_der_Objektorientierung]]

- **Kernkonzept:** [[Zusicherung_in_der_Objektorientierung]] (Constraints) sind formale [[Regel|Regeln]], die [[Objekt|Objekte]] einer [[Klasse]] erfüllen müssen, z. B. [[Wertbereich|Wertbereiche]] für [[Attribut|Attribute]] oder [[Invariante|Invarianten]] für [[Operation|Operationen]].
- **Nutzen & Zweck:** Sie löst das Problem der [[Datenintegrität]] und [[Konsistenz]] in [[Objektorientierte_Programmierung|objektorientierten Systemen]], indem sie [[Fehlerzustand|Fehlerzustände]] durch [[Validierung]] verhindert.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Prototyping|Prototypen]] oder [[Performance]]-kritische [[Code]]-Abschnitte, da [[Zusicherung|Zusicherungen]] [[Laufzeit]]-Overhead verursachen. Unterscheidet sich von [[Typprüfung]] durch domänenspezifische [[Regel|Regeln]].
- **Beispiel / Code:** ```java
// Zusicherung: Leistung muss zwischen 0 und 1440 liegen
class Mitglied {
    private int leistung;
    
    public void setLeistung(int leistung) {
        if (leistung < 0 || leistung > 1440) {
            throw new IllegalArgumentException("Ungültige Leistung");
        }
        this.leistung = leistung;
    }
}
```
