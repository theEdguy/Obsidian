---
id: e40d1ce2-9525-4e7a-9197-ff7f53cc1189
title: "Separation_of_Concerns"
date: 2026-05-31
tags:
  - software_engineering
  - entwurfsmuster
  - softwarearchitektur
  - modularisierung
  - mvc_pattern
  - schichtenarchitektur
  - designprinzipien
  - draft
source: "Klausur_Referenz"
---

# [[Separation_of_Concerns]]

- **Kernkonzept:** Die **Separation_of_Concerns** (deutsch: *Trennung der Belange*) ist ein grundlegendes [[Entwurfsprinzip]] in der Softwareentwicklung, das die Aufteilung eines Systems in klar abgegrenzte, unabhängige Module oder Schichten fordert. Jedes Modul adressiert einen spezifischen *Concern* (Belang), d. h. einen abgeschlossenen Verantwortungsbereich wie z. B. Benutzeroberfläche, Geschäftslogik oder Datenhaltung. Die Trennung erfolgt idealerweise so, dass Änderungen in einem Belang keine oder nur minimale Auswirkungen auf andere Belange haben. Dieses Prinzip ist eng verwandt mit [[Modularisierung]] und [[Kohäsion]], während es gleichzeitig [[Kopplung]] reduziert.
- **Nutzen & Zweck:** 1. **Wartbarkeit**: Durch die Isolation von Belangen lassen sich Fehler leichter lokalisieren und beheben, da die Auswirkungen von Änderungen begrenzt sind. 
2. **Wiederverwendbarkeit**: Module mit klaren Verantwortlichkeiten (z. B. ein [[Datenzugriffsobjekt]]) können in anderen Kontexten oder Projekten wiederverwendet werden. 
3. **Parallelisierung der Entwicklung**: Teams können unabhängig an verschiedenen Belangen arbeiten (z. B. Frontend vs. Backend). 
4. **Testbarkeit**: Isolierte Module lassen sich einfacher mit [[Unit_Tests]] oder [[Integrationstests]] prüfen. 
5. **Skalierbarkeit**: Belange wie Performance-Optimierung oder Sicherheit können gezielt in eigenen Schichten (z. B. [[Caching_Schicht]]) umgesetzt werden. 

Ein klassisches Beispiel ist das [[MVC_Pattern]] (Model-View-Controller), das die Trennung von Präsentation (View), Steuerung (Controller) und Datenmodell (Model) erzwingt. Auch [[Schichtenarchitektur]] (z. B. Drei-Schichten-Modell) basiert auf diesem Prinzip.
- **Abgrenzung & Grenzen:** 1. **Übertriebene Trennung**: Eine zu feingranulare Aufteilung kann zu unnötiger Komplexität führen (z. B. zu viele Schnittstellen oder [[Boilerplate_Code]]). 
2. **Verletzung der Trennung**: Häufige Stolpersteine sind z. B. Geschäftslogik in der [[Präsentationsschicht]] oder direkte Datenbankzugriffe aus der [[Benutzeroberfläche]]. 
3. **Abhängigkeiten**: Selbst bei guter Trennung entstehen Abhängigkeiten zwischen Belangen (z. B. muss die View das Model kennen). Diese sollten durch [[Schnittstellen]] oder [[Dependency_Injection]] minimiert werden. 
4. **Performance-Overhead**: Indirekte Aufrufe zwischen Schichten können die Performance beeinträchtigen (z. B. bei [[Remote_Procedure_Calls]]). 
5. **Kontextabhängigkeit**: Nicht alle Belange lassen sich strikt trennen (z. B. [[Cross-Cutting_Concerns]] wie Logging oder Authentifizierung, die mehrere Schichten durchdringen). Hier helfen Techniken wie [[Aspect-Oriented_Programming]] (AOP).
- **Beispiel / Code:** {'beschreibung': 'Das folgende UML-Klassendiagramm (in Mermaid-Syntax) veranschaulicht die Separation_of_Concerns am Beispiel eines einfachen Mitgliedermanagementsystems:', 'uml_diagramm': '```mermaid\nclassDiagram\n    class MitgliedView {\n        +zeigeMitgliederListe(List~Mitglied~) void\n        +zeigeFehlermeldung(String) void\n    }\n    \n    class MitgliedController {\n        -mitgliedService: MitgliedService\n        +erstelleMitglied(MitgliedDTO) void\n        +loescheMitglied(int) void\n    }\n    \n    class MitgliedService {\n        -mitgliedRepository: MitgliedRepository\n        +findeAlleMitglieder() List~Mitglied~\n        +speichereMitglied(Mitglied) void\n    }\n    \n    class MitgliedRepository {\n        +findeAlle() List~Mitglied~\n        +speichere(Mitglied) void\n    }\n    \n    class Mitglied {\n        -id: int\n        -name: String\n        +getId() int\n        +getName() String\n    }\n    \n    MitgliedView --> MitgliedController : nutzt\n    MitgliedController --> MitgliedService : delegiert\n    MitgliedService --> MitgliedRepository : nutzt\n    MitgliedRepository --> Mitglied : persistiert\n```', 'java_beispiel': {'beschreibung': 'Ein Codeausschnitt in Java, der die Trennung der Belange im Controller zeigt:', 'code': 'public class MitgliedController {\n    private final MitgliedService mitgliedService;\n    \n    public MitgliedController(MitgliedService mitgliedService) {\n        this.mitgliedService = mitgliedService; // Dependency Injection\n    }\n    \n    public void erstelleMitglied(MitgliedDTO mitgliedDTO) {\n        // Guard-Condition: Validierung (ein Concern!)\n        if (mitgliedDTO.getName() == null || mitgliedDTO.getName().isEmpty()) {\n            throw new IllegalArgumentException("Name darf nicht leer sein");\n        }\n        \n        // Action-Expression: Delegation an Service (separater Concern)\n        Mitglied mitglied = new Mitglied(mitgliedDTO.getName());\n        mitgliedService.speichereMitglied(mitglied);\n    }\n}\n\n// Der Service kapselt die Geschäftslogik (ein weiterer Concern)\npublic class MitgliedService {\n    private final MitgliedRepository mitgliedRepository;\n    \n    public MitgliedService(MitgliedRepository mitgliedRepository) {\n        this.mitgliedRepository = mitgliedRepository;\n    }\n    \n    public void speichereMitglied(Mitglied mitglied) {\n        // Geschäftslogik (z. B. Duplikatsprüfung) hier\n        mitgliedRepository.speichere(mitglied);\n    }\n}', 'hinweis': 'Im Beispiel sind die Belange klar getrennt:\n- **Controller**: Validierung (Guard-Condition) und Steuerung der Abläufe.\n- **Service**: Geschäftslogik (Action-Expression).\n- **Repository**: Datenhaltung (ein weiterer Concern).\n- **View**: Präsentation (hier nicht gezeigt, aber z. B. eine GUI oder REST-Response).'}}
