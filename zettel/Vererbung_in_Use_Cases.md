---
id: 5b7a7318-ca5d-4ded-902b-ae0928063312
title: "Vererbung_in_Use_Cases"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - use_case_modellierung
  - objektorientierter_entwurf
  - software_architektur
  - vererbung
  - draft
source: "Klausur_Referenz"
---

# [[Vererbung_in_Use_Cases]]

- **Kernkonzept:** Vererbung_in_Use_Cases bezeichnet eine [[Vererbung|vererbungsbasierte]] Beziehung zwischen zwei [[Use_Case|Use Cases]] in der [[UML]], bei der ein spezialisierter Use Case (Kind) eine eigenständige Variante eines allgemeinen Use Cases (Eltern) darstellt. Im Gegensatz zu [[Extend_und_Include_in_Use_Cases]] wird hier eine echte hierarchische Beziehung modelliert, bei der der Kind-Use-Case alle Eigenschaften und Akteursbeziehungen des Eltern-Use-Cases erbt und diese erweitern oder überschreiben kann. Diese Beziehung ist besonders dann sinnvoll, wenn der spezialisierte Use Case eine klare *is-a*-Relation zum allgemeinen Use Case aufweist (z. B. "Online-Bestellung" *ist eine* "Bestellung").
- **Nutzen & Zweck:** Vererbung_in_Use_Cases dient der **Wiederverwendung** und **Strukturierung** von Use-Case-Diagrammen, indem gemeinsame Funktionalitäten zentral definiert und in spezialisierten Varianten verfeinert werden. Vorteile sind:
- **Konsistenz**: Vermeidung von Redundanzen durch zentrale Definition gemeinsamer Abläufe.
- **Erweiterbarkeit**: Neue Varianten können durch Vererbung eingeführt werden, ohne bestehende Use Cases zu modifizieren.
- **Klarheit**: Explizite Darstellung von Hierarchien und Spezialisierungen im [[Use_Case_Diagramm]].

Typische Anwendungsfälle sind Szenarien, in denen ein Use Case eine spezifischere Ausprägung eines anderen darstellt (z. B. "Premium-Konto verwalten" als Spezialisierung von "Konto verwalten").
- **Abgrenzung & Grenzen:** Vererbung_in_Use_Cases unterscheidet sich grundlegend von anderen Use-Case-Beziehungen:
- **[[Extend_und_Include_in_Use_Cases]]**: Diese modellieren *optionale* oder *erzwungene* Erweiterungen, aber keine hierarchische Spezialisierung. Extend/Include sind *keine* Vererbungsbeziehungen und vererben keine Akteursassoziationen.
- **Stolpersteine**: 
  - **Falsche Anwendung**: Vererbung sollte nicht für *Teilabläufe* (→ Include) oder *bedingte Erweiterungen* (→ Extend) genutzt werden.
  - **Akteursvererbung**: Akteure werden *nicht* automatisch vererbt – jeder Use Case muss explizit mit seinen Akteuren verbunden sein.
  - **Komplexität**: Übermäßige Vererbungshierarchien können Use-Case-Diagramme unübersichtlich machen.
  - **Ablaufreihenfolge**: Vererbung modelliert *keine* zeitliche Abfolge von Use Cases (→ [[Aktivitätsdiagramm]] oder [[Sequenzdiagramm]]).

Vererbung ist nur dann sinnvoll, wenn der Kind-Use Case eine *echte Spezialisierung* darstellt und nicht nur eine Variante mit zusätzlichen Schritten.
- **Beispiel / Code:** {'uml_beschreibung': '```mermaid\nclassDiagram\n    UseCase "Bestellung aufgeben" <|-- UseCase "Online-Bestellung aufgeben"\n    UseCase "Bestellung aufgeben" <|-- UseCase "Telefon-Bestellung aufgeben"\n    \n    actor Kunde\n    actor Callcenter_Agent\n    \n    Kunde --> "Bestellung aufgeben"\n    Kunde --> "Online-Bestellung aufgeben"\n    Callcenter_Agent --> "Telefon-Bestellung aufgeben"\n```', 'erlaeuterung': 'In diesem Beispiel erbt "Online-Bestellung aufgeben" alle Eigenschaften von "Bestellung aufgeben", fügt aber spezifische Schritte (z. B. Zahlungsabwicklung per Kreditkarte) hinzu. Der Akteur *Kunde* ist mit beiden Use Cases verbunden, während *Callcenter_Agent* nur mit der Telefon-Variante assoziiert ist. Die Vererbung zeigt, dass eine Online-Bestellung eine *Art von* Bestellung ist.'}
