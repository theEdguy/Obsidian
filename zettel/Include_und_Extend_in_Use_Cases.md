---
aliases:
- Include_und_Extend
date: 2026-05-30
id: e979d0fd-5e49-4df5-93db-1b73cc7092cf
source: Klausur_Referenz
tags:
- software_engineering
- uml
- use_case_modellierung
- anforderungsanalyse
- entwurfsmuster
- softwarearchitektur
- draft
title: Include_und_Extend_in_Use_Cases
---

# [[Include_und_Extend_in_Use_Cases]]

- **Kernkonzept:** In der [[Use_Case_Modellierung]] beschreiben *Include* und *Extend* zwei fundamentale Beziehungen zwischen [[Use_Cases]], die die Wiederverwendung und Variabilität von Abläufen strukturieren.

- **Include-Beziehung**: Ein [[Use_Case]] (Basis-Use-Case) *schließt* einen anderen [[Use_Case]] (eingebetteter Use-Case) **mandatorisch** ein. Der eingebettete Use-Case wird dabei als Teil des Basis-Use-Cases ausgeführt. Dies entspricht einer *Dekomposition* von Funktionalität, um Redundanzen zu vermeiden (z. B. `A --<<include>>--> B`).

- **Extend-Beziehung**: Ein [[Use_Case]] (erweiternder Use-Case) *erweitert* einen anderen [[Use-Case]] (Basis-Use-Case) **optional** an definierten *Extension Points*, sofern eine Bedingung erfüllt ist. Der Basis-Use-Case bleibt dabei unabhängig und kann auch ohne die Erweiterung ausgeführt werden (z. B. `A --<<extend>>--> B` mit `Condition: {Bedingung}`).

Ein *Extension Point* ist eine explizit im Basis-Use-Case markierte Stelle, an der Erweiterungen eingehängt werden können. Er dient als *Anker* für bedingte Abläufe und erhöht die Flexibilität der Modellierung.
- **Nutzen & Zweck:** - **Include**: 
  - **Wiederverwendung**: Vermeidet Duplikation von Abläufen (z. B. gemeinsame Authentifizierung in mehreren [[Use_Cases]]).
  - **Modularität**: Zerlegt komplexe [[Use_Cases]] in handhabbare Teilschritte.
  - **Klarheit**: Macht Abhängigkeiten zwischen [[Use_Cases]] explizit sichtbar.

- **Extend**:
  - **Variabilität**: Ermöglicht optionale oder bedingte Erweiterungen (z. B. Sonderfälle wie "Premium-Features").
  - **Erweiterbarkeit**: Neue Funktionalität kann nachträglich hinzugefügt werden, ohne den Basis-Use-Case zu ändern (Prinzip der [[Offen_Geschlossen_Prinzip]]).
  - **Präzision**: Definiert klare Einstiegspunkte (*Extension Points*) für Erweiterungen, was die Wartbarkeit verbessert.

Beide Konzepte unterstützen die [[Trennung_von_Belangen]] und reduzieren die Komplexität in der [[Anforderungsanalyse]].
- **Abgrenzung & Grenzen:** - **Include vs. Extend**: 
  - *Include* ist **unbedingt** und **notwendig** für den Basis-Use-Case, während *Extend* **optional** und **bedingt** ist.
  - *Include* wird oft mit *Teil-von*-Beziehungen verwechselt, ist aber eine *Nutzungsbeziehung* (keine Hierarchie).
  - *Extend* darf nicht für *Spezialisierung* (wie in [[Vererbung]]) verwendet werden – hierfür ist die [[Generalisierung]] in [[Use_Cases]] vorgesehen.

- **Typische Stolpersteine**:
  - **Übermäßige Verwendung von Include**: Führt zu fragmentierten [[Use_Cases]], die schwer nachvollziehbar sind.
  - **Unklare Extension Points**: Fehlende oder vage definierte *Extension Points* machen Erweiterungen unberechenbar.
  - **Zyklische Abhängigkeiten**: `A --<<include>>--> B` und `B --<<include>>--> A` führen zu logischen Widersprüchen.
  - **Verwechslung mit [[Ablaufdiagramm]]-Strukturen**: Include/Extend sind **keine Kontrollflüsse**, sondern **strukturelle Beziehungen** zwischen [[Use_Cases]].

- **Grenzen**:
  - Beide Konzepte sind **rein konzeptionell** und haben keine direkte Entsprechung in der Implementierung (z. B. als [[Klasse]] oder [[Methode]]).
  - Sie eignen sich nicht für die Modellierung von **technischen Details** (z. B. Algorithmen), sondern fokussieren auf **Anwenderinteraktionen**.
- **Beispiel / Code:** {'uml_diagramm': '```mermaid\nclassDiagram\n    UseCase A : "Basis-Use-Case"\n    UseCase B : "Eingebetteter Use-Case"\n    UseCase C : "Erweiternder Use-Case"\n    UseCase D : "Basis-Use-Case mit Extension Point"\n\n    A --> B : <<include>>\n    C --> D : <<extend>>\n    note for D "Extension Point: \'Zahlung\'\n    Condition: {Benutzer ist Premium-Kunde}"\n```', 'textuelle_beschreibung': {'include_beispiel': {'szenario': "Online-Shop: 'Bestellung aufgeben' (A) *schließt* 'Zahlung abwickeln' (B) ein.", 'uml_notation': 'Bestellung_aufgeben --<<include>>--> Zahlung_abwickeln'}, 'extend_beispiel': {'szenario': "'Rechnung drucken' (C) *erweitert* 'Bestellung abschließen' (D) nur, wenn der Kunde eine Rechnung anfordert.", 'uml_notation': "Rechnung_drucken --<<extend>>--> Bestellung_abschließen\nCondition: {Rechnung angefordert}\nExtension Point: 'Dokumentation'"}}}
