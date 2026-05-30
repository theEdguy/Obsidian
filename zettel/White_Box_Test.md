---
id: 6568d6f1-8b8a-4ec1-96f1-ce7641ba31be
title: "White_Box_Test"
date: 2026-05-30
tags:
  - software_engineering
  - softwaretest
  - unit_testing
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[White_Box_Test]]

- **Kernkonzept:** Ein [[Testverfahren]], bei dem die [[Implementierung]] der [[Komponente]] bekannt ist und gezielt überprüft wird. Fokussiert auf [[Codeabdeckung]] und interne [[Struktur]].
- **Nutzen & Zweck:** Löst das Problem der unentdeckten [[Logikfehler]] durch gezielte Überprüfung von [[Algorithmus|Algorithmen]] und [[Datenfluss]]. Ermöglicht hohe [[Testabdeckung]] auf [[Codeebene]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Black_Box_Test|Black-Box-Tests]], die die [[Funktionalität]] aus [[Nutzerperspektive]] überprüfen. Bei komplexen [[Implementierung|Implementierungen]] kann der Testaufwand stark steigen. Erfordert Kenntnis des [[Quellcode|Quellcodes]].
- **Beispiel / Code:** ```java
// Beispiel für einen White-Box-Test
@Test
public void testBeitragBerechnung() {
    Mitglied mitglied = new Mitglied("Test");
    // Interner Rabatt-Algorithmus wird überprüft
    assertEquals(8.0, mitglied.berechneBeitrag(10.0, true), 0.01);
}
```
