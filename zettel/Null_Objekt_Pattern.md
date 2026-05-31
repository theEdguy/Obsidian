---
id: f1cd2348-a9f5-467d-ac24-9076c05c9771
title: "Null_Objekt_Pattern"
date: 2026-05-31
tags:
  - software_engineering
  - entwurfsmuster
  - design_patterns
  - oop
  - null_safety
  - uml
  - draft
source: "Klausur_Referenz"
---

# [[Null_Objekt_Pattern]]

- **Kernkonzept:** Das [[Null_Objekt_Pattern]] ist ein [[Entwurfsmuster]], das die Verwendung von `null`-Referenzen vermeidet, indem es ein spezielles Objekt bereitstellt, das ein standardmäßiges, "neutrales" Verhalten implementiert. Statt einer `null`-Prüfung wird eine Instanz einer Klasse verwendet, die eine [[Schnittstelle]] oder eine abstrakte Klasse erfüllt, aber keine Operationen ausführt oder Standardwerte zurückgibt. Dies eliminiert die Notwendigkeit von `null`-Checks und reduziert die Gefahr von [[NullPointerException]]s.
- **Nutzen & Zweck:** Das Pattern wird eingesetzt, um:
- **Kontrollfluss zu vereinfachen**: Durch das Ersetzen von `null`-Prüfungen mit einem definierten Objektverhalten.
- **Robustheit zu erhöhen**: Vermeidung von Laufzeitfehlern durch `null`-Referenzen.
- **Konsistenz zu gewährleisten**: Alle Aufrufe einer [[Schnittstelle]] führen zu einem gültigen, vorhersehbaren Verhalten, selbst wenn "nichts" getan werden soll.

Typische Anwendungsfälle sind:
- Rückgabewerte von Methoden, die sonst `null` liefern würden (z. B. leere Collections, Standardwerte).
- Platzhalter für nicht initialisierte oder fehlende Abhängigkeiten (z. B. in [[Dependency_Injection]]).
- Implementierung von [[Strategie_Pattern]] oder [[Zustand_Pattern]], wo ein "leerer" Zustand sinnvoll ist.
- **Abgrenzung & Grenzen:** Das [[Null_Objekt_Pattern]] ist **kein Ersatz** für:
- **Eingabevalidierung**: Es sollte nicht verwendet werden, um ungültige Eingaben zu maskieren (z. B. `null` als Parameter, wenn dies einen Fehler darstellt).
- **Fehlerbehandlung**: Kritische Fehler (z. B. Ressourcenmangel) sollten nicht durch ein Null-Objekt verschleiert werden.
- **Performance-kritische Szenarien**: Das Erstellen von Null-Objekten kann Overhead verursachen, wenn es in Schleifen oder häufig aufgerufenen Methoden eingesetzt wird.

**Stolpersteine**:
- **Übermäßige Verwendung**: Nicht jedes `null`-Problem sollte mit einem Null-Objekt gelöst werden. Manchmal ist `null` ein legitimes Signal (z. B. für "nicht gefunden").
- **Verwirrende Semantik**: Das Null-Objekt sollte klar als solches erkennbar sein (z. B. durch Namenskonventionen wie `EmptyUser` oder `NullLogger`).
- **Vererbungshierarchien**: Bei tiefen Hierarchien kann die Implementierung des Null-Objekts komplex werden, da es alle Methoden der [[Schnittstelle]] abdecken muss.
- **Beispiel / Code:** {'beschreibung': 'Beispiel in Java: Ein Logger-Interface mit einer Null-Implementierung, die keine Ausgaben macht.', 'code': {'interface': 'public interface Logger {\n    void log(String message);\n}', 'konkrete_implementierung': 'public class ConsoleLogger implements Logger {\n    @Override\n    public void log(String message) {\n        System.out.println(message);\n    }\n}', 'null_objekt_implementierung': 'public class NullLogger implements Logger {\n    @Override\n    public void log(String message) {\n        // Tut nichts (neutrales Verhalten)\n    }\n}', 'anwendung': 'public class Application {\n    private final Logger logger;\n\n    public Application(Logger logger) {\n        this.logger = (logger != null) ? logger : new NullLogger();\n    }\n\n    public void doSomething() {\n        logger.log("Aktion ausgeführt."); // Keine NullPointerException, auch wenn logger null war\n    }\n}'}, 'uml_beschreibung': {'mermaid': 'classDiagram\n    class Logger {\n        <<interface>>\n        +log(message: String) void\n    }\n\n    class ConsoleLogger {\n        +log(message: String) void\n    }\n\n    class NullLogger {\n        +log(message: String) void\n    }\n\n    Logger <|-- ConsoleLogger\n    Logger <|-- NullLogger'}}
