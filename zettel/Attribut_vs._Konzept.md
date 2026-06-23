---
id: 199bfdc7-81fa-4c50-8207-3a58be16f5dc
title: "Attribut vs. Konzept"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Attribut vs. Konzept]]

- **Kernkonzept:** Im Kontext der objektorientierten Analyse beschreibt das Konzept 'Attribut vs. Konzept' die Unterscheidung zwischen Eigenschaften eines Objekts (Attribute) und eigenständigen Entitäten der Problemdomäne (Konzepte). Attribute sind einfache Datenfelder, während Konzepte komplexe Objekte mit eigener Identität und Verhalten darstellen.
- **Nutzen & Zweck:** Dieses Konzept existiert, um während der Analysephase Missverständnisse bei der Modellierung zu vermeiden. Es löst das Problem, dass Entwickler fälschlicherweise komplexe Domänenobjekte als einfache Attribute modellieren, was zu unflexiblen und schwer wartbaren Systemen führt. Durch klare Trennung wird die Problemdomäne präziser abgebildet und die spätere Softwarearchitektur robuster gestaltet.
- **Abgrenzung & Grenzen:** Man sollte dieses Konzept nicht nutzen, wenn es sich um triviale Daten handelt, die keine eigene Identität oder Verhalten benötigen, wie z.B. Farben, Zahlen oder einfache Texte. Es unterscheidet sich von reiner Attributmodellierung dadurch, dass es die semantische Bedeutung der Domäne berücksichtigt: Ein 'Attribut' ist eine Eigenschaft eines Objekts, während ein 'Konzept' ein eigenständiges Objekt mit Beziehungen zu anderen Konzepten darstellt. Nicht jedes Substantiv in Use-Case-Beschreibungen ist automatisch ein Konzept.
- **Beispiel / Code:** ```java
// Falsch: 'Abteilung' als Attribut modelliert
class Mitglied {
    private String name;
    private String abteilung; // Attribut statt Konzept
}

// Richtig: 'Abteilung' als eigenständiges Konzept modelliert
class Mitglied {
    private String name;
    private Abteilung abteilung; // Konzept mit eigener Identität
}

class Abteilung {
    private String name;
    private List<Mitglied> mitglieder;
    // Weitere Eigenschaften und Verhalten
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2a2
- **Vorgänger / Parent:** [[Objektidentifikation]]
- **Folgezettel / Unterzettel:**
  - [[Faustregel_Objekt_statt_Attribut]]
- **Querverweise:**
  - [[Problemdomäne]]
  - [[Fachkonzept]]
