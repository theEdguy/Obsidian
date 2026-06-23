---
id: 020c11b0-a80b-4ddc-8d7b-c32abe78f008
title: "Lebenslinie"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - uml-element
  - interaktion
  - draft
source: "software_engineering_kapitel_13"
---

# [[Lebenslinie]]

- **Kernkonzept:** Eine [[Lebenslinie]] (engl. 'Lifeline') in der [[UML]]-Modellierung repräsentiert die Existenz eines [[Objekt|Objekts]] oder [[Akteur|Akteurs]] über einen bestimmten Zeitraum innerhalb eines [[Sequenzdiagramm|Sequenzdiagramms]] und visualisiert dessen [[Interaktion|Interaktionen]] mit anderen [[Entität|Entitäten]], um den zeitlichen Ablauf von [[Nachricht|Nachrichten]] und [[Operation|Operationen]] darzustellen. Sie zeigt zudem, wann ein [[Objekt]] erzeugt, aktiv ist und zerstört wird.
- **Nutzen & Zweck:** Lebenslinien dienen dazu, den dynamischen Ablauf von [[Interaktion|Interaktionen]] zwischen [[Objekt|Objekten]] oder [[Akteur|Akteuren]] in einem [[System]] zu modellieren und das Problem der zeitlichen Abhängigkeiten sowie der Dauer der Existenz von [[Objekt|Objekten]] während eines Prozesses klar und nachvollziehbar abzubilden. Dadurch wird die Analyse des [[Systemverhalten|Systemverhaltens]] erleichtert, [[Schnittstelle|Schnittstellen]] identifiziert und die Kommunikation zwischen [[Entwickler|Entwicklern]], [[Designer|Designern]] und [[Stakeholder|Stakeholdern]] verbessert. Sie lösen insbesondere das Problem, komplexe [[Prozess|Prozesse]] mit mehreren [[Akteur|Akteuren]] und [[Nachricht|Nachrichten]] in ihrer zeitlichen Reihenfolge verständlich zu strukturieren.
- **Abgrenzung & Grenzen:** Lebenslinien sollten nicht genutzt werden, um statische [[Struktur|Strukturen]] oder Beziehungen zwischen [[Klasse|Klassen]] darzustellen – hierfür eignen sich [[Klassendiagramm|Klassendiagramme]] besser. Im Gegensatz zu [[Aktivitätsdiagramm|Aktivitätsdiagrammen]], die den [[Kontrollfluss]] von [[Aktivität|Aktivitäten]] zeigen, fokussieren Lebenslinien auf die [[Interaktion]] spezifischer [[Instanz|Instanzen]]. Zudem sind sie ungeeignet für die Modellierung von [[Zustandsänderung|Zustandsänderungen]], wofür [[Zustandsdiagramm|Zustandsdiagramme]] verwendet werden. Für die Darstellung räumlicher Verteilungen oder struktureller Beziehungen zwischen [[Objekt|Objekten]] sind [[Kommunikationsdiagramm|Kommunikationsdiagramme]] besser geeignet, da diese die Verbindungen zwischen [[Entität|Entitäten]] betonen. Lebenslinien stoßen auch an Grenzen, wenn komplexe logische Bedingungen oder parallele Abläufe detailliert abgebildet werden sollen – hierfür sollten [[Fragment (UML)|Fragmente]] in [[Sequenzdiagramm|Sequenzdiagrammen]] genutzt werden.
- **Beispiel / Code:** ```java
// Beispiel: UML-Sequenzdiagramm (textuelle Notation) mit Lebenslinien und Aktivierungsphasen
participant "Nutzer" as Nutzer
participant "MitgliedVerwaltung" as System
participant "Datenbank" as DB

Nutzer -> System: abteilungVerlassen(abteilungId)
activate System
System -> DB: datenAktualisieren(abteilungId, nutzerId)
activate DB
DB --> System: bestätigung
DB -> DB: logEintragErstellen()
deactivate DB
System --> Nutzer: Bestätigung senden()
System -> Nutzer: Benachrichtigung bei [[Statusänderung|Statusänderungen]]()
deactivate System
```

// Jede vertikale Linie (z. B. unter 'Nutzer', 'System', 'DB') repräsentiert eine Lebenslinie,
die die Existenz und Aktivität der [[Objekt|Objekte]] während der [[Interaktion]] zeigt.
// Die 'activate'- und 'deactivate'-Markierungen kennzeichnen die Aktivierungsphasen der [[Objekt|Objekte]].

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1a
- **Vorgänger / Parent:** [[Sequenzdiagramm]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
