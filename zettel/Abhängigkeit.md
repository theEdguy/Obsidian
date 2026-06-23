---
id: e0e4ba2f-01e6-4081-bac5-b4057648753c
title: "Abhängigkeit"
date: 2026-06-23
tags:
  - software_engineering
  - beziehung
  - modellierung
  - draft
source: "software_engineering_kapitel_05"
---

# [[Abhängigkeit]]

- **Kernkonzept:** Eine Abhängigkeit (Dependency) in der objektorientierten Modellierung beschreibt eine lose Beziehung zwischen Klassen, bei der eine Klasse temporär auf eine andere Klasse angewiesen ist, ohne dass eine dauerhafte Assoziation oder strukturelle Verbindung besteht. Sie drückt aus, dass Änderungen in der abhängigen Klasse Auswirkungen auf die nutzende Klasse haben können.
- **Nutzen & Zweck:** Abhängigkeiten existieren, um dynamische oder kurzfristige Beziehungen zwischen Klassen im Modell sichtbar zu machen, die keine feste Assoziation rechtfertigen. Sie lösen das Problem, dass nicht alle Beziehungen zwischen Objekten dauerhaft oder strukturell sind – etwa wenn eine Methode einer Klasse ein Objekt einer anderen Klasse als Parameter erhält, es lokal nutzt und dann verwirft. Durch die explizite Darstellung von Abhängigkeiten wird die Kopplung im System transparent, was die Wartbarkeit und Verständlichkeit des Modells erhöht.
- **Abgrenzung & Grenzen:** Abhängigkeiten sollten nicht genutzt werden, wenn eine dauerhafte, strukturelle Beziehung zwischen Klassen besteht, wie etwa bei Attributen oder Assoziationen. Im Gegensatz zu Assoziationen, Aggregationen oder Kompositionen drücken Abhängigkeiten keine Besitzverhältnisse oder Lebenszeitabhängigkeiten aus. Sie sind auch ungeeignet, wenn die Beziehung zwischen Klassen bidirektional oder navigierbar sein muss. Zudem sollten sie nicht für statische Vererbungsbeziehungen verwendet werden, da diese durch Generalisierung/Spezialisierung modelliert werden.
- **Beispiel / Code:** ```java
// Klasse 'ReportGenerator' ist abhängig von 'DataSource', 
// da sie deren Objekte nur temporär in der Methode 'generate' nutzt.
public class ReportGenerator {
    public void generate(DataSource dataSource) {
        String data = dataSource.fetchData();
        System.out.println("Generating report with: " + data);
    }
}

public class DataSource {
    public String fetchData() {
        return "Sample Data";
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1e
- **Vorgänger / Parent:** [[Objektorientierte_Analyse_und_Design]]
- **Folgezettel / Unterzettel:**
  - [[Dependency_Injection]]
- **Querverweise:**
  - [[Klassendiagramm]]
  - [[Software_Engineering]]
