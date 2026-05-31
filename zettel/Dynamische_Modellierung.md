---
id: 55de83dd-65b1-4e04-bfff-ad49e1be20e3
title: "Dynamische_Modellierung"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - softwarearchitektur
  - modellierung
  - verhaltensanalyse
  - schichtenarchitektur
  - mvc
  - draft
source: "Klausur_Referenz"
---

# [[Dynamische_Modellierung]]

- **Kernkonzept:** Die **Dynamische_Modellierung** beschreibt die Darstellung und Analyse des Verhaltens von Systemen oder Software-Komponenten über die Zeit. Im Gegensatz zur [[Statische_Modellierung]], die Strukturen wie Klassen, Attribute und Beziehungen abbildet, fokussiert sie sich auf Interaktionen, Zustandsänderungen und Abläufe (z. B. Methodenaufrufe, Nachrichtenflüsse oder Workflows). Sie nutzt Diagramme der [[UML]], insbesondere [[Sequenzdiagramm]], [[Zustandsdiagramm]] und [[Aktivitätsdiagramm]], um dynamische Aspekte wie Kontrollflüsse, Nebenläufigkeit oder Lebenszyklen von Objekten zu modellieren. Ein zentraler Aspekt ist die Abbildung der [[Geschäftslogik]] in Form von Algorithmen oder Prozessen, die durch externe Ereignisse oder interne Bedingungen ausgelöst werden.
- **Nutzen & Zweck:** Die Dynamische_Modellierung dient folgenden Zwecken:
- **Verhaltensanalyse**: Sie ermöglicht das Verständnis komplexer Abläufe (z. B. in [[Schichtenarchitektur]]-Systemen) und identifiziert Engpässe oder Fehlerquellen.
- **Kommunikation**: Sie visualisiert Interaktionen zwischen Komponenten (z. B. im [[Model-View-Controller]]-Muster) für Entwickler, Architekten und Stakeholder.
- **Spezifikation**: Sie definiert Anforderungen an die [[Schnittstelle]]-Interaktion oder die Reaktion auf Ereignisse (z. B. in Echtzeitsystemen).
- **Dokumentation**: Sie ergänzt statische Modelle (z. B. [[Klassendiagramm]]) um dynamische Perspektiven, um die Implementierung zu leiten.
- **Testvorbereitung**: Sie unterstützt die Erstellung von Testfällen durch klare Abbildung von Eingabe-Ausgabe-Beziehungen oder Zustandsübergängen.
- **Abgrenzung & Grenzen:** Abgrenzung und typische Stolpersteine:
- **Gegenüber [[Statische_Modellierung]]**: Dynamische Modelle zeigen *wie* etwas passiert, nicht *was* existiert. Eine Klasse im [[Klassendiagramm]] beschreibt z. B. Attribute, während ein [[Sequenzdiagramm]] deren Methodenaufrufe darstellt.
- **Komplexität**: Zu detaillierte dynamische Modelle können unübersichtlich werden (z. B. verschachtelte Schleifen in [[Aktivitätsdiagrammen]]). Hier hilft eine Fokussierung auf kritische Pfade.
- **Metamodell-Ebenen**: Dynamische Modelle gehören zur **M1-Ebene** (Modellinstanz), während ihre Definition (z. B. UML-Syntax) auf **M2** (Metamodell) liegt. Verwechslungen führen zu inkonsistenten Darstellungen.
- **Toolabhängigkeit**: Nicht alle UML-Tools unterstützen dynamische Diagramme gleich gut (z. B. Simulation von [[Zustandsdiagrammen]]).
- **Missverständnisse im [[Model-View-Controller]]**: Dynamische Modelle helfen, die Rollen von [[Controller]] (Steuerung) und [[Modell]] (Geschäftslogik) zu trennen, indem sie deren Interaktionen explizit machen (z. B. wer ruft wen auf).
- **Beispiel / Code:** {'beschreibung': 'Ein [[Sequenzdiagramm]] (UML) zur dynamischen Modellierung der Interaktion zwischen den Klassen `A` (Schicht 1) und `B` (Schicht 2) aus dem Kontext. Das Diagramm zeigt den Methodenaufruf `op1()` von `A` nach `B`, gefolgt von einem Rückruf `op2()` von `B` zu `A` mit Parameterübergabe:', 'mermaid_diagramm': 'sequenceDiagram\n    participant A as Klasse A (Schicht 1)\n    participant B as Klasse B (Schicht 2)\n    A->>B: op1()\n    activate B\n    B-->>A: Rückgabewert\n    deactivate B\n    B->>A: op2(parameter)\n    activate A\n    A-->>B: Bestätigung\n    deactivate A'}
