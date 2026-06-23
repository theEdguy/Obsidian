---
id: d7749a3b-0a92-46ff-a9ca-c37ac525ca84
title: "OMG OCL"
date: 2026-06-23
tags:
  - software_engineering
  - constraints
  - uml
  - draft
source: "software_engineering_kapitel_10"
---

# [[OMG OCL]]

- **Kernkonzept:** OMG OCL (Object Constraint Language) ist eine formale Sprache der Object Management Group (OMG) zur Spezifikation von Bedingungen, Einschränkungen und Abfragen in UML-Modellen. Sie ermöglicht präzise Definitionen von Regeln, die über grafische UML-Diagramme hinausgehen, z. B. Invarianten, Vor- und Nachbedingungen.
- **Nutzen & Zweck:** OMG OCL existiert, um Unklarheiten und Mehrdeutigkeiten in UML-Modellen zu beseitigen, die durch rein grafische Darstellungen entstehen können. Sie löst das Problem, komplexe Geschäftsregeln, Integritätsbedingungen oder logische Abhängigkeiten zwischen Modellelementen exakt und maschinenlesbar zu formulieren, was für die automatisierte Validierung, Codegenerierung oder Modellprüfung essenziell ist.
- **Abgrenzung & Grenzen:** OMG OCL sollte nicht genutzt werden, wenn die Modellierungsanforderungen bereits durch einfache UML-Diagramme (z. B. Klassendiagramme) ausreichend abgedeckt sind oder wenn die Projektbeteiligten keine Erfahrung mit formalen Sprachen haben. Im Gegensatz zu Programmiersprachen wie Java oder Python dient OCL nicht der Implementierung, sondern ausschließlich der Spezifikation. Alternativen wie informelle Kommentare oder Pseudocode sind flexibler, aber weniger präzise und nicht automatisiert prüfbar.
- **Beispiel / Code:** ```ocl
context Person inv:
  self.alter >= 0 and self.alter <= 120

context Verein::addMitglied(p: Person): Boolean
  pre: p.isActive = true
  post: self.mitglieder->includes(p) and result = true
```

*Erklärung:*
- Die Invariante (`inv`) stellt sicher, dass das Attribut `alter` einer `Person` immer zwischen 0 und 120 liegt.
- Die Vorbedingung (`pre`) verlangt, dass eine Person aktiv sein muss, bevor sie einem `Verein` hinzugefügt wird.
- Die Nachbedingung (`post`) garantiert, dass die Person nach der Operation in der Mitgliederliste enthalten ist und der Rückgabewert `true` ist.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a1a1
- **Vorgänger / Parent:** [[OMG_UML]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
