---
id: 26d93649-4d76-4db1-a258-19eb38de959e
title: "Entitaet"
date: 2026-06-20
tags:
  - software_engineering
  - domaenenmodellierung
  - entwurfsmuster
  - uml
  - datenmodellierung
  - state_pattern
  - domain_driven_design
  - draft
source: "Referenz_Scan"
---

# [[Entitaet]]

- **Kernkonzept:** Eine **Entität** ist ein zentrales Konzept in der [[Softwaremodellierung]] und [[Datenmodellierung]], das ein eindeutig identifizierbares, abgrenzbares Objekt oder Konzept der realen Welt oder des Problemraums repräsentiert. Entitäten besitzen eine klare [[Identität]] (z. B. durch einen eindeutigen Bezeichner) und können Attribute sowie Beziehungen zu anderen Entitäten aufweisen. Im Kontext von [[Klassendiagrammen]] (UML) oder [[Entity-Relationship-Modellen]] (ERM) werden Entitäten oft als Klassen oder Tabellen modelliert, die Zustände, Verhalten oder Daten kapseln. Im gegebenen Beispiel (State-Pattern) sind `State`-Instanzen wie `Login` oder `ManageMembers` Entitäten, die spezifische Zustände eines Systems repräsentieren und hierarchisch strukturiert sind (z. B. durch `isSubStateOf`).
- **Nutzen & Zweck:** 1. **Strukturierung von Domänenwissen**: Entitäten ermöglichen die Abbildung realer oder konzeptueller Objekte in Software, was die [[Domänenmodellierung]] und Kommunikation mit Stakeholdern erleichtert.
2. **Wiederverwendung und Wartbarkeit**: Durch die klare Abgrenzung von Entitäten (z. B. als [[Klassen]] oder [[Module]]) lassen sich Systeme modular gestalten, was die [[Wiederverwendbarkeit]] und [[Erweiterbarkeit]] fördert.
3. **Dokumentation von Entwurfsentscheidungen**: Entitäten dienen als Ankerpunkte für die Dokumentation von [[Architekturentscheidungen]] (z. B. im [[Domain-Driven_Design]]).
4. **Standardisierung**: Im [[State_Pattern]] oder [[Composite_Pattern]] helfen Entitäten, komplexe Zustände oder Hierarchien systematisch zu modellieren (z. B. durch hierarchische Benennung wie `ManageMembers(EditMember, NotAllowed)`).
5. **Datenpersistenz**: In Datenbanken werden Entitäten als Tabellen abgebildet, wobei ihre Attribute zu Spalten und Beziehungen zu Fremdschlüsseln werden (z. B. im [[ORM]]).
- **Abgrenzung & Grenzen:** 1. **Keine Verwechslung mit Werten**: Entitäten unterscheiden sich von [[Wertobjekten]] (Value Objects) durch ihre Identität – während zwei Wert-Objekte mit gleichen Attributen austauschbar sind (z. B. `Money(100, EUR)`), sind zwei Entitäten mit identischen Attributen nicht gleich (z. B. zwei `User`-Instanzen mit gleichem Namen).
2. **Keine 1:1-Abbildung der Realität**: Entitäten sind Abstraktionen und sollten nur die für den Problemraum relevanten Attribute und Beziehungen enthalten (z. B. wird ein `Kunde` in einem Bestellsystem anders modelliert als in einem CRM).
3. **Stolpersteine in Hierarchien**: Bei hierarchischen Entitäten (wie im State-Pattern) kann die Verwaltung von [[Zustandsübergängen]] komplex werden, insbesondere wenn Zustände dynamisch hinzugefügt oder entfernt werden.
4. **Grenzen der Modellierung**: Nicht alle Konzepte lassen sich sinnvoll als Entitäten abbilden – z. B. sind [[Algorithmen]] oder [[Prozesse]] oft besser als [[Dienste]] oder [[Funktionen]] modelliert.
5. **Performance-Overhead**: In verteilten Systemen können Entitäten mit vielen Beziehungen (z. B. in [[Graphdatenbanken]]) zu Performance-Problemen führen, wenn die [[Datenkonsistenz]] sichergestellt werden muss.
- **Beispiel / Code:** {'beschreibung': 'Das folgende UML-Klassendiagramm (Mermaid-Syntax) veranschaulicht hierarchische Entitäten im State-Pattern aus dem Kontext:', 'uml': '```mermaid\nclassDiagram\n    class State {\n        <<interface>>\n        +isSubStateOf(State state) boolean\n        +isSuperStateOf(State state) boolean\n    }\n\n    class S {\n        <<enumeration>>\n        Started\n        ValidationFailed\n        Login\n        SelectUseCase\n        EditMember\n        NotAllowed\n        ManageMembers\n        Initialized\n        ValidateToken\n        Check\n        -List~State~ subStates\n    }\n\n    State <|-- S\n    S --> S : subStates (Hierarchie)\n    note for S "Login(Started, ValidationFailed) bedeutet:\n    Login ist Substate von Started und ValidationFailed"\n```', 'java_beispiel': '```java\n// Beispiel für eine hierarchische Entität im State-Pattern\npublic enum S implements State {\n    Login(Started, ValidationFailed),  // Login ist Substate von Started und ValidationFailed\n    ManageMembers(EditMember, NotAllowed);  // ManageMembers ist Superstate von EditMember und NotAllowed\n\n    private final List<State> superStates;\n\n    S(State... superStates) {\n        this.superStates = Arrays.asList(superStates);\n    }\n\n    @Override\n    public boolean isSubStateOf(State state) {\n        return this == state || superStates.stream().anyMatch(s -> s.isSubStateOf(state));\n    }\n}\n```'}
