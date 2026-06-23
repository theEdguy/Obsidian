---
id: 60ebe717-2a12-45c9-8093-813211a499ee
title: "Natürliche Modellierung"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - geschichte
  - draft
source: "software_engineering_kapitel_03"
---

# [[Natürliche Modellierung]]

- **Kernkonzept:** Natürliche Modellierung ist ein Grundprinzip der Objektorientierung, bei dem Objekte und Klassen der Softwareentwicklung als Abbildungen realer Entitäten oder Konzepte aus der Problemdomäne gestaltet werden, um deren Struktur und Verhalten intuitiv abzubilden.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Lücke zwischen der realen Welt und der Software zu verkleinern. Es löst das Problem der Komplexitätsbewältigung, indem es Entwicklern ermöglicht, Systeme so zu entwerfen, dass sie für Anwender und Stakeholder verständlich und nachvollziehbar sind. Durch die direkte Abbildung realer Objekte wird die Kommunikation zwischen Entwicklern und Domänenexperten verbessert, was zu präziseren Anforderungen und weniger Missverständnissen führt. Zudem fördert es die Wiederverwendbarkeit und Wartbarkeit von Code, da die Modelle näher an der Realität und damit weniger anfällig für Änderungen sind.
- **Abgrenzung & Grenzen:** Natürliche Modellierung sollte nicht genutzt werden, wenn die Problemdomäne stark abstrakt oder mathematisch geprägt ist, da hier reale Entitäten schwer identifizierbar sind. Alternativen wie funktionale Programmierung oder datenflussorientierte Ansätze können in solchen Fällen besser geeignet sein. Zudem kann eine zu starke Fokussierung auf die Realität zu übermäßig komplexen Modellen führen, wenn irrelevante Details abgebildet werden. Die Methode unterscheidet sich von rein technischen Ansätzen, die primär auf Effizienz oder Implementierungsdetails abzielen, indem sie den Fokus auf die Domänenlogik legt.
- **Beispiel / Code:** ```java
// Beispiel: Natürliche Modellierung eines Vereinsmitglieds
public class Mitglied {
    private String name;
    private String adresse;
    private int alter;
    private int leistungspunkte;

    public Mitglied(String name, String adresse, int alter) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
        this.leistungspunkte = 0;
    }

    public int leistungsprognose(int tage) {
        // Berechnung basierend auf realen Eigenschaften
        return leistungspunkte + (alter < 30 ? tage * 2 : tage);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2a
- **Vorgänger / Parent:** [[Säulen_der_Objektorientierung]]
- **Folgezettel / Unterzettel:**
  - [[Simula]]
  - [[Kristen_Nygaard]]
  - [[Ole-Johan_Dahl]]
- **Querverweise:** keine
