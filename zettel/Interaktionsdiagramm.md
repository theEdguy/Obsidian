---
id: 83b03d5b-7a03-4f14-be8e-6d788343d508
title: "Interaktionsdiagramm"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - modellierung
  - dynamische_analyse
  - draft
source: "SWE Slides (Folien 286-300)"
---

# [[Interaktionsdiagramm]]

- **Kernkonzept:** Ein [[Interaktionsdiagramm]] ist ein [[UML-Diagramm]], das die [[Interaktion|Interaktionen]] zwischen [[Objekt|Objekten]] oder [[Komponente|Komponenten]] in einem [[System]] darstellt, um das dynamische [[Verhalten]] zu modellieren und [[Ablauf|Abläufe]] sowie [[Verantwortlichkeit|Verantwortlichkeiten]] zu klären.
- **Nutzen & Zweck:** Es unterstützt die [[Analyse]] und das [[Design]] von [[System|Systemen]], indem es [[Nachrichtenfluss|Nachrichtenflüsse]] und [[Zusammenarbeit|Zusammenarbeiten]] zwischen [[Objekt|Objekten]] oder [[Komponente|Komponenten]] visualisiert. Dadurch werden [[Design]]-Entscheidungen dokumentiert und [[Fehler]] in der [[Logik]] frühzeitig erkannt. Besonders nützlich ist es zur Klärung von [[Ablauf|Abläufen]] in [[Event-gesteuertes_System|Event-gesteuerten Systemen]] oder bei der Anwendung von [[Entwurfsmuster|Mustern]] wie dem [[Observer_Pattern]].
- **Abgrenzung & Grenzen:** Nicht geeignet für die Darstellung statischer [[Struktur|Strukturen]] (hierfür [[Klassendiagramm]] verwenden). Bei komplexen [[System|Systemen]] kann es unübersichtlich werden und ersetzt keine detaillierte [[Dokumentation]] oder [[Implementierung]]. Es umfasst spezifischere [[Diagrammtyp|Diagrammtypen]] wie [[Sequenzdiagramm|Sequenzdiagramme]] und [[Kommunikationsdiagramm|Kommunikationsdiagramme]], die unterschiedliche Schwerpunkte setzen (z. B. zeitliche Abfolge vs. strukturelle Beziehungen).
- **Beispiel / Code:** ```java
// Beispiel für ein [[Sequenzdiagramm]] (Teil eines [[Interaktionsdiagramm|Interaktionsdiagramms]])
Objekte: [Benutzer, Controller, Model, View]
Nachrichten:
1. Benutzer → Controller: login(benutzername, passwort)
2. Controller → Model: validiere(benutzername, passwort)
3. Model → Controller: true/false
4. Controller → View: zeigeErgebnis()

// Alternativ: [[Kommunikationsdiagramm]]-Beispiel (fokussiert auf strukturelle Beziehungen)
Objekte: [A:Benutzer, B:Controller, C:Model, D:View]
Nachrichten:
A → B: 1: login(benutzername, passwort)
B → C: 1.1: validiere(benutzername, passwort)
C → B: 1.2: true/false
B → D: 2: zeigeErgebnis()
```
