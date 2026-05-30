---
id: 155c3f2a-7212-4d8c-bbf9-8cfeb29a6402
title: "Polymorphie"
date: 2026-05-30
tags:
  - software_engineering
  - objektorientierung
  - entwurfsmuster
  - uml
  - vererbung
  - dynamische_bindung
  - draft
source: "Klausur_Referenz"
---

# [[Polymorphie]]

- **Kernkonzept:** Polymorphie (griech. für "Vielgestaltigkeit") ist ein zentrales Konzept der [[Objektorientierung]], das es ermöglicht, Objekte unterschiedlicher Klassen über eine gemeinsame [[Schnittstelle]] oder Basisklasse einheitlich zu behandeln. Dabei entscheidet die tatsächliche Klasse des Objekts zur Laufzeit, welche Implementierung einer Methode ausgeführt wird (dynamische Bindung). Polymorphie basiert auf den Prinzipien der [[Vererbung]] und [[Abstraktion]].
- **Nutzen & Zweck:** Polymorphie dient der **Flexibilität** und **Wiederverwendbarkeit** von Code, indem sie:
- **Erweiterbarkeit** ermöglicht: Neue Klassen können hinzugefügt werden, ohne bestehenden Code zu ändern (vgl. [[Open_Closed_Principle]]).
- **Abstraktion** fördert: Algorithmen können auf hoher Ebene formuliert werden, ohne Details der konkreten Implementierung zu kennen.
- **Kapselung** unterstützt: Interne Änderungen einer Klasse bleiben verborgen, solange die [[Schnittstelle]] stabil bleibt.

Typische Anwendungsfälle sind:
- [[Entwurfsmuster]] wie [[Strategy_Pattern]], [[Factory_Method]] oder [[Composite_Pattern]].
- Frameworks, die über [[Hook_Methoden]] oder [[Template_Method_Pattern]] gesteuert werden.
- Generische Datenstrukturen (z. B. Listen von Objekten einer Basisklasse).
- **Abgrenzung & Grenzen:** 1. **Statische vs. dynamische Polymorphie**: 
   - *Statische Polymorphie* (Überladung von Methoden) wird zur Compile-Zeit aufgelöst und ist kein OOP-spezifisches Konzept.
   - *Dynamische Polymorphie* (Überschreiben von Methoden) erfordert [[Vererbung]] oder [[Schnittstellen]] und wird zur Laufzeit aufgelöst.

2. **Grenzen der Polymorphie**:
   - Sie funktioniert nur bei Methoden, die in der Basisklasse oder [[Schnittstelle]] deklariert sind. Private Methoden oder Felder sind nicht polymorph.
   - Performance-Overhead durch dynamische Bindung (z. B. in Echtzeitsystemen problematisch).
   - **Fragile Base Class Problem**: Änderungen in der Basisklasse können abgeleitete Klassen brechen.

3. **Stolpersteine**:
   - Falsche Annahmen über die tatsächliche Klasse eines Objekts (z. B. durch `instanceof`-Checks) untergraben den Nutzen von Polymorphie.
   - Übermäßige Verwendung kann zu unübersichtlichen Hierarchien führen (vgl. [[Deep_Inheritance_Hierarchy_Anti-Pattern]]).
   - In Sprachen ohne Mehrfachvererbung (z. B. Java) müssen [[Schnittstellen]] oder [[Mixin_Pattern]] genutzt werden, um Polymorphie über mehrere Hierarchien zu ermöglichen.
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel zeigt Polymorphie anhand einer Basisklasse `Form` mit abgeleiteten Klassen `Kreis` und `Rechteck`. Die Methode `berechneFlaeche()` wird polymorph aufgerufen, obwohl der Container nur Objekte vom Typ `Form` kennt. Das [[Klassendiagramm]] würde eine Vererbungsbeziehung zwischen `Form` und den abgeleiteten Klassen zeigen, mit einer abstrakten Methode `berechneFlaeche()`.', 'uml_klassendiagramm': '```mermaid\nclassDiagram\n    class Form {\n        <<abstract>>\n        +berechneFlaeche()* double\n    }\n    class Kreis {\n        -radius: double\n        +berechneFlaeche() double\n    }\n    class Rechteck {\n        -breite: double\n        -hoehe: double\n        +berechneFlaeche() double\n    }\n    Form <|-- Kreis\n    Form <|-- Rechteck\n```', 'code_beispiel': {'sprache': 'Java', 'inhalt': 'public abstract class Form {\n    public abstract double berechneFlaeche();\n}\n\npublic class Kreis extends Form {\n    private double radius;\n    \n    public Kreis(double radius) {\n        this.radius = radius;\n    }\n    \n    @Override\n    public double berechneFlaeche() {\n        return Math.PI * radius * radius;\n    }\n}\n\npublic class Rechteck extends Form {\n    private double breite;\n    private double hoehe;\n    \n    public Rechteck(double breite, double hoehe) {\n        this.breite = breite;\n        this.hoehe = hoehe;\n    }\n    \n    @Override\n    public double berechneFlaeche() {\n        return breite * hoehe;\n    }\n}\n\n// Nutzung der Polymorphie:\npublic class Main {\n    public static void main(String[] args) {\n        Form[] formen = {new Kreis(5), new Rechteck(4, 6)};\n        for (Form form : formen) {\n            System.out.println("Fläche: " + form.berechneFlaeche()); // Polymorpher Aufruf\n        }\n    }\n}'}}
