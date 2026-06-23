---
id: 4c599387-9d87-404a-a470-acc834a19d8a
title: "Aktion"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_08"
---

# [[Aktion]]

- **Kernkonzept:** Eine Aktion in der UML-Modellierung bezeichnet eine ausführbare Einheit innerhalb eines Aktivitätsdiagramms, die eine einzelne Arbeitsschritt oder Verarbeitungsschritt repräsentiert. Sie stellt eine atomare, nicht weiter unterteilbare Tätigkeit dar, die im Rahmen eines Prozesses ausgeführt wird.
- **Nutzen & Zweck:** Aktionen dienen dazu, komplexe Abläufe in kleinere, verständliche und modellierbare Einheiten zu zerlegen. Sie ermöglichen die präzise Darstellung von Workflows, Algorithmen oder Geschäftsprozessen, indem sie die logische Abfolge von Tätigkeiten visualisieren. Dadurch wird die Kommunikation zwischen Entwicklern, Analysten und Stakeholdern verbessert und die Nachvollziehbarkeit von Systemverhalten sichergestellt.
- **Abgrenzung & Grenzen:** Aktionen sollten nicht genutzt werden, wenn es um die Darstellung von Zuständen oder Ereignissen geht – hierfür eignen sich Zustandsdiagramme besser. Im Gegensatz zu Aktivitäten, die aus mehreren Aktionen bestehen können, sind Aktionen atomar und nicht weiter zerlegbar. Für hochgradig parallele oder ereignisgesteuerte Abläufe können Aktionen zu starr sein; hier bieten sich Petri-Netze oder erweiterte UML-Konstrukte wie Signale an.
- **Beispiel / Code:** ```java
// Beispiel für eine Aktion in einem Aktivitätsdiagramm (pseudocode)
public class MitgliedVerwalten {
    // Aktion: Mitglied anlegen
    public void mitgliedAnlegen(String name, String adresse) {
        Mitglied neuesMitglied = new Mitglied(name, adresse);
        datenbank.speichern(neuesMitglied);
    }
    
    // Aktion: Mitglied löschen
    public void mitgliedLoeschen(Mitglied mitglied) {
        datenbank.loeschen(mitglied);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a1
- **Vorgänger / Parent:** [[Aktivitätsdiagramm_Bausteine]]
- **Folgezettel / Unterzettel:**
  - [[Geschachtelte_Aktion]]
- **Querverweise:**
  - [[Aktivitätsdiagramm]]
