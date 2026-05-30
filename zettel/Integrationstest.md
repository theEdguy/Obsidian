---
id: 81d210ee-e584-4644-901c-1bd06aad6d45
title: "Integrationstest"
date: 2026-05-30
tags:
  - software_engineering
  - softwaretest
  - integration_testing
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Integrationstest]]

- **Kernkonzept:** Ein [[Test]] auf der mittleren [[Testebene]], der die Interaktion zwischen [[Komponente|Komponenten]] oder [[Teilsystem|Teilsystemen]] überprüft. Ziel ist die Verifizierung von [[Schnittstelle|Schnittstellen]] und [[Architekturentscheidung|Architekturentscheidungen]].
- **Nutzen & Zweck:** Löst das Problem der unentdeckten [[Schnittstellenfehler]] durch Überprüfung der Zusammenarbeit von [[Komponente|Komponenten]]. Ermöglicht die Validierung von [[Architektur]] und [[Datenfluss]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Modultest|Modultests]] oder [[Systemtest|Systemtests]]. Bei unklaren [[Schnittstelle|Schnittstellen]] kann der Testaufwand stark steigen. Erfordert oft [[Testumgebung|Testumgebungen]], die der Produktion ähneln.
- **Beispiel / Code:** ```java
// Beispiel für einen Integrationstest
@Test
public void testMitgliedUndBeitragIntegration() {
    Mitglied mitglied = new Mitglied("Anna Schmidt");
    Beitrag beitrag = new Beitrag(mitglied, 10.0);
    mitglied.addBeitrag(beitrag);
    
    assertEquals(1, mitglied.getBeitraege().size());
    assertEquals(10.0, mitglied.getBeitraege().get(0).getBetrag());
}
```
