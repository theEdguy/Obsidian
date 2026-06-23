---
id: fd1707d3-6d8b-4970-bc31-b890ccb568b9
title: "Kommunikationsdiagramm"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - uml
  - diagrammtyp
  - interaktion
  - draft
source: "software_engineering_kapitel_13"
---

# [[Kommunikationsdiagramm]]

- **Kernkonzept:** Ein [[Kommunikationsdiagramm]] (auch Kollaborationsdiagramm genannt) ist eine [[UML]]-Diagrammart, die die [[Interaktion|Interaktionen]] zwischen [[Objekt|Objekten]] oder [[Rolle|Rollen]] in einem System durch [[Nachricht|Nachrichtenflüsse]] darstellt und dabei die strukturellen [[Beziehung|Beziehungen]] der beteiligten [[Element|Elemente]] betont. Es visualisiert, wie [[Objekt|Objekte]] zur Erfüllung einer bestimmten Funktionalität zusammenarbeiten, wobei die räumliche Anordnung und die [[Verbindung|Verbindungen]] der [[Objekt|Objekte]] im Vordergrund stehen.
- **Nutzen & Zweck:** Kommunikationsdiagramme existieren, um die dynamischen Aspekte eines Systems aus einer strukturorientierten Perspektive zu modellieren. Sie lösen das Problem, dass reine [[Klassendiagramm|Klassendiagramme]] keine [[Ablauf|Abläufe]] darstellen und [[Sequenzdiagramm|Sequenzdiagramme]] zwar zeitliche Abfolgen zeigen, aber die statischen [[Beziehung|Beziehungen]] zwischen [[Objekt|Objekten]] weniger deutlich machen. Durch die Kombination von [[Nachricht|Nachrichtenfluss]] und [[Objektstruktur]] helfen sie, komplexe [[Interaktion|Interaktionen]] in verteilten Systemen oder bei der Zusammenarbeit mehrerer [[Komponente|Komponenten]] zu verstehen und zu dokumentieren. Sie dienen insbesondere dazu, die [[Zusammenarbeit]] und den [[Nachricht|Nachrichtenaustausch]] zwischen [[Objekt|Objekten]] in einem [[Anwendungsfall]] zu visualisieren, wenn die räumliche Anordnung oder die [[Beziehung|Beziehungen]] der [[Objekt|Objekte]] im Vordergrund stehen. Dies erleichtert die Analyse von [[Systemverhalten]] und die Identifikation von [[Abhängigkeit|Abhängigkeiten]], ohne den zeitlichen Verlauf in den Mittelpunkt zu stellen. Kommunikationsdiagramme unterstützen somit die Modellierung komplexer [[Ablauf|Abläufe]] und fördern das Verständnis für [[lose_Kopplung|lose Kopplung]] und [[Kohäsion]] in der [[Softwarearchitektur]].
- **Abgrenzung & Grenzen:** Kommunikationsdiagramme sollten nicht genutzt werden, wenn die zeitliche Abfolge der [[Nachricht|Nachrichten]] von zentraler Bedeutung ist – hier sind [[Sequenzdiagramm|Sequenzdiagramme]] besser geeignet, da sie explizit [[Lebenslinie|Lebenslinien]] und [[Steuerungsfokus]] darstellen. Sie eignen sich ebenfalls weniger für die Darstellung sehr einfacher [[Interaktion|Interaktionen]] oder wenn die strukturellen [[Beziehung|Beziehungen]] der [[Objekt|Objekte]] irrelevant sind. Im Vergleich zu [[Aktivitätsdiagramm|Aktivitätsdiagrammen]] fehlt ihnen die Fähigkeit, [[Kontrollfluss|Kontrollflüsse]] wie [[Entscheidung|Entscheidungen]], [[Schleife|Schleifen]] oder parallele [[Ablauf|Abläufe]] abzubilden, da diese durch zusätzliche Notationen oder Fragmente umständlich dargestellt werden müssen. Für die Modellierung von [[Algorithmus|Algorithmen]] oder [[Geschäftsprozess|Geschäftsprozessen]] sind sie daher ungeeignet. Zudem erschwert die fehlende explizite Darstellung von [[Objektzustand|Objektzuständen]] über die Zeit die Nachverfolgung von [[Zustandsänderung|Zustandsänderungen]].
- **Beispiel / Code:** ```java
// Beispiel: Vereinfachte Darstellung eines Kommunikationsdiagramms als UML-Textnotation
// (Hinweis: Kein ausführbarer Code, sondern strukturelle Beschreibung mit Nummerierung der Nachrichten)

@startuml
actor [[Nutzer]]
participant "[[MitgliedVerwaltung]]" as mv
participant "[[Mitglied]]" as m
participant "[[Datenbank]]" as db

Nutzer -> mv: 1: Mitglied anlegen(name, adresse)
mv -> m: 2: erstelleMitglied(name, adresse)
m -> db: 3: speichereMitglied()
db --> m: 4: Rückgabewert
m --> mv: 5: Mitglied-Objekt
mv --> Nutzer: 6: Bestätigung
@enduml

// Alternativ: Textuelle UML-Notation für Kommunikationsdiagramme
// Objekt1 -> Objekt2: 1: nachricht1(argument)
// Objekt2 -> Objekt3: 2: nachricht2()
// Objekt3 --> Objekt1: 3: antwort()
// 
// In einem Kommunikationsdiagramm werden die Objekte als Rechtecke dargestellt,
// verbunden durch Linien, an denen die Nachrichten als Pfeile mit Beschriftungen
// (z. B. "1: nachricht1(argument)") annotiert sind. Die Nummerierung gibt die
// Reihenfolge der Nachrichten an, während die strukturellen Beziehungen der
// Objekte durch die Verbindungslinien visualisiert werden.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d2
- **Vorgänger / Parent:** [[UML]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
