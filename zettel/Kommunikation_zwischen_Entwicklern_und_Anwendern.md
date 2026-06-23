---
id: 0f6f7033-4110-4897-a1fa-2664b47f4d3d
title: "Kommunikation zwischen Entwicklern und Anwendern"
date: 2026-06-23
tags:
  - software_engineering
  - prozess
  - draft
source: "software_engineering_kapitel_03"
---

# [[Kommunikation zwischen Entwicklern und Anwendern]]

- **Kernkonzept:** Die Kommunikation zwischen Entwicklern und Anwendern bezeichnet den strukturierten und iterativen Austausch von Anforderungen, Fachwissen und Feedback, um eine gemeinsame Verständnisbasis für die Softwareentwicklung zu schaffen. Sie ist essenziell, um reale Problemstellungen präzise in technische Lösungen zu überführen.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Kluft zwischen fachlichen Anforderungen (Problemraum) und technischer Umsetzung (Lösungsraum) zu überbrücken. Durch kontinuierliche Interaktion werden Missverständnisse reduziert, Anforderungen präzisiert und die Qualität der Software verbessert. Es löst das Problem, dass Entwickler ohne direkten Austausch oft an den Bedürfnissen der Anwender vorbeientwickeln, was zu teuren Nachbesserungen oder unbrauchbaren Produkten führt.
- **Abgrenzung & Grenzen:** Die Kommunikation zwischen Entwicklern und Anwendern sollte nicht genutzt werden, wenn Anforderungen bereits vollständig und unveränderlich dokumentiert sind (z. B. bei stark regulierten Systemen mit festen Spezifikationen). Alternativen wie detaillierte Lastenhefte oder formale Spezifikationen können hier effizienter sein. Zudem ist der Ansatz weniger geeignet, wenn Anwender keine Zeit oder Expertise für den Austausch haben – dann drohen oberflächliche Lösungen. Im Gegensatz zu rein dokumentenbasierten Methoden erfordert dieser Ansatz jedoch mehr Zeit und Ressourcen für Meetings und Iterationen.
- **Beispiel / Code:** ```java
// Beispiel für ein Dialog-getriebenes Anforderungsmodell (UML-Klasse basierend auf Anwenderfeedback)
class Mitglied {
    private String name;
    private String adresse;
    private int alter;
    private int leistungspunkte;

    // Methode basiert auf Anwenderaussage: "Leistungsfähigkeit muss jederzeit abrufbar sein"
    public int leistungsprognose(Date datum) {
        // Berechnung basierend auf historischen Daten
        return this.leistungspunkte * berechneTrend(datum);
    }
}
```

*Erläuterung:* Der Code zeigt, wie eine fachliche Anforderung ("Leistungsprognose") direkt aus dem Dialog mit Anwendern in eine technische Umsetzung überführt wird. Die Methode `leistungsprognose()` spiegelt das im Gespräch identifizierte Bedürfnis wider.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4c
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
