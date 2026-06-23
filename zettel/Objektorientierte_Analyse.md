---
id: ae6f956e-3978-4233-bfcd-d8af3d851821
title: "Objektorientierte Analyse"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Objektorientierte Analyse]]

- **Kernkonzept:** Die objektorientierte Analyse ist eine Methode im Software-Engineering, die darauf abzielt, die Problemdomäne durch Identifikation von Objekten, deren Beziehungen und Interaktionen zu verstehen und zu modellieren, ohne dabei bereits Lösungsaspekte der Software zu berücksichtigen.
- **Nutzen & Zweck:** Dieses Konzept existiert, um eine klare und strukturierte Grundlage für die Softwareentwicklung zu schaffen, indem es die realen Anforderungen und Zusammenhänge der Problemdomäne erfasst. Es löst das Problem, dass Entwickler oft zu früh in technische Details abgleiten, ohne das eigentliche Problem vollständig verstanden zu haben. Durch die Fokussierung auf die Problemdomäne wird sichergestellt, dass die spätere Softwarelösung die tatsächlichen Bedürfnisse der Nutzer und Stakeholder abbildet.
- **Abgrenzung & Grenzen:** Die objektorientierte Analyse sollte nicht genutzt werden, wenn es sich um triviale oder stark prozedural geprägte Systeme handelt, bei denen eine detaillierte Modellierung der Problemdomäne keinen Mehrwert bietet. Sie unterscheidet sich von der objektorientierten Designphase, die sich auf die technische Umsetzung konzentriert, sowie von funktionalen oder datengetriebenen Analysemethoden, die weniger Wert auf die Modellierung von Objekten und deren Beziehungen legen. Zudem ist sie nicht geeignet, wenn keine klaren Use Cases oder Anforderungen vorliegen, da sie auf diesen aufbaut.
- **Beispiel / Code:** ```java
// Beispiel: Identifikation von Objekten und deren Beziehungen in der Problemdomäne "Vereinsverwaltung"
class Mitglied {
    private String name;
    private Status status;
    private List<Abteilung> abteilungen;
    
    public void abteilungVerlassen(Abteilung abteilung) {
        abteilungen.remove(abteilung);
        if (abteilungen.isEmpty()) {
            this.status = Status.PASSIV;
        }
    }
}

class Abteilung {
    private String name;
    private List<Mitglied> mitglieder;
}

enum Status {
    AKTIV, PASSIV
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Objektidentifikation]]
  - [[Klassenmodell]]
  - [[Dynamisches_Modell]]
- **Querverweise:**
  - [[Use-Case-basierte_Analyse]]
  - [[UML]]
