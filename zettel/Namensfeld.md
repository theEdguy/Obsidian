---
id: caf2f7b3-0f96-4b67-9dad-bc36167965ae
title: "Namensfeld"
date: 2026-06-23
tags:
  - software_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_04"
---

# [[Namensfeld]]

- **Kernkonzept:** Das Namensfeld in UML-Klassendiagrammen ist der Bereich einer Klasse, der den Klassennamen sowie optionale Metadaten wie Stereotype und Eigenschaften (Properties) enthält. Es dient der eindeutigen Identifikation und Klassifizierung des Modellelements innerhalb des Diagramms.
- **Nutzen & Zweck:** Das Namensfeld existiert, um Klassen in UML-Diagrammen klar und standardisiert zu benennen und zu kategorisieren. Es löst das Problem der Mehrdeutigkeit, indem es durch Stereotype (z. B. <<Interface>>) und Properties (z. B. {abstract}) zusätzliche semantische Informationen bereitstellt. Dies ermöglicht eine präzise Modellierung und verbessert die Kommunikation zwischen Entwicklern, indem es die Rolle und Eigenschaften einer Klasse auf einen Blick erkennbar macht.
- **Abgrenzung & Grenzen:** Das Namensfeld sollte nicht genutzt werden, um detaillierte Implementierungsinformationen oder komplexe Logik abzubilden – dafür sind die Attribute- und Operationsfelder vorgesehen. Es unterscheidet sich von diesen Feldern, indem es keine strukturellen oder verhaltensbezogenen Details enthält, sondern ausschließlich der Identifikation und Klassifizierung dient. Alternativen wie Kommentare oder Notizen sind für ergänzende Erklärungen besser geeignet, da sie flexibler sind, aber keine standardisierte Semantik bieten.
- **Beispiel / Code:** ```java
// UML-Klassendarstellung mit Namensfeld
<<Interface>>
Klassenname {isAbstract = true, author = "Max Mustermann"}

// Beispiel für eine abstrakte Klasse mit Stereotyp
<<Controller>>
Benutzerverwaltung {abstract}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a1
- **Vorgänger / Parent:** [[Klassenkompartimente]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
