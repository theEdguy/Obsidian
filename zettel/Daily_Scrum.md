---
id: 423451d3-5b66-483a-adab-35a12785ffbe
title: "Daily Scrum"
date: 2026-06-23
tags:
  - software_engineering
  - daily_scrum
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Daily Scrum]]

- **Kernkonzept:** Das Daily Scrum ist ein tägliches, zeitlich begrenztes Meeting im Scrum-Framework, bei dem das Entwicklungsteam den Fortschritt in Richtung des Sprint-Ziels synchronisiert, Hindernisse identifiziert und den nächsten Arbeitstag plant.
- **Nutzen & Zweck:** Das Daily Scrum existiert, um Transparenz über den aktuellen Stand der Arbeit zu schaffen, die Zusammenarbeit im Team zu fördern und schnell auf Blockaden oder Abweichungen vom Sprint-Ziel reagieren zu können. Es löst das Problem der isolierten Arbeitsweise und ermöglicht eine kontinuierliche Anpassung der Planung, ohne den Overhead längerer Meetings zu verursachen.
- **Abgrenzung & Grenzen:** Das Daily Scrum sollte nicht als Statusbericht für externe Stakeholder oder zur detaillierten Problemlösung genutzt werden. Es unterscheidet sich von klassischen Statusmeetings durch seine strikte Zeitbegrenzung (max. 15 Minuten), Fokussierung auf das Sprint-Ziel und die Selbstorganisation des Teams. Alternativen wie wöchentliche Meetings oder asynchrone Updates eignen sich besser für komplexe Diskussionen oder Teams mit geringer Interdependenz.
- **Beispiel / Code:** ```java
// Beispiel für eine einfache Struktur zur Dokumentation von Daily Scrum-Inhalten
public class DailyScrum {
    private String teamMember;
    private String yesterdayProgress;
    private String todayPlan;
    private String impediments;

    public DailyScrum(String teamMember, String yesterdayProgress, 
                     String todayPlan, String impediments) {
        this.teamMember = teamMember;
        this.yesterdayProgress = yesterdayProgress;
        this.todayPlan = todayPlan;
        this.impediments = impediments;
    }
    
    // Getter und Setter für die Felder
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9b2
- **Vorgänger / Parent:** [[Scrum-Events]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Scrum-Events]]
  - [[Scrum]]
