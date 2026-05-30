---
id: 54f1928e-6757-4cf9-b131-f914beb3c791
title: "Produktfamilie"
date: 2026-05-30
tags:
  - software_engineering
  - konzept
  - architektur
  - draft
source: "SWE Slides (Folien 346-360)"
---

# [[Produktfamilie]]

- **Kernkonzept:** Eine [[Produktfamilie]] bezeichnet eine Gruppe von [[Produkt|Produkten]], die zusammengehören und gemeinsam entwickelt, getestet und verwendet werden.
- **Nutzen & Zweck:** Sie stellt sicher, dass [[Objekt|Objekte]] innerhalb einer [[Produktfamilie]] zueinander kompatibel sind und fördert die [[Konsistenz]] sowie [[Wiederverwendbarkeit]] von [[Code]]. Besonders nützlich in [[Internationalisierung]] oder bei [[Themenwechsel|Themenwechseln]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Produkt|Produkte]] unabhängig voneinander entwickelt oder verwendet werden sollen. In solchen Fällen sind [[Einzelkomponenten]] oder [[Modularisierung]] vorzuziehen.
- **Beispiel / Code:** Eine [[Produktfamilie]] könnte aus `GermanAddressLabel`, `GermanTelephoneLabel` und `GermanBusinessLabel` bestehen, die alle von `GermanLabelFactory` erstellt werden.
