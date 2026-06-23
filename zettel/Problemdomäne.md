---
id: 9696e052-3344-4a62-bee1-d69f2796b41a
title: "Problemdomäne"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Problemdomäne]]

- **Kernkonzept:** Die Problemdomäne bezeichnet den spezifischen Ausschnitt der realen Welt, der für ein Softwareprojekt relevant ist und in dem die zu lösenden Probleme, Anforderungen sowie die zentralen Konzepte und Beziehungen zwischen diesen existieren. Sie bildet die Grundlage für die Analysephase im Software-Engineering und fokussiert sich auf das Verständnis des Problems, nicht auf dessen technische Umsetzung.
- **Nutzen & Zweck:** Das Konzept der Problemdomäne existiert, um ein klares und gemeinsames Verständnis des zu lösenden Problems zwischen allen Projektbeteiligten (z. B. Entwicklern, Auftraggebern, Domänenexperten) zu schaffen. Es hilft, die Anforderungen präzise zu erfassen, Missverständnisse zu vermeiden und sicherzustellen, dass die spätere Softwarelösung tatsächlich die realen Bedürfnisse der Nutzer abdeckt. Ohne eine explizite Fokussierung auf die Problemdomäne besteht die Gefahr, dass technische Lösungen entwickelt werden, die an den eigentlichen Anforderungen vorbeigehen oder unnötige Komplexität einführen.
- **Abgrenzung & Grenzen:** Die Problemdomäne sollte nicht mit der Lösungsdomäne verwechselt oder vermischt werden. Während die Problemdomäne das 'Was' (die Anforderungen und Konzepte des Problems) beschreibt, beschäftigt sich die Lösungsdomäne mit dem 'Wie' (der technischen Umsetzung, z. B. Architektur, Algorithmen oder Datenbankdesign). Das Konzept ist zudem nicht geeignet, wenn bereits eine fertige technische Lösung vorliegt oder wenn es sich um ein rein technisches Projekt ohne domänenspezifische Anforderungen handelt (z. B. ein Framework für generische Datenverarbeitung). In solchen Fällen wäre eine Fokussierung auf die Problemdomäne überflüssig oder sogar hinderlich.
- **Beispiel / Code:** ```java
// Beispiel: Identifizierte Konzepte der Problemdomäne für ein Vereinsverwaltungssystem
// (basierend auf dem Use Case 'Mitglieder verwalten')

public class Mitglied {
    private String name;
    private String status; // z. B. 'aktiv' oder 'passiv'
    private List<Abteilung> abteilungen;
    
    public void abteilungVerlassen(Abteilung abteilung) {
        // Logik zur Entfernung aus der Abteilung und Statusaktualisierung
        // (Problemdomäne: Was passiert? Nicht: Wie wird es technisch umgesetzt?)
    }
}

public class Abteilung {
    private String name;
    private List<Mitglied> mitglieder;
    
    public boolean hatMindestanzahlMitglieder() {
        return mitglieder.size() >= 10;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Fachkonzept]]
  - [[Problemraum]]
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Objektorientierte_Analyse]]
