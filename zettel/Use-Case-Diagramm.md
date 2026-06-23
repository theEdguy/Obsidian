---
id: b8e27e2f-e1b8-470c-af02-606deca0b274
title: "Use-Case-Diagramm"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - analyse
  - diagramme
  - use_case_diagramme
  - funktionale_anforderungen
  - anforderung
  - diagramm
  - draft
source: "software_engineering_kapitel_12"
---

# [[Use-Case-Diagramm]]

- **Kernkonzept:** Ein [[Use-Case-Diagramm]] ist eine grafische [[Darstellung]] in der [[UML]], die die [[Interaktion]] zwischen [[Akteur|Akteuren]] (z. B. [[Benutzer|Benutzern]], externen [[System|Systemen]] oder [[Stakeholder|Stakeholdern]]) und einem [[Softwaresystem]] abbildet, um [[funktionale_Anforderung|funktionale Anforderungen]] aus [[Benutzer|Benutzersicht]] zu visualisieren. Es strukturiert [[Use_Case|Use-Cases]] und deren [[Beziehung|Beziehungen]] (z. B. <<include>>, <<extend>>) und definiert die [[Systemgrenze|Systemgrenzen]], um die [[Funktionalität]] des Systems klar zu umreißen.
- **Nutzen & Zweck:** Ein [[Use-Case-Diagramm]] dient primär dazu, die [[Anforderung|Anforderungen]] an ein [[Softwaresystem]] frühzeitig zu erfassen, zu dokumentieren und für [[Stakeholder]], [[Kunde|Kunden]] sowie [[Entwicklungsteam|Entwicklungsteams]] verständlich zu kommunizieren. Es hilft, die [[Perspektive]] der [[Benutzer]] einzunehmen, zentrale [[Systemfunktion|Systemfunktionen]] zu identifizieren und die [[Kommunikation]] zwischen allen Beteiligten zu verbessern. Durch die klare Abgrenzung von [[Systemgrenze|Systemgrenzen]] und [[Akteur|Akteuren]] wird die [[Komplexität]] reduziert, was die Grundlage für [[Architektur]], [[Design]], [[Test]] und [[Implementierung]] schafft. Zudem ermöglicht es eine [[Priorisierung]] von [[Entwicklungsaufgabe|Entwicklungsaufgaben]] und unterstützt eine [[use-case-getriebene_Entwicklung]], indem es eine [[Übersicht]] über die [[Funktionalität]] des Systems bietet. Es schafft eine gemeinsame Basis für die Zusammenarbeit zwischen [[Auftraggeber|Auftraggebern]] und [[Entwicklungsteam|Entwicklungsteams]] und erleichtert die [[Validierung]] der [[Anforderung|Anforderungen]] durch [[Feedback]]-Schleifen. Darüber hinaus unterstützt es die Planung iterativer [[Entwicklungsprozess|Entwicklungsprozesse]], reduziert [[Missverständnis|Missverständnisse]] zwischen [[Stakeholder|Stakeholdern]] und dient als Ausgangspunkt für detailliertere [[Analyse]]-Schritte wie [[Sequenzdiagramm|Sequenzdiagramme]] oder [[Aktivitätsdiagramm|Aktivitätsdiagramme]].
- **Abgrenzung & Grenzen:** Ein [[Use-Case-Diagramm]] sollte nicht genutzt werden, um [[technische_Implementierung|technische Details]], [[Algorithmus|Algorithmen]], zeitliche [[Ablauf|Abläufe]] (z. B. [[Workflow|Workflows]]), interne [[Systemstruktur|Systemstrukturen]] oder [[nicht-funktionale_Anforderung|nicht-funktionale Anforderungen]] wie [[Performance]], [[Sicherheit]] oder [[Skalierbarkeit]] darzustellen. Es eignet sich nicht für die Modellierung von [[Datenfluss|Datenflüssen]], detaillierten [[Prozessmodell|Prozessmodellen]] mit Verzweigungen (hierfür sind [[Aktivitätsdiagramm|Aktivitätsdiagramme]] oder [[BPMN]] besser geeignet) oder [[Zustandsänderung|Zustandsänderungen]] (hierfür sind [[Zustandsdiagramm|Zustandsdiagramme]] vorzuziehen). Für die Darstellung von [[Systeminteraktion|Systeminteraktionen]] oder zeitlichen [[Ablauf|Abläufen]] sind [[Sequenzdiagramm|Sequenzdiagramme]] oder [[Kommunikationsdiagramm|Kommunikationsdiagramme]] besser geeignet. Bei komplexen [[Geschäftsprozess|Geschäftsprozessen]] mit vielen Ausnahmen oder Sonderfällen sind andere [[Modellierungssprache|Modellierungssprachen]] wie [[BPMN]] vorzuziehen. Zudem eignet es sich nicht zur Abbildung von [[Datenstruktur|Datenstrukturen]] oder [[Algorithmus|Algorithmen]], die in [[Klassendiagramm|Klassendiagrammen]] oder [[Pseudocode]] besser dargestellt werden.
- **Beispiel / Code:** ```plantuml
@startuml
left to right direction
actor "[[Vereinsmanager]]" as Vereinsmanager
actor "[[Mitglied]]" as Mitglied
actor "[[Administrator]]" as Admin
actor "[[MailClient|Mail-Client]]" as MailClient

rectangle "Vereinsverwaltung" as MyClub {
  usecase "[[Mitglieder_verwalten]]" as UC1
  usecase "[[Mitglied_anlegen]]" as UC2
  usecase "[[Mitglied_bearbeiten]]" as UC3
  usecase "[[Mitglied_löschen]]" as UC4
  usecase "[[Abteilung_zuweisen]]" as UC5
  usecase "[[Benutzer_authentifizieren]]" as UC6
}

Vereinsmanager --> UC1
Vereinsmanager --> UC2
Vereinsmanager --> UC3
Vereinsmanager --> UC4
Vereinsmanager --> UC5
Mitglied --> UC2
Admin --> UC1
Admin --> UC6
MailClient --> UC1

UC2 .> UC1 : <<include>>
UC3 .> UC1 : <<include>>
UC4 .> UC1 : <<include>>
UC5 .> UC1 : <<extend>>
@enduml


@startuml
left to right direction
actor "[[Mitglied]]" as member
actor "[[Administrator]]" as admin

rectangle MyClub {
  usecase "[[Mitglieder_verwalten]]" as UC1
  usecase "[[Mitglied_hinzufügen]]" as UC2
  usecase "[[Mitglied_bearbeiten]]" as UC3
  usecase "[[Mitglied_löschen]]" as UC4
}

member --> UC1
admin --> UC2
admin --> UC3
admin --> UC4
UC1 <|-- UC2
UC1 <|-- UC3
UC1 <|-- UC4
@enduml
```

