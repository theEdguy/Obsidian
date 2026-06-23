---
id: 7da80c92-ee9d-41e2-8b52-1803c3523c11
title: "Ausnahme"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - requirements_engineering
  - draft
source: "software_engineering_kapitel_09"
---

# [[Ausnahme]]

- **Kernkonzept:** Eine Ausnahme (engl. Exception) bezeichnet in der Software-Engineering-Analyse einen unerwarteten oder fehlerhaften Zustand, der während der Ausführung einer Systemoperation auftritt und eine spezielle Behandlung erfordert. Sie wird explizit im Kontext von Use Cases und Operationen dokumentiert, um abweichendes Verhalten von der normalen Ablauflogik zu definieren.
- **Nutzen & Zweck:** Ausnahmen existieren, um die Robustheit und Klarheit der Systemanforderungen zu erhöhen. Sie lösen das Problem, dass unvorhergesehene Situationen (z. B. ungültige Eingaben, fehlende Berechtigungen) in der Analysephase oft vernachlässigt werden, obwohl sie kritische Auswirkungen auf die Funktionalität haben. Durch ihre explizite Dokumentation wird sichergestellt, dass Entwickler und Stakeholder solche Fälle frühzeitig erkennen, priorisieren und in der späteren Implementierung behandeln können. Dies reduziert spätere Nacharbeiten und erhöht die Zuverlässigkeit des Systems.
- **Abgrenzung & Grenzen:** Ausnahmen sollten nicht mit normalen Ablaufvarianten (z. B. optionalen Schritten in Use Cases) verwechselt werden, die Teil der regulären Geschäftslogik sind. Während Alternativen wie Fehlercodes oder Rückgabewerte ebenfalls Fehlerzustände signalisieren können, bieten Ausnahmen den Vorteil, dass sie strukturiert und zentral dokumentiert werden – insbesondere in der Analysephase, wo noch keine Implementierungsdetails feststehen. Sie sind jedoch kein Ersatz für detaillierte Vor- oder Nachbedingungen, sondern ergänzen diese. In frühen Analysephasen sollte man Ausnahmen zudem nicht mit technischen Fehlern (z. B. Netzwerkausfällen) vermischen, da diese oft erst im Design berücksichtigt werden.
- **Beispiel / Code:** ```java
/**
 * Operation: abteilungVerlassen
 * 
 * @param abteilung Die Abteilung, aus der das Mitglied entfernt wird.
 * @throws IllegalArgumentException Falls das Mitglied nicht der Abteilung angehört.
 */
public void abteilungVerlassen(Abteilung abteilung) throws IllegalArgumentException {
    if (!this.abteilungen.contains(abteilung)) {
        throw new IllegalArgumentException("Mitglied gehört nicht der angegebenen Abteilung an.");
    }
    // Normaler Ablauf: Mitglied entfernen, Status prüfen, etc.
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b4
- **Vorgänger / Parent:** [[Use-Case-Beschreibung]]
- **Folgezettel / Unterzettel:**
  - [[Fehlerbehandlung]]
  - [[Wiederherstellungsprozess]]
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Systemrobustheit]]
