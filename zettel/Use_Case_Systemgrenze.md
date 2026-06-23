---
id: 3f8eade3-04fe-43b1-b6a8-da0fc381d032
title: "Use Case Systemgrenze"
date: 2026-06-23
tags:
  - software_engineering
  - systemarchitektur
  - modellierung
  - analyse
  - draft
source: "software_engineering_kapitel_08"
---

# [[Use Case Systemgrenze]]

- **Kernkonzept:** Die [[Systemgrenze]] definiert im Kontext von [[Use_Case|Use Cases]] den Rahmen eines [[Softwaresystem|Softwaresystems]] oder einer [[Komponente]], innerhalb dessen die beschriebenen [[Interaktion]]en und Abläufe stattfinden. Sie trennt das betrachtete System von seiner Umgebung und den beteiligten [[Akteur|Akteuren]] ab und legt fest, welche [[Funktionalität|Funktionalitäten]] innerhalb des Systems liegen und welche außerhalb durch [[Akteur|Akteure]] repräsentiert werden.
- **Nutzen & Zweck:** Die [[Systemgrenze]] dient dazu, den Fokus der [[Analyse]] und [[Modellierung]] klar einzugrenzen. Sie hilft, [[Verantwortlichkeit|Verantwortlichkeiten]] zwischen dem System und externen [[Akteur|Akteuren]] zu klären, Missverständnisse über den Umfang des Systems zu vermeiden und die [[Komplexität]] durch präzise Abgrenzung zu reduzieren. Dadurch wird die Kommunikation über [[Anforderung|Anforderungen]] zwischen [[Stakeholder|Stakeholdern]] erleichtert und die spätere [[Implementierung]] unterstützt. Ohne sie wäre unklar, welche [[Funktionalität|Funktionen]] das System selbst übernehmen muss und welche außerhalb liegen.
- **Abgrenzung & Grenzen:** Die [[Systemgrenze]] sollte nicht genutzt werden, wenn das zu modellierende System noch nicht ausreichend verstanden oder definiert ist, da dies zu falschen Annahmen führen kann. Alternativen wie [[Kontextdiagramm|Kontextdiagramme]] bieten eine höhere [[Abstraktionsebene]], wenn es primär um die Einbettung des Systems in seine Umgebung geht. Zudem ist die [[Systemgrenze]] ungeeignet, um technische [[Implementierungsdetail|Implementierungsdetails]] oder interne [[Systemarchitektur|Systemarchitekturen]] abzubilden – hierfür sind [[Komponentendiagramm|Komponentendiagramme]] oder [[Klassendiagramm|Klassendiagramme]] besser geeignet. Für die detaillierte Modellierung interner Systemprozesse, die keine Interaktion mit externen [[Akteur|Akteuren]] erfordern, eignen sich [[Aktivitätsdiagramm|Aktivitätsdiagramme]] oder [[Zustandsdiagramm|Zustandsdiagramme]] besser.
- **Beispiel / Code:** ```plantuml
@startuml
left to right direction
actor Vereinsmanager
actor MailClient
actor Mitglied
actor Vorstand
actor Kassenwart

rectangle MyClub {
  usecase "Mitglieder verwalten" as UC1
  usecase "Mitglied anlegen" as UC2
  usecase "Mitglied bearbeiten" as UC3
  usecase "Mitglied austragen" as UC4
  usecase "Beitrag abrechnen" as UC5
}

Vereinsmanager --> UC1
MailClient --> UC1
Mitglied --> UC2
Mitglied --> UC4
Vorstand --> UC2
Vorstand --> UC4
Kassenwart --> UC5
UC1 <|-- UC2
UC1 <|-- UC3
UC1 <|-- UC4
@enduml
```

In diesem Beispiel markiert das Rechteck *MyClub* die [[Systemgrenze]]. Alle [[Use_Case|Use Cases]] innerhalb des Rechtecks sind Teil des Systems, während *Vereinsmanager*, *MailClient*, *Mitglied*, *Vorstand* und *Kassenwart* als externe [[Akteur|Akteure]] außerhalb der Grenze agieren. Das Diagramm verdeutlicht, welche [[Funktionalität|Funktionen]] vom System übernommen werden und welche [[Interaktion]]en mit externen [[Akteur|Akteuren]] stattfinden.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c
- **Vorgänger / Parent:** [[Use_Case]]
- **Folgezettel / Unterzettel:**
  - [[Systemgrenze_Definition]]
  - [[Systemgrenze_Abgrenzung]]
- **Querverweise:**
  - [[Akteur]]
  - [[Anwendungsfall]]
