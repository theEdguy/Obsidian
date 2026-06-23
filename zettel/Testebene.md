---
id: 37d0c5e9-6b3b-459f-a5a8-48c3a270820a
title: "Testebene"
date: 2026-06-23
tags:
  - software_engineering
  - softwaretest
  - qualitaetssicherung
  - test
  - qualität
  - testen
  - draft
source: "software_engineering_kapitel_06"
---

# [[Testebene]]

- **Kernkonzept:** [[Testebene]] bezeichnet eine hierarchische Stufe im [[Testprozess]], die sich auf einen bestimmten [[Abstraktionsgrad]] des [[Softwaresystem|Systems]] konzentriert. Sie umfasst systematische [[Testverfahren]], wie [[Modultest]], [[Integrationstest]], [[Systemtest]] und [[Akzeptanztest]], um die [[Korrektheit]], [[Vollständigkeit]], [[Fehlerfreiheit]] und [[Zuverlässigkeit]] der Software durch strukturiertes [[Testen]] sicherzustellen.
- **Nutzen & Zweck:** [[Testebene|Testebenen]] lösen das Problem der unklaren [[Testabdeckung]] durch strukturierte Überprüfung auf verschiedenen [[Abstraktionsgrad|Abstraktionsgraden]]. Sie ermöglichen eine frühzeitige [[Fehlererkennung]] und gezielte [[Fehlerlokalisierung]], reduzieren [[Wartungskosten]] und erhöhen das Vertrauen in das [[Softwaresystem]]. Durch systematisches [[Testen]] wird sichergestellt, dass die Software die definierten [[Anforderung|Anforderungen]] erfüllt und [[Benutzerfreundlichkeit]] sowie [[Stabilität]] gewährleistet. Zudem minimiert es das Risiko kostspieliger oder sicherheitskritischer Fehler in der Produktion. [[Testen]] validiert [[Architektur]]-Entscheidungen, verbessert die [[Wartbarkeit]] und unterstützt die [[Qualitätssicherung]] über den gesamten [[Softwareentwicklungsprozess]] hinweg.
- **Abgrenzung & Grenzen:** [[Testebene|Testebenen]] sind kein Ersatz für sorgfältiges [[Design]] oder [[Code-Review|Code-Reviews]], da sie keine strukturellen Schwächen in der [[Architektur]] aufdecken. Sie sind weniger effektiv, wenn [[Anforderung|Anforderungen]] unklar oder häufigen Änderungen unterworfen sind, da die [[Testfall|Testfälle]] dann kontinuierlich angepasst werden müssen. [[Testen]] unterscheidet sich von informellem Ausprobieren durch systematische Planung, Wiederholbarkeit und messbare Kriterien. In sicherheitskritischen Bereichen können ergänzende Methoden wie [[Formale_Verifikation]] oder [[Statische_Code-Analyse]] eingesetzt werden, ersetzen jedoch nicht das dynamische [[Testen]]. Bei extrem kurzen Iterationen oder [[Prototyp|Prototypen]] mit geringem Risiko kann der Testaufwand unverhältnismäßig sein. Zudem garantieren [[Testebene|Testebenen]] keine absolute [[Fehlerfreiheit]], sondern dienen der [[Risikominimierung]]. Eine klare Definition der [[Schnittstelle|Schnittstellen]] zwischen den [[Testebene|Ebenen]] ist essenziell, um die Effizienz zu gewährleisten.
- **Beispiel / Code:** ```java
// Beispiel für Testebenen in einem Projekt mit JUnit

// 1. Modultest (Unit Test): Test der Klasse Calculator (White-Box-Test)
import static org.junit.Assert.*;
import org.junit.Test;

public class CalculatorTest {
    @Test
    public void testAddition() {
        Calculator calculator = new Calculator();
        assertEquals(5, calculator.add(2, 3));
    }
    
    @Test(expected = IllegalArgumentException.class)
    public void testDivisionByZero() {
        Calculator calculator = new Calculator();
        calculator.divide(10, 0);
    }
}

// 2. Integrationstest: Test der Interaktion zwischen Calculator und Logger-Modul
import org.junit.Test;
import static org.mockito.Mockito.*;

public class CalculatorIntegrationTest {
    @Test
    public void testLoggingOnAddition() {
        Logger logger = mock(Logger.class);
        Calculator calculator = new Calculator(logger);
        calculator.add(2, 3);
        verify(logger).log("Addition performed: 2 + 3 = 5");
    }
}

// 3. Systemtest: Test der Calculator-Anwendung als Gesamtsystem
import org.junit.Test;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;

public class CalculatorSystemTest {
    @Test
    public void testWebInterface() {
        WebDriver driver = new ChromeDriver();
        driver.get("http://localhost:8080/calculator");
        // Simuliere Benutzereingaben und prüfe Ausgaben
        assertTrue(driver.getPageSource().contains("5"));
        driver.quit();
    }
}

// 4. Akzeptanztest: Test durch Endnutzer oder Product Owner

// Ergänzendes Beispiel für Modultest (Unit Test) der Klasse Mitglied
import org.junit.jupiter.api.Test;
import static org.junit.jupiter.api.Assertions.*;

class MitgliedTest {
    @Test
    void testAdresseAendern() {
        Mitglied mitglied = new Mitglied("Max", "Muster", "Alte Str. 1");
        mitglied.setAdresse("Neue Str. 2");
        assertEquals("Neue Str. 2", mitglied.getAdresse(), 
            "[[Adresse]] sollte aktualisiert werden");
    }
    
    @Test
    void testMailVersandProtokollieren() {
        Mitglied mitglied = new Mitglied("Anna", "Beispiel", "Testweg 3");
        assertTrue(mitglied.protokolliereMailVersand("Willkommen"), 
            "Mail-Versand sollte protokolliert werden");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1f
- **Vorgänger / Parent:** [[Software-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Modultests]]
  - [[Integrationstests]]
  - [[Systemtests]]
  - [[Akzeptanztests]]
- **Querverweise:** keine
