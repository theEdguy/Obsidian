---
id: 6d3c6d69-82be-4190-b7ef-a80aeedc6a79
title: "Navigierbare Assoziation"
date: 2026-06-23
tags:
  - software_engineering
  - klassendiagramm
  - beziehung
  - draft
source: "software_engineering_kapitel_05"
---

# [[Navigierbare Assoziation]]

- **Kernkonzept:** Eine navigierbare Assoziation ist eine gerichtete Beziehung zwischen Klassen in einem Klassendiagramm, bei der nur eine der beteiligten Klassen die andere kennt und auf deren Objekte zugreifen kann, während die andere Klasse keine Kenntnis von der Beziehung hat.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Richtung der Abhängigkeit und Kommunikation zwischen Objekten explizit zu modellieren. Es löst das Problem unklarer Verantwortlichkeiten und unnötiger Kopplung, indem es sicherstellt, dass nur die notwendigen Klassen voneinander wissen. Dadurch wird die Wartbarkeit und Verständlichkeit des Systems verbessert, da die Zugriffsrichtung klar definiert ist und unidirektionale Abhängigkeiten gezielt gesteuert werden können.
- **Abgrenzung & Grenzen:** Eine navigierbare Assoziation sollte nicht genutzt werden, wenn eine bidirektionale Beziehung erforderlich ist, bei der beide Klassen voneinander Kenntnis haben müssen. Sie unterscheidet sich von einer regulären (nicht-navigierbaren) Assoziation durch die explizite Richtungsangabe und von einer Abhängigkeit (Dependency) dadurch, dass sie eine strukturelle Beziehung beschreibt, während eine Dependency eine temporäre oder dynamische Beziehung darstellt. Zudem ist sie keine Komposition oder Aggregation, da diese spezifische Existenzabhängigkeiten oder Teile-Ganzes-Beziehungen modellieren.
- **Beispiel / Code:** ```java
// Beispiel für eine navigierbare Assoziation in Java
class Mitglied {
    private List<Disziplin> disziplinen;
    
    public List<Disziplin> getDisziplinen() {
        return disziplinen;
    }
    
    public void addDisziplin(Disziplin disziplin) {
        disziplinen.add(disziplin);
    }
}

class Disziplin {
    // Die Disziplin kennt keine Mitglieder, die sie ausüben
    private String name;
    
    public Disziplin(String name) {
        this.name = name;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1a1c
- **Vorgänger / Parent:** [[Assoziation]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Assoziation]]
  - [[Klassendiagramm]]
