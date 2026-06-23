---
id: 90faad3a-39be-49ad-bd00-7806670c1fef
title: "Systemgrenze"
date: 2026-06-23
tags:
  - software_engineering
  - systemdesign
  - analyse
  - anforderungsanalyse
  - architektur
  - modellierung
  - requirements_engineering
  - draft
source: "software_engineering_kapitel_09"
---

# [[Systemgrenze]]

- **Kernkonzept:** Die [[Systemgrenze]] definiert die [[Abgrenzung]] zwischen einem [[Softwaresystem]] und seiner [[Umgebung]], insbesondere den [[Akteur|Akteuren]] oder [[Fremdsystem|Fremdsystemen]]. Sie legt fest, welche [[Funktionalität|Funktionalitäten]] innerhalb des [[Softwaresystem|Systems]] liegen und welche externen [[Akteur|Akteure]] oder [[System|Systeme]] mit dem [[Softwaresystem]] interagieren. In [[Use-Case-Diagramm|Use-Case-Diagrammen]] wird sie als Rechteck dargestellt und bildet die Grundlage für die [[Use-Case-Analyse]] sowie die präzise Definition des [[Scope|Projektumfangs]].
- **Nutzen & Zweck:** Die [[Systemgrenze]] klärt den [[Scope]] eines Projekts und verhindert [[Scope_Creep]]. Sie ist essenziell für die [[Use-Case-Analyse]], die Identifikation von [[Verantwortlichkeit|Verantwortlichkeiten]] und [[Schnittstelle|Schnittstellen]] sowie für [[Architekturentscheidung|Architekturentscheidungen]]. Ohne sie entstehen [[Missverständnis|Missverständnisse]] zwischen [[Stakeholder|Stakeholdern]] über den Umfang des [[Softwaresystem|Systems]], was zu unklaren [[Anforderung|Anforderungen]] und fehlerhaften [[Implementierung|Implementierungen]] führen kann. Zudem dient sie als Grundlage für die Modellierung von Interaktionen zwischen [[Akteur|Akteuren]] und dem [[Softwaresystem]] und hilft, den funktionalen Umfang präzise zu definieren. Durch die klare Abgrenzung wird die [[Komplexität]] reduziert, die [[Kommunikation]] zwischen [[Stakeholder|Stakeholdern]] verbessert und die Fokussierung auf die [[Kernfunktionalität|Kernfunktionalitäten]] des [[Softwaresystem|Systems]] ermöglicht.
- **Abgrenzung & Grenzen:** Die [[Systemgrenze]] ist eine [[konzeptionelle_Grenze]] und keine [[technische_Grenze]] wie die [[Netzwerkgrenze]]. Sie ersetzt weder die [[Datenmodellierung]] noch die Definition technischer [[Schnittstelle|Schnittstellen]], sondern beschreibt ausschließlich den funktionalen Umfang. Im Gegensatz zu [[Modulgrenze|Modulgrenzen]], die innerhalb des [[Softwaresystem|Systems]] [[Systemkomponente|Komponenten]] trennen, trennt sie das [[Softwaresystem]] von seiner [[Umgebung]]. Sie sollte nicht genutzt werden, um technische [[Implementierung|Implementierungsdetails]] (z. B. [[Datenbank|Datenbanken]], [[Framework|Frameworks]]) zu modellieren, da diese zur internen [[Systemarchitektur]] gehören. Die [[Systemgrenze]] ist zudem keine starre Festlegung, sondern kann sich im Laufe des Projekts anpassen, wenn neue [[Anforderung|Anforderungen]] oder Erkenntnisse hinzukommen. Alternativen wie [[Kontextdiagramm|Kontextdiagramme]] (z. B. in der [[Strukturierte_Analyse]]) fokussieren sich stärker auf [[Datenfluss|Datenflüsse]] statt auf funktionale Interaktionen. Zudem ist die [[Systemgrenze]] ungeeignet, um [[Nicht-funktionale_Anforderung|nicht-funktionale Anforderungen]] (z. B. [[Performance]], [[Sicherheit]]) abzubilden, da sie primär funktionale [[Schnittstelle|Schnittstellen]] beschreibt.
- **Beispiel / Code:** ```plaintext
Beispiel 1: Use Case "[[Mitglieder_verwalten]]"
Systemgrenze:
- Innerhalb: [[MyClub]]-System (z. B. Mitgliederdatenbank, Berechtigungsmanagement, [[Benutzerverwaltung]])
- Außerhalb: [[Vereinsmanager]], [[Mail_Client]], externe [[Authentifizierung|Authentifizierungssysteme]], [[Zahlungsdienstleister]]

Beispiel 2: Online-Shop
Systemgrenze:
- Innerhalb: Produktkatalog, Warenkorb, Bestellabwicklung, [[Benutzerverwaltung]], [[Rechnungsstellung]]
- Außerhalb: [[Logistikpartner]], externe [[API|APIs]] für Versandstatus, [[Zahlungsdienstleister]], [[Kundensupport-Systeme]]
```

```java
// Beispiel: Use-Case-Diagramm (UML) mit Systemgrenze als Rechteck
@startuml
actor "Vereinsmanager" as Manager
actor "Mitglied" as Mitglied

rectangle "Vereinsverwaltungssystem" {
  usecase "Mitglied anlegen" as UC1
  usecase "Mitglied bearbeiten" as UC2
  usecase "Mitglied löschen" as UC3
  usecase "Mitgliederliste exportieren" as UC4
}

Manager --> UC1
Manager --> UC2
Manager --> UC3
Manager --> UC4
Mitglied --> UC2
@enduml
```

*Erläuterung:* Das Rechteck symbolisiert die [[Systemgrenze]]. Die [[Use-Case|Use Cases]] innerhalb des Rechtecks sind Teil des [[Softwaresystem|Systems]], während die [[Akteur|Akteure]] außerhalb liegen und mit dem [[Softwaresystem]] interagieren. Die [[Systemgrenze]] hilft, den funktionalen Umfang des [[Softwaresystem|Systems]] klar zu definieren und externe [[Schnittstelle|Schnittstellen]] zu identifizieren.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a2
- **Vorgänger / Parent:** [[Use-Case-Diagramm]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Use-Case-Diagramm]]
