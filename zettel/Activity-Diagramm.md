---
id: 3137a21c-9405-41b5-9c40-bda573e9b8c4
title: "Activity-Diagramm"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - prozessdesign
  - draft
source: "SWE Slides (Folien 181-195)"
---

# [[Activity-Diagramm]]

- **Kernkonzept:** Ein [[Activity-Diagramm]] ist eine grafische [[Modellierungssprache|Modellierungssprache]] in der [[UML]], die den [[Kontrollfluss|Kontrollfluss]] und [[Datenfluss]] von [[Aktivität|Aktivitäten]] in einem [[System]] darstellt. Es eignet sich zur Visualisierung von [[Prozess|Prozessen]], [[Algorithmus|Algorithmen]] oder [[Use-Case|Use-Cases]].
- **Nutzen & Zweck:** Das [[Activity-Diagramm]] dient der klaren Darstellung komplexer [[Ablauf|Abläufe]] und [[Entscheidung|Entscheidungen]] in [[System|Systemen]]. Es hilft, [[Parallelität|parallele Prozesse]] zu modellieren, [[Schnittstelle|Schnittstellen]] zwischen [[Komponente|Komponenten]] zu identifizieren und [[Anforderung|Anforderungen]] an die [[Logik]] eines [[Systems]] zu präzisieren.
- **Abgrenzung & Grenzen:** Nicht geeignet für die detaillierte Modellierung von [[Zustand|Zuständen]] einzelner [[Objekt|Objekte]] (hierfür [[Zustandsdiagramm|Zustandsdiagramme]] verwenden) oder für die Darstellung von [[Klassenstruktur|Klassenstrukturen]] (hierfür [[Klassendiagramm|Klassendiagramme]]). Im Gegensatz zu [[Sequenzdiagramm|Sequenzdiagrammen]] liegt der Fokus nicht auf der [[Interaktion]] zwischen [[Akteur|Akteuren]], sondern auf dem [[Ablauf]] von [[Aktivität|Aktivitäten]].
- **Beispiel / Code:** ```uml
@startuml
start
:Eis zerkleinern;
if (Glas leer?) then (ja)
  :Glas bereitstellen;
else (nein)
  :Glas leeren;
endif
:Cocktail mixen;
:trinken;
stop
@enduml
```
