---
id: d25e619d-fb85-4cf7-b0da-6bad6697d50a
title: "Entkopplung"
date: 2026-05-31
tags:
  - software_engineering
  - entwurfsmuster
  - softwarearchitektur
  - designprinzipien
  - dependency_injection
  - modularisierung
  - uml
  - oop
  - draft
source: "Klausur_Referenz"
---

# [[Entkopplung]]

- **Kernkonzept:** Entkopplung bezeichnet im Software-Engineering das Prinzip, Abhängigkeiten zwischen Komponenten (z. B. [[Klassen]], [[Module]] oder [[Schnittstellen]]) zu minimieren, um deren Austauschbarkeit, Wartbarkeit und Testbarkeit zu erhöhen. Ziel ist es, Änderungen in einer Komponente möglichst ohne Auswirkungen auf andere Komponenten zu ermöglichen. Dies wird oft durch die Verwendung von [[Abstraktion]] (z. B. [[Schnittstellen]] oder [[Abstrakte_Klassen]]) und [[Designprinzipien]] wie [[Dependency_Inversion_Principle]] oder [[Loose_Coupling]] erreicht.
- **Nutzen & Zweck:** Entkopplung dient mehreren zentralen Zwecken:
1. **Wiederverwendbarkeit**: Entkoppelte Komponenten lassen sich leichter in anderen Kontexten einsetzen (z. B. durch [[Dependency_Injection]]).
2. **Wartbarkeit**: Änderungen an einer Komponente erfordern weniger Anpassungen in abhängigen Komponenten, was die Fehleranfälligkeit reduziert.
3. **Testbarkeit**: Komponenten können isoliert getestet werden (z. B. durch [[Mocking]] oder [[Unit_Tests]]).
4. **Skalierbarkeit**: Systeme lassen sich leichter erweitern, da neue Funktionalitäten mit minimalen Abhängigkeiten integriert werden können.
5. **Parallelisierung**: Entwicklerteams können unabhängig an verschiedenen Komponenten arbeiten, ohne Konflikte zu verursachen.

Beispiele für Entkopplung finden sich in [[Entwurfsmuster]] wie [[Observer_Pattern]] (lose Kopplung zwischen Subjekt und Beobachtern) oder [[Strategy_Pattern]] (Austausch von Algorithmen zur Laufzeit).
- **Abgrenzung & Grenzen:** Entkopplung ist kein Selbstzweck und hat Grenzen:
- **Übertriebene Abstraktion**: Zu viele [[Schnittstellen]] oder [[Abstrakte_Klassen]] können die Komplexität erhöhen und die Lesbarkeit beeinträchtigen (vgl. [[YAGNI]]).
- **Performance-Overhead**: Indirekte Aufrufe (z. B. über [[Dependency_Injection]]) können die Ausführungsgeschwindigkeit verringern.
- **Falsche Granularität**: Zu feingranulare Entkopplung (z. B. pro Methode eine [[Schnittstelle]]) führt zu unnötigem Boilerplate-Code.
- **Kontextabhängigkeit**: Nicht alle Systeme profitieren gleichermaßen von Entkopplung (z. B. monolithische Anwendungen vs. [[Microservices]]).

Typische Stolpersteine sind:
- **Zyklische Abhängigkeiten**: Selbst entkoppelte Komponenten können zyklische Abhängigkeiten bilden (vgl. [[Dependency_Graph]]).
- **Versteckte Kopplung**: Beispielsweise durch globale Zustände oder statische Methoden.
- **Falsche Annahmen**: Entkopplung löst keine Probleme mit [[Kohäsion]] oder schlechter [[Modularisierung]].
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel zeigt eine entkoppelte Implementierung eines Bestellprozesses mit [[Strategy_Pattern]] und [[Dependency_Injection]]. Die `Bestellung`-Klasse ist von der konkreten Zahlungsmethode entkoppelt und kann diese zur Laufzeit austauschen.', 'java_code': {'interface': 'public interface Zahlungsstrategie {\n    void bezahlen(double betrag);\n}', 'implementierungen': ['public class KreditkartenZahlung implements Zahlungsstrategie {\n    @Override\n    public void bezahlen(double betrag) {\n        System.out.println("Zahlung von " + betrag + " € per Kreditkarte.");\n    }\n}', 'public class PayPalZahlung implements Zahlungsstrategie {\n    @Override\n    public void bezahlen(double betrag) {\n        System.out.println("Zahlung von " + betrag + " € per PayPal.");\n    }\n}'], 'bestellung_klasse': 'public class Bestellung {\n    private Zahlungsstrategie zahlungsstrategie;\n\n    public Bestellung(Zahlungsstrategie zahlungsstrategie) {\n        this.zahlungsstrategie = zahlungsstrategie;\n    }\n\n    public void setZahlungsstrategie(Zahlungsstrategie zahlungsstrategie) {\n        this.zahlungsstrategie = zahlungsstrategie;\n    }\n\n    public void bezahlen(double betrag) {\n        zahlungsstrategie.bezahlen(betrag);\n    }\n}', 'anwendung': 'public class Main {\n    public static void main(String[] args) {\n        Bestellung bestellung = new Bestellung(new KreditkartenZahlung());\n        bestellung.bezahlen(100.0);\n\n        bestellung.setZahlungsstrategie(new PayPalZahlung());\n        bestellung.bezahlen(50.0);\n    }\n}'}, 'uml_beschreibung': {'mermaid_diagramm': 'classDiagram\n    class Zahlungsstrategie {\n        <<interface>>\n        +bezahlen(betrag: double)\n    }\n\n    class KreditkartenZahlung {\n        +bezahlen(betrag: double)\n    }\n\n    class PayPalZahlung {\n        +bezahlen(betrag: double)\n    }\n\n    class Bestellung {\n        -zahlungsstrategie: Zahlungsstrategie\n        +Bestellung(zahlungsstrategie: Zahlungsstrategie)\n        +setZahlungsstrategie(zahlungsstrategie: Zahlungsstrategie)\n        +bezahlen(betrag: double)\n    }\n\n    Zahlungsstrategie <|-- KreditkartenZahlung\n    Zahlungsstrategie <|-- PayPalZahlung\n    Bestellung --> Zahlungsstrategie'}}
