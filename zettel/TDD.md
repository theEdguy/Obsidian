---
id: 5f8d40fb-74cb-440a-b077-4f40521b7b92
title: "TDD"
date: 2026-05-30
tags:
  - software_engineering
  - entwicklungsmethode
  - draft
source: "SWE Slides (Folien 46-60)"
---

# [[TDD]]

- **Kernkonzept:** [[Test_Driven_Development|TDD]] (Test-Driven Development) ist eine [[Entwicklungsmethode]], bei der [[Testfall|Testfälle]] vor dem eigentlichen [[Code]] geschrieben werden. Der [[Entwicklungszyklus]] folgt dem Muster: [[Testfall]] schreiben → [[Testfall]] fehlschlagen lassen → [[Code]] schreiben → [[Testfall]] bestehen lassen → [[Refactoring]].
- **Nutzen & Zweck:** Es löst das Problem der [[Codequalität]] und [[Fehleranfälligkeit]] durch frühzeitige [[Testautomatisierung]] und fördert [[Modularität]] und [[Wartbarkeit]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Projekt|Projekte]] mit unklaren [[Anforderung|Anforderungen]] oder explorativen [[Entwicklungsphase|Phasen]]. Unterscheidet sich von [[Traditionelle_Entwicklung|traditioneller Entwicklung]] durch den Fokus auf [[Testfall|Testfälle]] vor dem [[Code]].
- **Beispiel / Code:** Beispiel in Java:

```java
// Schritt 1: Testfall schreiben
@Test
public void testAddition() {
    Calculator calculator = new Calculator();
    assertEquals(5, calculator.add(2, 3));
}

// Schritt 2: Code schreiben, um Test zu bestehen
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```
