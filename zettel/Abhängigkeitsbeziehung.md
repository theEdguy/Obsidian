---
id: f377db35-b636-49a2-913e-dd42dcbe8d3b
title: "Abhängigkeitsbeziehung"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - entwurfsmuster
  - softwarearchitektur
  - oop
  - kopplung
  - draft
source: "Klausur_Referenz"
---

# [[Abhängigkeitsbeziehung]]

- **Kernkonzept:** Eine **Abhängigkeitsbeziehung** (engl. *Dependency*) ist eine gerichtete Beziehung zwischen zwei [[Modul]]n oder [[Klasse]]n, bei der eine Änderung in der unabhängigen Einheit (Anbieter) potenziell eine Änderung in der abhängigen Einheit (Client) erfordert. Sie drückt eine *temporäre* oder *lose* Nutzung aus, bei der der Client die Funktionalität des Anbieters benötigt, ohne dass eine dauerhafte [[Assoziation]] (z. B. über Attribute) besteht. In [[UML]] wird sie als gestrichelter Pfeil (`---->`) dargestellt und oft mit dem Stereotyp `<<use>>` oder `<<call>>` präzisiert.
- **Nutzen & Zweck:** Abhängigkeitsbeziehungen dienen dazu, die **Kopplung** zwischen Komponenten zu minimieren und die **Kohäsion** zu erhöhen, indem sie klar dokumentieren, *wo* und *wie* eine Klasse von einer anderen abhängt. Sie helfen bei:
- Der Identifikation von [[Schnittstellen]]-Nutzung (z. B. Parameter, Rückgabewerte, lokale Variablen).
- Der Analyse von [[Refactoring]]-Bedarf (z. B. bei zyklischen Abhängigkeiten).
- Der Modellierung von [[Entwurfsmuster]]n wie [[Strategy_Pattern]] oder [[Factory_Method]], wo Algorithmen oder Objekterzeugung ausgelagert werden.
- Der Verbesserung der [[Testbarkeit]] durch Isolation (z. B. via [[Dependency_Injection]]).
- **Abgrenzung & Grenzen:** Abhängigkeitsbeziehungen unterscheiden sich von anderen UML-Beziehungen:
- **[[Assoziation]]**: Dauerhafte Beziehung (z. B. Attribut-Referenz), während Abhängigkeiten *flüchtig* sind (z. B. Methodenparameter).
- **[[Vererbung]]**: Statische, strukturelle Beziehung (`is-a`), während Abhängigkeiten dynamisch sind.
- **[[Aggregation]]/[[Komposition]]**: Teile-Ganzes-Beziehungen mit Lebenszyklusabhängigkeit.

**Stolpersteine**:
- *Zyklische Abhängigkeiten* führen zu unwartbarem Code (Verstoß gegen das [[Dependency_Inversion_Principle]]).
- *Versteckte Abhängigkeiten* (z. B. globale Variablen, Singletons) untergraben die [[Kapselung]].
- Übermäßige Abhängigkeiten deuten auf mangelnde [[Kohäsion]] hin (z. B. eine Klasse nutzt zu viele fremde Klassen).
- **Beispiel / Code:** {'uml': '```mermaid\nclassDiagram\n    class Bestellung {\n        +berechneGesamtpreis(steuersatz: SteuerRechner)\n    }\n    class SteuerRechner {\n        +berechneSteuer(betrag: double) double\n    }\n    Bestellung ..> SteuerRechner : <<use>>\n```', 'java': 'public class Bestellung {\n    // Abhängigkeit: SteuerRechner wird als Parameter genutzt (kein Attribut!)\n    public double berechneGesamtpreis(SteuerRechner steuerRechner) {\n        double netto = 100.0;\n        double steuer = steuerRechner.berechneSteuer(netto);\n        return netto + steuer;\n    }\n}\n\npublic class SteuerRechner {\n    public double berechneSteuer(double betrag) {\n        return betrag * 0.19;\n    }\n}', 'erläuterung': 'Die `Bestellung` nutzt den `SteuerRechner` nur temporär (als Methodenparameter), ohne ihn als Attribut zu speichern. Dies reduziert die Kopplung und ermöglicht z. B. den Austausch des SteuerRechners zur Laufzeit (z. B. für verschiedene Länder).'}
