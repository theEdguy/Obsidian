---
id: 1a37f96a-a47c-4ae0-88a3-7ea89bca926b
title: "Modultest"
date: 2026-05-30
tags:
  - software_engineering
  - softwaretest
  - unit_testing
  - draft
source: "SWE Slides (Folien 136-150)"
---

# [[Modultest]]

- **Kernkonzept:** Ein [[Test]] auf der untersten [[Testebene]], der einzelne [[Komponente|Komponenten]] (z. B. [[Klasse|Klassen]] oder [[Methode|Methoden]]) isoliert überprüft. Unterscheidet zwischen [[White_Box_Test]] und [[Black_Box_Test]].
- **Nutzen & Zweck:** Löst das Problem der frühen Fehlererkennung durch gezielte Überprüfung von [[Implementierung|Implementierungen]]. Reduziert die Komplexität von [[Integrationstest|Integrationstests]] durch vorherige Verifizierung der [[Komponente|Komponenten]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Integrationstest|Integrationstests]] oder [[Systemtest|Systemtests]]. Bei zu starker Fokussierung auf [[Modultest|Modultests]] können [[Schnittstellenfehler]] übersehen werden. Erfordert oft [[Testdoppel|Testdoubles]] (z. B. [[Mock_Objekt|Mock-Objekte]]).
- **Beispiel / Code:** ```java
// Beispiel für einen Modultest (JUnit)
@Test
public void testMitgliedAnlegen() {
    Mitglied mitglied = new Mitglied("Max Mustermann", new Adresse("Musterstr. 1", "12345", "Musterstadt"));
    assertEquals("Max Mustermann", mitglied.getName());
    assertNotNull(mitglied.getAdresse());
}
```
