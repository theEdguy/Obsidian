---
id: 0ed7b702-0d20-485f-88d7-ca39285dbd23
title: "Anwender"
date: 2026-05-30
tags:
  - software_engineering
  - anforderungsanalyse
  - usability
  - produktmanagement
  - user_experience
  - personas
  - draft
source: "Klausur_Referenz"
---

# [[Anwender]]

- **Kernkonzept:** Ein **Anwender** (auch **Endbenutzer** oder **User**) bezeichnet eine Person oder Rolle, die ein [[Softwaresystem]] oder eine Anwendung nutzt, um spezifische Aufgaben zu erfüllen oder Ziele zu erreichen. Im Gegensatz zu [[Entwickler]]n oder [[Systemadministrator]]en interagiert der Anwender primär mit der [[Benutzeroberfläche]] (UI) und profitiert von den funktionalen und nicht-funktionalen Eigenschaften des Systems, ohne dessen technische Implementierung zu beeinflussen oder zu verstehen.
- **Nutzen & Zweck:** Der Begriff dient der klaren Abgrenzung von Zielgruppen in der [[Softwareentwicklung]] und ist zentral für:
- **Anforderungsanalyse**: Identifikation von [[Use_Cases]] und [[User_Stories]], die die Bedürfnisse der Anwender abbilden.
- **Usability-Engineering**: Gestaltung intuitiver [[Benutzeroberflächen]] und Optimierung der [[User_Experience]] (UX).
- **Teststrategien**: Definition von [[Akzeptanztests]], die die Perspektive des Anwenders einnehmen (z. B. [[User_Acceptance_Testing]]).
- **Produktmanagement**: Priorisierung von Features basierend auf Anwenderfeedback (z. B. via [[Personas]] oder [[A/B_Testing]]).

Beispiel: Im Projekt *MyStilberater* sind Anwender modeinteressierte Nutzer, die das System zur Stilberatung verwenden – ihre Anforderungen fließen in die [[Produkt-Roadmap]] ein.
- **Abgrenzung & Grenzen:** - **Nicht-Anwender**: Technische Rollen wie [[Entwickler]], [[Tester]] oder [[DevOps]]-Ingenieure, die das System *erstellen* oder *betreiben*, zählen nicht zu den Anwendern.
- **Stakeholder vs. Anwender**: Stakeholder (z. B. Product Owner, Investoren) haben oft strategische Interessen, während Anwender operative Ziele verfolgen.
- **Typische Stolpersteine**:
  - *Annahme homogener Anwendergruppen*: Unterschiedliche [[Personas]] (z. B. Anfänger vs. Experten) erfordern angepasste UX-Designs.
  - *Übersehen von Edge-Cases*: Anwender nutzen Systeme oft anders als vorgesehen (z. B. Workarounds).
  - *Fehlende Empathie*: Technische Teams projizieren eigene Annahmen auf Anwender, statt [[User_Research]] durchzuführen.
- **Beispiel / Code:** ```mermaid
classDiagram
    class Anwender {
        +String name
        +String zielgruppe
        +interagiereMitSystem()
    }
    class MyStilberater {
        +starteBeratung()
        +zeigeOutfitVorschläge()
    }
    Anwender --> MyStilberater : nutzt
    note for Anwender "Beispiel-Persona:\n- Name: Anna, 28
- Zielgruppe: Berufstätige\n- Ziel: Schnelle Outfit-Auswahl für Meetings"
```
