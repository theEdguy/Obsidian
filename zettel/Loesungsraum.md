---
id: 1327f475-63e5-4739-b209-6706a5cdfdde
title: "Loesungsraum"
date: 2026-06-23
tags:
  - software_engineering
  - softwareentwurf
  - entwurfsmuster
  - architekturmuster
  - systemdesign
  - trade-offs
  - uml
  - prozess
  - draft
source: "software_engineering_kapitel_03"
---

# [[Loesungsraum]]

- **Kernkonzept:** Der [[Lösungsraum]] bezeichnet im [[Softwareentwurf]] die Menge aller möglichen [[Entwurfsmuster|Design- und Implementierungsvarianten]], die ein gegebenes [[Problem]] aus dem [[Problemraum]] in konkrete, ausführbare [[Softwareartefakt|Softwareartefakte]] überführen. Er umfasst strukturelle und verhaltensbezogene [[Alternativen]], die durch [[Entwurfsmuster]], [[Architekturmuster]] oder [[Modularisierung]] realisiert werden können, und dient als Brücke zwischen fachlichen [[Anforderung|Anforderungen]] und technischer [[Implementierung]]. Der [[Lösungsraum]] ist dynamisch und wird durch Rahmenbedingungen wie [[Kopplung]], [[Kohäsion]], [[Performance-Anforderung|Performance-Anforderungen]] oder technologische Einschränkungen eingegrenzt.
- **Nutzen & Zweck:** Der [[Lösungsraum]] dient als analytisches Werkzeug, um:
- **Design-Entscheidungen systematisch zu explorieren**, z. B. durch Abwägung zwischen [[Fassade_Pattern|Fassade]] und [[Mediator_Pattern|Mediator]] für die [[Systemorganisation]].
- **[[Trade-off|Trade-offs]] zu visualisieren**, etwa zwischen [[Flexibilität]] und [[Komplexität]] bei der Wahl zwischen [[Plugin-Architektur]] und monolithischer Struktur.
- **Kreativität im [[Entwurf]] zu fördern**, indem bewusst mehrere [[Lösungsweg|Lösungswege]] verglichen werden, z. B. [[Event-Driven_Architecture|Event-gesteuerte Architekturen]] vs. [[Request-Response]].
- **Risiken zu minimieren**, indem frühzeitig [[Alternativen]] identifiziert werden, falls primäre [[Lösung|Lösungen]] scheitern, z. B. Ersatz eines [[Singleton]] durch [[Dependency_Injection]] zur Verbesserung der [[Testbarkeit]].
- **Die methodische Durchgängigkeit zwischen [[Problemraum]] und [[Implementierung]] sicherzustellen**, um die semantische Lücke zwischen fachlichen [[Anforderung|Anforderungen]] und technischer Umsetzung zu schließen. Dadurch wird die Konsistenz zwischen [[Design]] und [[Implementierung]] gewährleistet und die [[Wartbarkeit]] des Systems verbessert.
- **Abgrenzung & Grenzen:** - **Kein [[Problemraum]]**: Der [[Lösungsraum]] setzt voraus, dass das [[Problem]] bereits durch [[Anforderungsanalyse]] oder [[Use_Case|Use-Cases]] definiert ist. Eine Vermischung führt zu unklaren [[Design-Entscheidung|Design-Entscheidungen]].
- **Keine direkte [[Implementierung]]**: Der [[Lösungsraum]] beschreibt *mögliche* [[Lösung|Lösungen]], nicht deren konkrete Umsetzung (z. B. [[Quellcode]] oder [[Klassendiagramm]]).
- **Kontextabhängigkeit**: [[Lösungsraum|Lösungsräume]] sind abhängig vom Anwendungskontext (z. B. ist [[Microservice|Microservices]] im [[Embedded-System|Embedded-Bereich]] oft ungeeignet).
- **Paradigmenabhängigkeit**: Das Konzept ist primär für [[Objektorientierung|objektorientierte]] Ansätze ausgelegt und nur eingeschränkt auf andere [[Programmierparadigma|Paradigmen]] wie [[Funktionale_Programmierung]] übertragbar.
- **Keine triviale Anwendung**: Bei einfachen oder prototypischen [[Anwendung|Anwendungen]] ohne langfristige [[Wartungsanforderung|Wartungsanforderungen]] ist eine explizite Trennung von [[Problemraum]] und [[Lösungsraum]] oft nicht notwendig.