Die Beispiele zeigen [[Use-Case-Diagramm|Use-Case-Diagramme]] für ein [[Vereinsverwaltungssystem]]. Im ersten Diagramm interagiert der [[Vereinsmanager]] mit allen [[Use_Case|Use-Cases]], während das [[Mitglied]] nur das [[Mitglied_anlegen]] auslösen kann. Der [[Administrator]] ist für die [[Authentifizierung]] zuständig und interagiert mit dem [[Use_Case|Use-Case]] [[Benutzer_authentifizieren]]. Der [[MailClient]] ist ein externes [[System]], das mit dem [[Use_Case|Use-Case]] [[Mitglieder_verwalten]] verbunden ist. Die <<include>>-Beziehungen verdeutlichen, dass [[Mitglied_anlegen]], [[Mitglied_bearbeiten]] und [[Mitglied_löschen]] Teil des übergeordneten [[Use_Case|Use-Cases]] [[Mitglieder_verwalten]] sind. Die <<extend>>-Beziehung zeigt, dass [[Abteilung_zuweisen]] eine optionale Erweiterung darstellt. Das zweite Diagramm veranschaulicht eine vereinfachte Variante mit Fokus auf die [[Beziehung|Beziehungen]] zwischen [[Akteur|Akteuren]] und [[Use_Case|Use-Cases]].

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4b
- **Vorgänger / Parent:** [[UML]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[UML]]
  - [[Anforderungserhebung]]
