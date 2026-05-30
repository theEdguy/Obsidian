---
id: 7fe4d05b-c410-4b0c-97f8-93472ebb74fa
title: "Package"
date: 2026-05-30
tags:
  - software_engineering
  - implementierung
  - design
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Package]]

- **Kernkonzept:** Ein [[Package]] ist eine Strukturierungseinheit in der [[Implementierung]], die [[Klasse|Klassen]], [[Schnittstelle|Schnittstellen]] und andere [[Package|Packages]] gruppiert. Es dient der Organisation und [[Modularität]] des Codes.
- **Nutzen & Zweck:** Es verbessert die Übersichtlichkeit, reduziert Namenskonflikte und fördert die [[Wiederverwendbarkeit]]. [[Package|Packages]] ermöglichen eine klare Trennung von Verantwortlichkeiten und vermeiden zyklische Abhängigkeiten.
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Modul|Module]] oder [[Komponente|Komponenten]] auf [[Architektur]]-Ebene. [[Package|Packages]] sind kleiner und codebezogen. Im Gegensatz zu [[Namespace|Namespaces]] können sie Abhängigkeiten explizit steuern (z. B. durch `import` oder `access`).
- **Beispiel / Code:** ```java
// Beispiel für Package-Struktur in Java
package de.hs_karlsruhe.management;

public class BestellService {
    // Implementierung
}
```