**Stolpersteine**:
- *[[Analysis_Paralysis]]*: Zu viele [[Alternativen]] können zu Entscheidungsblockaden führen.
- *Voreingenommenheit*: Präferenzen für bestimmte [[Entwurfsmuster]] (z. B. [[Factory_Method]]) können den [[Lösungsraum]] unbewusst verengen.
- *Fehlende [[Metrik|Metriken]]*: Ohne klare [[Bewertungskriterium|Bewertungskriterien]] (z. B. [[Zyklomatische_Komplexität]], [[Kopplungsmetrik|Kopplungsmetriken]]) ist die Auswahl von [[Alternativen]] subjektiv.
- **Beispiel / Code:** ```mermaid
classDiagram
    %% Beispiel: Lösungsraum für die Organisation eines mobilen Stilberaters (MyStilberater)
    %% Alternative 1: Zentrale Steuerung (Fassade)
    class StilberaterFassade {
        +empfehleOutfit()
        +speichereBenutzerdaten()
    }
    StilberaterFassade --> OutfitGenerator
    StilberaterFassade --> Benutzerverwaltung

    %% Alternative 2: Dezentrale Verantwortung (Mediator)
    class StilberaterMediator {
        +koordiniereEmpfehlung()
    }
    StilberaterMediator --> OutfitGenerator
    StilberaterMediator --> Benutzerverwaltung
    OutfitGenerator --> StilberaterMediator : Benachrichtigung
    Benutzerverwaltung --> StilberaterMediator : Benachrichtigung

    %% Alternative 3: Transformation eines UML-Modells in Code (Problemraum → Lösungsraum)
    class OutfitGenerator {
        +generiereOutfit()
    }
    class Benutzerverwaltung {
        +speichereDaten()
        +lieferePräferenzen()
    }
```

```java
// Beispiel: Transformation der Klasse 'Mitglied' aus dem Problemraum (UML-Modell)
in den Lösungsraum (Java-Implementierung)

class Mitglied {
    private String name;
    private Anschrift adresse;
    private LocalDate alter;
    private int leistung;

    public Mitglied(String name, Anschrift adresse, LocalDate alter) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
        this.leistung = 0;
    }

    public int leistungsprognose(LocalDate datum) {
        // Berechnung basierend auf historischen Leistungsdaten
        return this.leistung + berechneTrend(datum);
    }

    private int berechneTrend(LocalDate datum) {
        // Implementierungsdetails der Prognose
        return 0;
    }
}
```

**Erläuterung**:
- Die ersten beiden [[Alternativen]] zeigen unterschiedliche [[Lösung|Lösungen]] für die [[Systemorganisation]]:
  1. **[[Fassade_Pattern|Fassade]]**: Eine zentrale Klasse (`StilberaterFassade`) kapselt die Interaktion mit [[Subsystem|Subsystemen]].
  2. **[[Mediator_Pattern|Mediator]]**: Eine vermittelnde Klasse (`StilberaterMediator`) reduziert direkte [[Abhängigkeit|Abhängigkeiten]] zwischen [[Komponente|Komponenten]].
- Die dritte [[Alternative]] demonstriert die Überführung eines [[UML-Modell|UML-Modells]] (z. B. aus dem [[Problemraum]]) in eine konkrete [[Implementierung]] (Java-Klasse).
- Der [[Lösungsraum]] umfasst auch hybride Ansätze (z. B. Kombination beider [[Muster]]) oder weitere [[Variante|Varianten]] wie [[Event_Sourcing]].

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4b
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Implementierung]]
- **Querverweise:**
  - [[Problemraum]]
