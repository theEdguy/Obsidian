---
id: 63a96936-cf06-4bf9-a766-9d291b3e20ab
title: "UML_Diagramme"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - modellierung
  - softwarearchitektur
  - entwurfsmuster
  - systemanalyse
  - omg_standard
  - draft
source: "Klausur_Referenz"
---

# [[UML_Diagramme]]

- **Kernkonzept:** Die **Unified Modeling Language (UML)** ist eine standardisierte, grafische Modellierungssprache der [[OMG_Object_Management_Group]], die zur Spezifikation, Visualisierung, Konstruktion und Dokumentation von Artefakten in der Softwareentwicklung dient. UML umfasst verschiedene Diagrammtypen, die statische (z. B. [[Klassendiagramm]]) und dynamische (z. B. [[Sequenzdiagramm]]) Aspekte eines Systems abbilden. Das Meta-Modell der UML definiert dabei die Syntax und Semantik aller Beschreibungselemente, wodurch Erweiterungen (z. B. durch [[Stereotypen]]) methodisch konsistent integriert werden können. Ein zentrales Prinzip ist die Unterscheidung zwischen *Klassendiagrammen* (strukturelle Abstraktion) und *Instanzdiagrammen* (konkrete Ausprägungen).
- **Nutzen & Zweck:** UML_Diagramme dienen der **kommunikativen Präzision** in interdisziplinären Teams und ermöglichen:
- **Analysephase**: Abbildung von Anforderungen (z. B. [[Use_Case_Diagramm]]) und Domänenmodellen.
- **Entwurfsphase**: Definition von [[Softwarearchitektur]]-Mustern (z. B. [[Schichtenarchitektur]]) und [[Entwurfsmuster]]n (z. B. [[Singleton_Pattern]]).
- **Implementierungsphase**: Generierung von Code-Gerüsten (z. B. aus [[Klassendiagramm]]en) oder Reverse Engineering.
- **Dokumentation**: Langfristige Nachvollziehbarkeit von Systemstrukturen und -verhalten.

Durch die Standardisierung (OMG UML 2.5) wird eine einheitliche Notation gewährleistet, die Werkzeugunterstützung (z. B. PlantUML, Enterprise Architect) und automatisierte Validierung ermöglicht.
- **Abgrenzung & Grenzen:** - **Kein Programmierparadigma**: UML ist *keine* Programmiersprache, sondern ein Modellierungswerkzeug. Die Umsetzung in Code (z. B. Java, C#) erfordert manuelle oder toolgestützte Transformation.
- **Semantische Lücken**: UML-Diagramme können mehrdeutig sein (z. B. unklare Kardinalitäten in [[Assoziationen]]). Präzision erfordert zusätzliche textuelle Spezifikationen (z. B. OCL-Constraints).
- **Komplexitätsgrenzen**: Für große Systeme werden Diagramme schnell unübersichtlich. Hier helfen *Viewpoints* (z. B. Trennung von logischer und physischer Architektur) oder hierarchische Dekomposition.
- **Kein Ersatz für Prototyping**: Dynamische Aspekte (z. B. Performance) lassen sich oft nur durch [[Test_Driven_Development]] oder Simulationen validieren.
- **Werkzeugabhängigkeit**: Die Qualität der Diagramme hängt stark von der Tool-Unterstützung ab (z. B. Layout-Algorithmen, Exportformate).
- **Beispiel / Code:** {'beschreibung': 'Beispiel eines **Klassendiagramms** (textuell in Mermaid-Syntax) für ein einfaches [[Observer_Pattern]]-Szenario:', 'mermaid_syntax': '```mermaid\nclassDiagram\n    class Subject {\n        +attach(Observer)\n        +detach(Observer)\n        +notify()\n    }\n    class Observer {\n        <<interface>>\n        +update()\n    }\n    class ConcreteSubject {\n        +getState()\n        +setState()\n    }\n    class ConcreteObserver {\n        +update()\n    }\n    Subject <|-- ConcreteSubject\n    Observer <|-- ConcreteObserver\n    Subject "1" *-- "*" Observer : observers\n```', 'erlaeuterung': 'Das Diagramm zeigt:\n1. Die abstrakte Klasse `Subject` mit Methoden zur Verwaltung von [[Observer]]n.\n2. Das Interface `Observer` mit der `update()`-Methode.\n3. Konkrete Implementierungen (`ConcreteSubject`, `ConcreteObserver`).\n4. Eine *Kompositionsbeziehung* (gefüllte Raute) zwischen `Subject` und `Observer` mit Kardinalität 1..*.\n\nEin **Instanzdiagramm** dazu würde konkrete Objekte (z. B. `wetterStation: ConcreteSubject`) und deren Links abbilden.'}
