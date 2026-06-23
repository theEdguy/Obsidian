---
id: 238782ba-2338-4c94-9a77-1b1b1c3062e9
title: "Verteilungsdiagramm"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - systemdesign
  - architektur
  - diagramm
  - verteilung
  - draft
source: "software_engineering_kapitel_10"
---

# [[Verteilungsdiagramm]]

- **Kernkonzept:** Ein [[Verteilungsdiagramm|Verteilungsdiagramm]] (Deployment Diagram) ist ein [[UML]]-Diagramm, das die physische [[Laufzeitkonfiguration]] eines [[Softwaresystem|Systems]] visualisiert, indem es die Verteilung von [[Komponente|Komponenten]] auf physische [[Knoten]] (z. B. [[Server]], Rechner, Prozessoren) sowie deren [[Kommunikationsbeziehung|Kommunikationsbeziehungen]] zur [[Laufzeit]] darstellt. Es zeigt, wie ein System in einer realen [[Betriebsumgebung]] konfiguriert ist und unterstützt die Planung von [[Infrastruktur]] und [[Systemintegration]].
- **Nutzen & Zweck:** Verteilungsdiagramme dienen der Dokumentation und Planung der [[Infrastruktur]] eines [[Softwaresystem|Systems]], insbesondere in [[Verteiltes_System|verteilten Systemen]]. Sie lösen das Problem der Unklarheit über die physische Verteilung von [[Komponente|Komponenten]], deren [[Abhängigkeit|Abhängigkeiten]] und die [[Kommunikationsbeziehung|Kommunikationsbeziehungen]] zwischen verschiedenen [[Knoten]]. Dadurch ermöglichen sie eine bessere Planung von [[Ressource|Ressourcen]], [[Lastverteilung]], [[Skalierbarkeit]], [[Fehlertoleranz]] und [[Performance]]. Zudem unterstützen sie die Analyse von [[Systemintegration]] und die Identifikation potenzieller Engpässe oder Single Points of Failure.
- **Abgrenzung & Grenzen:** Verteilungsdiagramme sind nicht geeignet, um [[Logik]], [[Algorithmus|Algorithmen]] oder dynamische [[Ablauf|Abläufe]] (z. B. [[Interaktion]] zwischen [[Objekt|Objekten]]) darzustellen. Hierfür sind [[Sequenzdiagramm|Sequenzdiagramme]], [[Aktivitätsdiagramm|Aktivitätsdiagramme]] oder [[Zustandsdiagramm|Zustandsdiagramme]] besser geeignet. Im Gegensatz zu [[Komponentendiagramm|Komponentendiagrammen]], die die logische Aufteilung eines [[Softwaresystem|Systems]] zeigen, fokussieren Verteilungsdiagramme auf die physische Verteilung auf [[Hardware]]. Sie sind zudem ungeeignet für detaillierte [[Implementierung]]sdetails oder die Darstellung von [[Entwurfsmuster|Mustern]] wie [[Observer_Pattern|Observer]] oder [[Singleton]].
- **Beispiel / Code:** ```uml
@startuml
node "kundenPC" as client {
  artifact "MyClub.jar" as myclub
  component "MyClub" as myclub_comp
}

node "lzs.myclub.de" as server {
  component "LizenzServer" as license
  component ":MailClient" as mail
}

client --> server : Mapi

node "Web Server" {
  artifact "WebApp.war"
}

node "Application Server" {
  artifact "BusinessLogic.jar"
}

node "Database Server" {
  database "MyClubDB"
}

"Web Server" --> "Application Server" : HTTP
"Application Server" --> "Database Server" : JDBC
@enduml
```

*Erklärung:* Das Diagramm zeigt zwei Szenarien:
1. Ein [[Client-Server-System]] mit einem [[Knoten]] `kundenPC`, der die Anwendung `MyClub.jar` ausführt, und einem [[Server]] `lzs.myclub.de`, der [[Komponente|Komponenten]] wie `LizenzServer` und `MailClient` hostet. Die [[Kommunikationsbeziehung|Kommunikation]] erfolgt über `Mapi`.
2. Ein dreistufiges System mit [[Web Server]], [[Application Server]] und [[Database Server]], das die physische Verteilung von [[Artefakt|Artefakten]] (`WebApp.war`, `BusinessLogic.jar`) und deren [[Kommunikationsbeziehung|Kommunikationsprotokolle]] (HTTP, JDBC) darstellt.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3a
- **Vorgänger / Parent:** [[Verteilungsarchitektur]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
