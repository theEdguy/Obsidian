---
id: b955f62d-81d7-438e-ae60-d199801ae6f9
title: "UML Metamodell"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - sprache
  - draft
source: "software_engineering_kapitel_08"
---

# [[UML Metamodell]]

- **Kernkonzept:** Das UML Metamodell definiert die abstrakte Syntax und Semantik der Unified Modeling Language (UML) selbst. Es beschreibt die Struktur, Regeln und Beziehungen der UML-Elemente wie Klassen, Use Cases oder Aktivitätsdiagramme auf einer metaebenen, um deren konsistente Anwendung und Interpretation zu ermöglichen.
- **Nutzen & Zweck:** Das UML Metamodell existiert, um eine standardisierte und präzise Grundlage für die Modellierung mit UML zu schaffen. Es löst das Problem der Mehrdeutigkeit und Inkonsistenz, indem es klare Regeln für die Erstellung und Interpretation von UML-Diagrammen vorgibt. Dadurch wird die Kommunikation zwischen Entwicklern, Tool-Herstellern und Anwendern vereinfacht und die Interoperabilität von UML-Werkzeugen sichergestellt.
- **Abgrenzung & Grenzen:** Das UML Metamodell sollte nicht genutzt werden, wenn einfache oder informelle Modellierungsansätze ausreichen, da es eine hohe Komplexität und Abstraktionsebene mit sich bringt. Es unterscheidet sich von konkreten UML-Diagrammen (z. B. Klassendiagrammen) dadurch, dass es nicht direkt zur Modellierung von Software-Systemen dient, sondern die Sprache selbst beschreibt. Für pragmatische oder prototypische Modellierungen kann es überdimensioniert sein.
- **Beispiel / Code:** ```java
// Beispiel: Ausschnitt aus dem UML Metamodell (vereinfacht als Klasse dargestellt)
class Class {
    private String name;
    private List<Attribute> attributes;
    private List<Operation> operations;
    private List<Association> associations;
    
    public void addAttribute(Attribute attribute) { /* ... */ }
    public void addOperation(Operation operation) { /* ... */ }
}

// Das Metamodell definiert, wie eine 'Class' in UML strukturiert ist,
// nicht jedoch eine konkrete Klasse eines Software-Systems.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 16b
- **Vorgänger / Parent:** [[UML]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[UML]]
