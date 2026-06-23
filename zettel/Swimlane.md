---
id: 78a48587-c7e1-4dc3-b047-5faab88c49a8
title: "Swimlane"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - prozessmodellierung
  - organisation
  - modellierung
  - verantwortlichkeit
  - draft
source: "software_engineering_kapitel_08"
---

# [[Swimlane]]

- **Kernkonzept:** Eine [[Swimlane]] ist ein [[Strukturierungselement]] in [[Activity-Diagramm|Activity-Diagrammen]], das [[Aktivität|Aktivitäten]] nach [[Verantwortlichkeit|Verantwortlichkeiten]], [[Organisationseinheit|Organisationseinheiten]], [[Akteur|Akteuren]] oder [[System|Systemen]] gruppiert. Sie trennt [[Prozess|Prozesse]] in logische Bereiche und visualisiert, welche Einheit für bestimmte [[Aktion|Aktionen]] zuständig ist.
- **Nutzen & Zweck:** [[Swimlane|Swimlanes]] verdeutlichen die [[Verteilung]] von [[Aufgabe|Aufgaben]] in [[Geschäftsprozess|Geschäftsprozessen]] oder [[Use-Case|Use-Cases]] und helfen, [[Schnittstelle|Schnittstellen]] zwischen [[Rolle|Rollen]], [[System|Systemen]] oder Abteilungen zu identifizieren. Sie lösen das Problem unklarer [[Zuständigkeit|Zuständigkeiten]], indem sie auf einen Blick zeigen, wer (z. B. [[Abteilung|Abteilungen]], [[Rolle|Rollen]] oder [[Systemkomponente|Systemkomponenten]]) welche [[Aufgabe|Aufgaben]] übernimmt. Dies fördert die [[Transparenz]] in [[Kollaborationsmodell|Kollaborationsmodellen]] und strukturiert die [[Zusammenarbeit]] in komplexen [[Workflow|Workflows]].
- **Abgrenzung & Grenzen:** [[Swimlane|Swimlanes]] sind nicht geeignet für die Modellierung von [[Datenfluss|Datenflüssen]] ohne [[Organisationsbezug]] oder für die Darstellung von [[Zustand|Zuständen]] einzelner [[Objekt|Objekte]]. Sie sollten vermieden werden, wenn der Fokus auf rein technischen [[Ablauf|Abläufen]] ohne organisatorische oder akteursbezogene [[Verantwortlichkeit|Verantwortlichkeiten]] liegt, da sie dann überflüssig sind. Alternativen wie einfache [[Activity-Diagramm|Activity-Diagramme]] ohne [[Swimlane|Swimlanes]] eignen sich besser für algorithmische oder datenflussorientierte [[Darstellung|Darstellungen]]. Zudem sind [[Swimlane|Swimlanes]] weniger geeignet für sehr feingranulare oder hochdynamische [[Prozess|Prozesse]], bei denen [[Verantwortlichkeit|Verantwortlichkeiten]] häufig wechseln oder nicht klar abgrenzbar sind. Im Gegensatz zu [[Partition_(UML)|Partitionen]] in [[UML]] sind [[Swimlane|Swimlanes]] explizit auf [[Organisationseinheit|Organisationseinheiten]] oder [[Akteur|Akteure]] ausgerichtet.
- **Beispiel / Code:** ```uml
@startuml
|Mitglied|
  :Mitglied anmelden;
|System|
  :Daten validieren;
  :Mitglied in Datenbank eintragen;
|E-Mail-System|
  :Bestätigungsmail senden;
@enduml
```

Das Beispiel zeigt die [[Verantwortlichkeit|Verantwortungsteilung]] zwischen [[Mitglied]], [[System]] und [[E-Mail-System]] in einem [[Anmeldeprozess]].

```uml
@startuml
|MyClub|
start
:Nachricht an die Abteilungsleitung generieren;
|Mail Client|
:Mail versenden;
:Versand protokollieren;
stop
@enduml
```

Hier wird die [[Interaktion]] zwischen einer [[Organisationseinheit]] (MyClub) und einem [[Mail-Client]] dargestellt.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a6
- **Vorgänger / Parent:** [[Aktivitätsdiagramm_Bausteine]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Aktivitätsdiagramm]]
