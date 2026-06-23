---
id: 571da281-35fa-4d4a-96dc-f73b8c1d006a
title: "Fachkonzept"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Fachkonzept]]

- **Kernkonzept:** Das Fachkonzept ist ein zentrales Ergebnis der Analysephase im Software-Engineering, das die Problemdomäne und deren Strukturen, Konzepte sowie Zusammenhänge modelliert, ohne bereits technische Lösungsdetails zu berücksichtigen. Es dient als Brücke zwischen Anforderungen und der späteren Software-Architektur.
- **Nutzen & Zweck:** Das Fachkonzept existiert, um ein tiefgreifendes Verständnis der Problemdomäne zu schaffen und die essenziellen Abläufe, Objekte sowie deren Beziehungen zu identifizieren. Es löst das Problem, dass Entwickler und Stakeholder ohne eine klare, lösungsneutrale Darstellung der Domäne Gefahr laufen, technische Lösungen zu früh zu entwerfen oder zentrale Anforderungen zu übersehen. Durch die Fokussierung auf das 'Was' statt das 'Wie' wird sichergestellt, dass die Software später die tatsächlichen Bedürfnisse der Nutzer abbildet.
- **Abgrenzung & Grenzen:** Das Fachkonzept sollte nicht genutzt werden, wenn bereits technische Designentscheidungen getroffen werden müssen oder Implementierungsdetails im Vordergrund stehen. Es unterscheidet sich von einem technischen Designkonzept dadurch, dass es bewusst auf Plattform-, Framework- oder Programmiersprachen-spezifische Aspekte verzichtet. Alternativen wie das *Lösungsdesign* oder *Architekturmodelle* kommen erst in späteren Phasen zum Einsatz, wenn das Fachkonzept bereits vorliegt und validiert wurde. Zudem ist es ungeeignet für Projekte, bei denen die Problemdomäne trivial oder bereits vollständig verstanden ist.
- **Beispiel / Code:** ```java
// Beispiel: Fachkonzept-Klasse 'Mitglied' aus der Problemdomäne eines Vereins
// (ohne technische Attribute wie Datenbank-IDs oder Methoden-Implementierungen)
public class Mitglied {
    private String name;
    private String status; // z.B. 'aktiv', 'passiv'
    private List<Abteilung> abteilungen;
    
    // Fachliche Beziehungen (keine technischen Details)
    public void abteilungBeitreten(Abteilung abteilung) {
        // Logik zur Mitgliedschaft in einer Abteilung (Problemdomäne)
    }
    
    public void statusAendern(String neuerStatus) {
        // Regelwerk für Statusänderungen (z.B. Benachrichtigungen)
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3a
- **Vorgänger / Parent:** [[Problemdomäne]]
- **Folgezettel / Unterzettel:**
  - [[Entität]]
  - [[Wert]]
  - [[Dienst]]
- **Querverweise:**
  - [[Problemdomäne]]
  - [[Anforderungsanalyse]]
