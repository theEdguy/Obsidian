---
id: 0ba30683-31ef-419b-87e3-4bda5e63ae68
title: "Entitaet"
date: 2026-06-23
tags:
  - software_engineering
  - domaenenmodellierung
  - entwurfsmuster
  - uml
  - datenmodellierung
  - state_pattern
  - domain_driven_design
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Entitaet]]

- **Kernkonzept:** Eine **[[Entitaet|Entität]]** ist ein zentrales [[Konzept]] in der [[Softwaremodellierung]] und [[Datenmodellierung]], das ein eindeutig identifizierbares, abgrenzbares [[Objekt]] oder [[Konzept]] der realen Welt oder des [[Problemraum|Problemraums]] repräsentiert. Sie besitzt eine klare [[Identität]] (z. B. durch einen eindeutigen Bezeichner) und kann [[Attribute]] sowie [[Beziehung|Beziehungen]] zu anderen [[Entitaet|Entitäten]] aufweisen. Im Kontext der [[Analyse]] dient sie dazu, die Strukturen und Zusammenhänge der [[Problemdomäne]] systematisch zu erfassen und zu modellieren, um ein präzises Verständnis der Anforderungen und Abläufe zu gewinnen.
- **Nutzen & Zweck:** 1. **Strukturierung von [[Domänenwissen]]**: [[Entitaet|Entitäten]] ermöglichen die Abbildung realer oder konzeptueller [[Objekt|Objekte]] in Software, was die [[Domänenmodellierung]] und Kommunikation mit [[Stakeholder|Stakeholdern]] erleichtert. Sie bilden die Grundlage für die spätere Softwarelösung, indem sie die [[Problemdomäne]] präzise abbilden.
2. **Wiederverwendung und Wartbarkeit**: Durch die klare Abgrenzung von [[Entitaet|Entitäten]] (z. B. als [[Klasse|Klassen]] oder [[Modul|Module]]) lassen sich Systeme modular gestalten, was die [[Wiederverwendbarkeit]] und [[Erweiterbarkeit]] fördert. Dies unterstützt auch die [[Dokumentation]] von [[Architekturentscheidung|Architekturentscheidungen]], insbesondere im [[Domain-Driven_Design]].
3. **Standardisierung und Komplexitätsmanagement**: Im [[State_Pattern]], [[Composite_Pattern]] oder anderen [[Entwurfsmuster|Entwurfsmustern]] helfen [[Entitaet|Entitäten]], komplexe Zustände, Hierarchien oder Strukturen systematisch zu modellieren (z. B. durch hierarchische Benennung wie `ManageMembers(EditMember, NotAllowed)`).
4. **Datenpersistenz und Integration**: In [[Datenbank|Datenbanken]] werden [[Entitaet|Entitäten]] als Tabellen abgebildet, wobei ihre [[Attribute]] zu Spalten und [[Beziehung|Beziehungen]] zu Fremdschlüsseln werden (z. B. im [[ORM]]). Dies erleichtert die Integration in verteilte Systeme, erfordert jedoch besondere Aufmerksamkeit für [[Datenkonsistenz]] und Performance.
5. **Analyse und Anforderungsermittlung**: [[Entitaet|Entitäten]] dienen als Ankerpunkte für die Identifikation und Beschreibung von [[Anforderung|Anforderungen]], indem sie die relevanten [[Objekt|Objekte]] und deren [[Beziehung|Beziehungen]] in der [[Problemdomäne]] sichtbar machen. Dies unterstützt die [[Kommunikation]] zwischen Entwicklern und [[Fachexperte|Fachexperten]] und reduziert Missverständnisse.
- **Abgrenzung & Grenzen:** 1. **Abgrenzung zu [[Wertobjekt|Wertobjekten]]**: [[Entitaet|Entitäten]] unterscheiden sich von [[Wertobjekt|Wertobjekten]] durch ihre [[Identität]] – während zwei [[Wertobjekt|Wertobjekte]] mit gleichen [[Attribute|Attributen]] austauschbar sind (z. B. `Money(100, EUR)`), sind zwei [[Entitaet|Entitäten]] mit identischen [[Attribute|Attributen]] nicht gleich (z. B. zwei `User`-Instanzen mit gleichem Namen).
2. **Keine 1:1-Abbildung der Realität**: [[Entitaet|Entitäten]] sind Abstraktionen und sollten nur die für den [[Problemraum]] relevanten [[Attribute]] und [[Beziehung|Beziehungen]] enthalten. Beispielsweise wird ein `Kunde` in einem [[Bestellsystem]] anders modelliert als in einem [[CRM-System]].
3. **Keine Modellierung von [[Attribut|Attributen]] oder temporären Zuständen**: [[Entitaet|Entitäten]] sollten nicht mit [[Attribut|Attributen]] verwechselt werden, die lediglich Eigenschaften beschreiben und keine eigenständige [[Identität]] besitzen (z. B. `Name` oder `Farbe`). Ebenso sind sie ungeeignet für die Modellierung von Quantitäten, einfachen Datenwerten oder temporären Zuständen ohne dauerhafte Bedeutung in der [[Problemdomäne]].
4. **Stolpersteine in Hierarchien und Dynamik**: Bei hierarchischen [[Entitaet|Entitäten]] (wie im [[State_Pattern]]) kann die Verwaltung von [[Zustandsübergang|Zustandsübergängen]] komplex werden, insbesondere wenn Zustände dynamisch hinzugefügt oder entfernt werden. Dies erfordert sorgfältiges [[Refactoring]] und die Berücksichtigung von [[Kohäsion]] und [[Lose_Kopplung|lose Kopplung]].
5. **Grenzen der Modellierung**: Nicht alle [[Konzept|Konzepte]] lassen sich sinnvoll als [[Entitaet|Entitäten]] abbilden – z. B. sind [[Algorithmus|Algorithmen]], [[Prozess|Prozesse]] oder [[Dienst|Dienste]] oft besser als [[Funktion|Funktionen]] oder [[Schnittstelle|Schnittstellen]] modelliert. Zudem können [[Entitaet|Entitäten]] mit vielen [[Beziehung|Beziehungen]] (z. B. in [[Graphdatenbank|Graphdatenbanken]]) zu Performance-Problemen führen, wenn die [[Datenkonsistenz]] sichergestellt werden muss.
6. **Analyse vs. Implementierung**: Während [[Entitaet|Entitäten]] in der [[Analyse]] dazu dienen, die [[Problemdomäne]] zu verstehen, müssen sie in der Implementierung oft an technische Rahmenbedingungen angepasst werden (z. B. durch [[Datenbanknormalisierung]] oder [[Objekt-Relationales_Mapping]]).
- **Beispiel / Code:** {'beschreibung': 'Die folgenden Beispiele veranschaulichen die Modellierung von [[Entitaet|Entitäten]] in verschiedenen Kontexten:', 'uml_hierarchische_entitaeten': '```mermaid\nclassDiagram\n    class State {\n        <<interface>>\n        +isSubStateOf(State state) boolean\n        +isSuperStateOf(State state) boolean\n    }\n\n    class S {\n        <<enumeration>>\n        Started\n        ValidationFailed\n        Login\n        SelectUseCase\n        EditMember\n        NotAllowed\n        ManageMembers\n        Initialized\n        ValidateToken\n        Check\n        -List~State~ subStates\n    }\n\n    State <|-- S\n    S --> S : subStates (Hierarchie)\n    note for S "Login(Started, ValidationFailed) bedeutet:\\nLogin ist Substate von Started und ValidationFailed"\n```', 'java_state_pattern': '```java\n// Beispiel für hierarchische Entitäten im State-Pattern\npublic enum S implements State {\n    Login(Started, ValidationFailed),  // Login ist Substate von Started und ValidationFailed\n    ManageMembers(EditMember, NotAllowed);  // ManageMembers ist Superstate von EditMember und NotAllowed\n\n    private final List<State> superStates;\n\n    S(State... superStates) {\n        this.superStates = Arrays.asList(superStates);\n    }\n\n    @Override\n    public boolean isSubStateOf(State state) {\n        return this == state || superStates.stream().anyMatch(s -> s.isSubStateOf(state));\n    }\n}\n```', 'java_analyse_entitaet': '```java\n// Beispiel einer Entität \'Mitglied\' in einem Vereinsverwaltungssystem (Analyse-Perspektive)\npublic class Mitglied {\n    private String mitgliedsId;  // Eindeutige Identität der Entität\n    private String name;\n    private String status;      // z. B. \'aktiv\' oder \'passiv\'\n    private List<Abteilung> abteilungen;  // Beziehung zu einer anderen Entität\n\n    public Mitglied(String mitgliedsId, String name) {\n        this.mitgliedsId = mitgliedsId;\n        this.name = name;\n        this.status = "aktiv";\n        this.abteilungen = new ArrayList<>();\n    }\n\n    public void abteilungVerlassen(Abteilung abteilung) {\n        abteilungen.remove(abteilung);\n        if (abteilungen.isEmpty()) {\n            this.status = "passiv";\n        }\n    }\n}\n```'}

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3a1
- **Vorgänger / Parent:** [[Fachkonzept]]
- **Folgezettel / Unterzettel:**
  - [[Identität]]
  - [[Lebenszyklus]]
- **Querverweise:**
  - [[Problemdomäne]]
  - [[Klassenmodell]]
