---
id: fb547d47-aaf0-4e41-8f58-e5da522916ac
title: "Verteilungsdiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - systemdesign
  - architektur
  - draft
source: "SWE Slides (Folien 211-225)"
---

# [[Verteilungsdiagramm]]

- **Kernkonzept:** Ein [[Verteilungsdiagramm|Verteilungsdiagramm]] (Deployment Diagram) visualisiert die [[Laufzeitkonfiguration]] eines Systems, indem es die Verteilung von [[Komponente|Komponenten]] auf physische [[Knoten]] (z. B. Rechner, Prozessoren) und deren [[Kommunikationsbeziehung|Kommunikationsbeziehungen]] darstellt.
- **Nutzen & Zweck:** Es hilft, die [[Systemarchitektur]] zur [[Laufzeit]] zu dokumentieren und zu planen, insbesondere bei verteilten Systemen. Dadurch wird die [[Skalierbarkeit]], [[Fehlertoleranz]] und [[Performance]] des Systems besser analysierbar.
- **Abgrenzung & Grenzen:** Nicht geeignet für die Darstellung von [[Dynamik]] (z. B. [[Ablauf]] oder [[Interaktion]]), hierfür sind [[Sequenzdiagramm|Sequenzdiagramme]] oder [[Aktivitätsdiagramm|Aktivitätsdiagramme]] besser geeignet. Verteilungsdiagramme zeigen keine [[Logik]] oder [[Algorithmus|Algorithmen]].
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
@enduml
```
