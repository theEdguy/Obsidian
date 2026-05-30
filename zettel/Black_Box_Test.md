---
id: 5905f8a4-7d28-4a47-bbb5-4a86055800ef
title: "Black_Box_Test"
date: 2026-05-30
tags:
  - software_engineering
  - softwaretest
  - functional_testing
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Black_Box_Test]]

- **Kernkonzept:** Ein [[Testverfahren]], bei dem die [[Implementierung]] der [[Komponente]] unbekannt ist und nur die [[Schnittstelle]] überprüft wird. Fokussiert auf die [[Funktionalität]] aus [[Nutzerperspektive]].
- **Nutzen & Zweck:** Löst das Problem der unklaren [[Nutzererfahrung]] durch Überprüfung der [[Funktionalität]] ohne Kenntnis des [[Quellcode|Quellcodes]]. Ermöglicht unabhängige [[Testdurchführung]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[White_Box_Test|White-Box-Tests]], die interne [[Logikfehler]] aufdecken. Bei unklaren [[Spezifikation|Spezifikationen]] können [[Testfall|Testfälle]] schwer definierbar sein. Erfordert oft [[Testdaten]] mit hoher [[Abdeckung]].
- **Beispiel / Code:** ```java
// Beispiel für einen Black-Box-Test
@Test
public void testMitgliedAnlegen() {
    Mitgliederverwaltung verwaltung = new Mitgliederverwaltung();
    verwaltung.neuesMitgliedAnlegen("Max Mustermann", "Musterstr. 1");
    
    assertTrue(verwaltung.enthaeltMitglied("Max Mustermann"));
}
```
