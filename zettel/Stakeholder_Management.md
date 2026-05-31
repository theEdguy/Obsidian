---
id: 223ffb75-0607-41f3-8d02-1dde822f9d29
title: "Stakeholder_Management"
date: 2026-05-31
tags:
  - software_engineering
  - projektmanagement
  - anforderungsanalyse
  - uml
  - risikomanagement
  - kommunikationsstrategie
  - draft
source: "Klausur_Referenz"
---

# [[Stakeholder_Management]]

- **Kernkonzept:** Stakeholder_Management bezeichnet im [[Software_Engineering]] den systematischen Prozess der Identifikation, Analyse, Priorisierung und Kommunikation mit allen Personen oder Gruppen, die ein berechtigtes Interesse an einem Softwareprojekt haben oder von dessen Ergebnissen betroffen sind. Dazu zählen z. B. Auftraggeber, Endnutzer, Entwicklerteams, Projektmanager, externe Regulierungsbehörden oder betriebliche Abteilungen. Ziel ist es, deren Anforderungen, Erwartungen und Einflussmöglichkeiten frühzeitig zu erfassen und in den [[Softwareentwicklungsprozess]] (z. B. [[Anforderungsanalyse]] oder [[Risikomanagement]]) zu integrieren, um Konflikte zu minimieren und die Akzeptanz des Systems zu erhöhen.
- **Nutzen & Zweck:** 1. **Anforderungsabdeckung**: Verhindert, dass kritische Anforderungen übersehen werden (z. B. Compliance-Vorgaben von Regulierungsbehörden).
2. **Risikoreduktion**: Frühzeitige Identifikation von Widerständen oder unrealistischen Erwartungen (z. B. durch [[Use_Case]]-Workshops mit Endnutzern).
3. **Projekttransparenz**: Schafft klare Kommunikationsstrukturen (z. B. durch [[Stakeholder_Register]] oder regelmäßige Statusupdates).
4. **Priorisierung**: Ermöglicht die Fokussierung auf einflussreiche Stakeholder (z. B. mittels [[Macht-Interesse-Matrix]]).
5. **Nachhaltige Akzeptanz**: Fördert die langfristige Nutzung des Systems durch Einbindung aller Betroffenen (z. B. Schulungen für Endnutzer).

Im Kontext der Vorlesungsfolien (z. B. `ManageMembers`) zeigt sich Stakeholder_Management konkret in der Definition von [[Systemoperationen]] wie `manageMembers(token: Token)`, die Vorbedingungen (z. B. Authentifizierung) und Nachbedingungen (z. B. Zugriffsrechte) berücksichtigen müssen – hier sind Stakeholder wie Administratoren oder Mitglieder direkt betroffen.
- **Abgrenzung & Grenzen:** 1. **Kein Ersatz für [[Anforderungsmanagement]]**: Stakeholder_Management identifiziert zwar Anforderungen, ersetzt aber keine strukturierte [[Anforderungsspezifikation]] (z. B. mit [[User_Stories]] oder [[UML]]-Diagrammen).
2. **Dynamik der Stakeholder**: Rollen und Interessen können sich im Projektverlauf ändern (z. B. neue Regularien), was eine kontinuierliche Anpassung erfordert.
3. **Konfliktpotenzial**: Unterschiedliche Stakeholder haben oft widersprüchliche Ziele (z. B. Entwickler vs. Budgetverantwortliche), die durch [[Verhandlungsstrategien]] gelöst werden müssen.
4. **Kein technisches Konzept**: Stakeholder_Management ist primär ein organisatorisches Werkzeug und kein [[Entwurfsmuster]] oder [[Architekturstil]].
5. **Grenzen der Einflussnahme**: Nicht alle Stakeholder können oder sollten in Entscheidungen eingebunden werden (z. B. externe Wettbewerber).

Typische Stolpersteine:
- **Unklare Verantwortlichkeiten**: Wer ist für die Kommunikation mit welchem Stakeholder zuständig? (Lösung: [[RACI-Matrix]]).
- **Überkommunikation**: Zu viele Meetings mit irrelevanten Stakeholdern.
- **Unterschätzung informeller Einflussnehmer**: Z. B. erfahrene Entwickler, die Entscheidungen „hinter den Kulissen“ prägen.
- **Beispiel / Code:** {'beschreibung': 'Das folgende [[Klassendiagramm]] (textuell in Mermaid-Syntax) veranschaulicht eine vereinfachte Struktur für ein Stakeholder_Management-System im Kontext der Vorlesungsfolien (z. B. `ManageMembers`). Es zeigt die Beziehungen zwischen Stakeholdern, ihren Anforderungen und den Systemoperationen:', 'mermaid_diagramm': 'classDiagram\n    class Stakeholder {\n        +String name\n        +String rolle\n        +int einfluss\n        +int interesse\n        +anforderungenHinzufuegen(Anforderung anf)\n        +anforderungenAbrufen() List~Anforderung~\n    }\n    \n    class Anforderung {\n        +String id\n        +String beschreibung\n        +boolean istUmgesetzt\n        +prioritaetSetzen(int wert)\n    }\n    \n    class Systemoperation {\n        <<interface>>\n        +execute()\n    }\n    \n    class ManageMembers {\n        +Token token\n        +execute()\n        -validateToken() boolean\n    }\n    \n    Stakeholder "1" *-- "0..*" Anforderung : besitzt\n    Stakeholder "1" --> "0..*" Systemoperation : beeinflusst\n    Systemoperation <|-- ManageMembers\n    \n    note for ManageMembers "Vorbedingung: token.isValid() == true\\nNachbedingung: Mitgliederliste ist aktualisiert"\n    note for Stakeholder "Beispiel: Administrator (hoher Einfluss, hohes Interesse)"\n    '}
