---
id: b65b878d-a125-4088-9727-efb2e1dfd0aa
title: "Review-Prozess"
date: 2026-06-23
tags:
  - software_engineering
  - review
  - validierung
  - draft
source: "software_engineering_kapitel_07"
---

# [[Review-Prozess]]

- **Kernkonzept:** Der Review-Prozess ist eine systematische Überprüfung von Arbeitsergebnissen (z. B. Use Cases, Code oder Architektur) durch unabhängige Dritte, um Fehler zu identifizieren, Qualität zu sichern und die Erfüllung von Anforderungen zu validieren. Er dient als qualitätssichernde Maßnahme im Software-Engineering-Prozess.
- **Nutzen & Zweck:** Der Review-Prozess existiert, um frühzeitig Defizite in der Anforderungsanalyse, im Design oder in der Implementierung aufzudecken, bevor diese in spätere Entwicklungsphasen übertragen werden. Er löst das Problem, dass Fehler oder Unstimmigkeiten in Use Cases, Architekturentscheidungen oder Code oft erst spät erkannt werden, was zu hohen Korrekturkosten führt. Zudem fördert er Wissenstransfer im Team und stellt sicher, dass alle Beteiligten ein gemeinsames Verständnis der Anforderungen und Lösungen entwickeln.
- **Abgrenzung & Grenzen:** Der Review-Prozess sollte nicht genutzt werden, wenn Zeitdruck oder Ressourcenmangel eine gründliche Prüfung verhindern, da oberflächliche Reviews keine signifikanten Vorteile bringen. Er unterscheidet sich von automatisierten Tests oder Code-Analysen, da er menschliche Expertise und kontextuelles Verständnis erfordert, um z. B. logische Fehler in Use Cases oder Designentscheidungen zu erkennen. Zudem ist er ungeeignet für triviale oder klar definierte Aufgaben, bei denen der Aufwand den Nutzen übersteigt. Alternativen wie Pair Programming oder kontinuierliche Integration können in agilen Umgebungen ergänzend oder teilweise ersetzend wirken.
- **Beispiel / Code:** ```java
// Beispiel für einen dokumentierten Use Case mit Review-Hinweisen (Pseudocode)
/**
 * Use Case: Mitglieder verwalten (Review-Protokoll)
 * 
 * Review-Datum: 2023-11-15
 * Reviewer: Max Mustermann, Anna Schmidt
 * 
 * Festgestellte Mängel:
 * 1. Fehlende Validierung der E-Mail-Adresse (F1.2 nicht vollständig erfüllt)
 * 2. Unklare Regelung für passive Mitglieder (Offener Punkt im Beispiel)
 * 
 * Empfehlungen:
 * - E-Mail-Validierung gemäß RFC 5322 implementieren
 * - Klare Definition für passive Mitglieder in F2.1 ergänzen
 */
public class MitgliedVerwaltungUseCase {
    // ... Implementierung der Use-Case-Logik
    public void mitgliedAktualisieren(Mitglied mitglied) {
        if (!isValidEmail(mitglied.getEmail())) {
            throw new IllegalArgumentException("Ungültige E-Mail-Adresse");
        }
        // ...
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2d2
- **Vorgänger / Parent:** [[Anforderungsvalidierung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Anforderungsvalidierung]]
  - [[Qualitätssicherung]]
