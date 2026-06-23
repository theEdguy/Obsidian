---
id: bc0c3b95-16ac-4213-86b9-148f67537716
title: "Dienst"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Dienst]]

- **Kernkonzept:** Ein 'Dienst' im Kontext der Software-Engineering-Analyse bezeichnet ein abstraktes Konzept, das eine funktionale Einheit oder eine wiederkehrende Aktivität innerhalb der Problemdomäne repräsentiert. Es beschreibt eine Leistung oder Funktion, die von einem System oder Akteur erbracht wird, ohne dabei auf technische Implementierungsdetails einzugehen.
- **Nutzen & Zweck:** Das Konzept 'Dienst' existiert, um die funktionalen Anforderungen eines Systems klar und domänenspezifisch zu strukturieren. Es hilft dabei, zentrale Abläufe und Verantwortlichkeiten in der Problemdomäne zu identifizieren und von konkreten Objekten oder Attributen zu trennen. Dadurch wird die Komplexität reduziert, indem wiederkehrende oder übergreifende Funktionen gebündelt und als eigenständige Einheiten betrachtet werden, was die Analyse und spätere Modellierung erleichtert.
- **Abgrenzung & Grenzen:** Ein 'Dienst' sollte nicht genutzt werden, wenn es sich um ein einfaches Attribut, eine quantitative Eigenschaft oder eine triviale Entität handelt, die keine eigenständige Funktionalität besitzt. Im Gegensatz zu einem 'Objekt' oder 'Konzept', das eine Entität mit Zuständen und Eigenschaften beschreibt, fokussiert sich ein 'Dienst' auf das 'Was' einer Aktivität oder Leistung. Es unterscheidet sich von 'Prozessen' oder 'Ereignissen', indem es keine zeitliche Abfolge oder Auslöser modelliert, sondern eine wiederverwendbare Funktion darstellt. Zudem sollte es nicht mit technischen Services (z. B. Webservices) verwechselt werden, da es rein konzeptionell ist.
- **Beispiel / Code:** ```java
// Beispiel: Konzept eines 'Dienstes' in der Problemdomäne 'Vereinsverwaltung'
public class MitgliedschaftsDienst {
    // Verantwortlichkeit: Verwaltung von Mitgliedschaften im Verein
    
    public void mitgliedschaftBeenden(Mitglied mitglied) {
        // Logik zum Beenden der Mitgliedschaft, z. B. Statusänderung und Benachrichtigung
        mitglied.setStatus("passiv");
        benachrichtigungsDienst.sendeBenachrichtigung(mitglied, "Mitgliedschaft beendet");
    }
    
    public void abteilungWechseln(Mitglied mitglied, Abteilung alteAbteilung, Abteilung neueAbteilung) {
        // Logik zum Wechsel der Abteilung, inkl. Validierungen
        alteAbteilung.entferneMitglied(mitglied);
        neueAbteilung.fuegeMitgliedHinzu(mitglied);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3a3
- **Vorgänger / Parent:** [[Fachkonzept]]
- **Folgezettel / Unterzettel:**
  - [[Operation]]
  - [[Verantwortlichkeit]]
- **Querverweise:**
  - [[Problemdomäne]]
  - [[Schnittstelle]]
