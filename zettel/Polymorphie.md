---
id: f90ea6a6-7cf1-4c2d-8117-676749761719
title: "Polymorphie"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - entwurfsmuster
  - uml
  - vererbung
  - dynamische_bindung
  - paradigma
  - draft
source: "software_engineering_kapitel_03"
---

# [[Polymorphie]]

- **Kernkonzept:** Polymorphie (griech. für "Vielgestaltigkeit") ist ein zentrales [[Konzept]] der [[Objektorientierung]], das es ermöglicht, [[Objekte]] unterschiedlicher [[Klassen]] über eine gemeinsame [[Schnittstelle]] oder [[Basisklasse]] einheitlich zu behandeln. Dabei entscheidet die tatsächliche [[Klasse]] des [[Objekts]] zur Laufzeit, welche Implementierung einer [[Methode]] ausgeführt wird ([[Dynamische_Bindung]]). Polymorphie basiert auf den Prinzipien der [[Vererbung]] und [[Abstraktion]] und löst das Problem der starren Bindung von [[Operationen]] an spezifische [[Klassen]], indem sie Flexibilität und Erweiterbarkeit in der Softwareentwicklung schafft.
- **Nutzen & Zweck:** Polymorphie dient der **Flexibilität** und **Wiederverwendbarkeit** von [[Code]], indem sie:
- **Erweiterbarkeit** ermöglicht: Neue [[Klassen]] können hinzugefügt werden, ohne bestehenden [[Code]] zu ändern (vgl. [[Open_Closed_Principle]]).
- **Abstraktion** fördert: [[Algorithmen]] können auf hoher Ebene formuliert werden, ohne Details der konkreten Implementierung zu kennen.
- **Kapselung** unterstützt: Interne Änderungen einer [[Klasse]] bleiben verborgen, solange die [[Schnittstelle]] stabil bleibt.
- Die **Wartbarkeit** verbessert: [[Systeme]] können leichter an neue Anforderungen angepasst werden, ohne bestehende Strukturen zu verändern.

Typische Anwendungsfälle sind:
- [[Entwurfsmuster]] wie [[Strategy_Pattern]], [[Factory_Method]], [[Composite_Pattern]], [[Template_Method_Pattern]] oder [[Hook_Methoden]].
- [[Frameworks]], die über [[Schnittstellen]] oder [[Abstraktion]] gesteuert werden.
- Generische [[Datenstrukturen]] (z. B. Listen von [[Objekten]] einer [[Basisklasse]]).
- [[Event-gesteuerte_Systeme]], in denen [[Beobachter|Beobachtern]] polymorph auf [[Ereignisse]] reagieren.
- **Abgrenzung & Grenzen:** 1. **Statische vs. dynamische Polymorphie**:
   - *Statische Polymorphie* (Überladung von [[Methoden]]) wird zur Compile-Zeit aufgelöst und ist kein [[Objektorientierung|OOP]]-spezifisches [[Konzept]].
   - *Dynamische Polymorphie* (Überschreiben von [[Methoden]]) erfordert [[Vererbung]] oder [[Schnittstellen]] und wird zur Laufzeit aufgelöst.

2. **Grenzen der Polymorphie**:
   - Sie funktioniert nur bei [[Methoden]], die in der [[Basisklasse]] oder [[Schnittstelle]] deklariert sind. Private [[Methoden]] oder Felder sind nicht polymorph.
   - Performance-Overhead durch [[Dynamische_Bindung]] (z. B. in [[Echtzeitsystemen]] problematisch).
   - **Fragile Base Class Problem**: Änderungen in der [[Basisklasse]] können abgeleitete [[Klassen]] brechen.
   - Polymorphie sollte vermieden werden, wenn die Beziehungen zwischen [[Klassen]] statisch und unveränderlich sind oder wenn die zusätzliche [[Abstraktion]] die [[Komplexität]] unnötig erhöht.
   - Im Vergleich zu prozeduralen Ansätzen kann Polymorphie zu höherem Overhead führen, insbesondere bei einfachen Problemen, bei denen die Vorteile der [[Abstraktion]] nicht zum Tragen kommen.

3. **Stolpersteine**:
   - Falsche Annahmen über die tatsächliche [[Klasse]] eines [[Objekts]] (z. B. durch `instanceof`-Checks) untergraben den Nutzen von Polymorphie.
   - Übermäßige Verwendung kann zu unübersichtlichen Hierarchien führen (vgl. [[Deep_Inheritance_Hierarchy_Anti-Pattern]]).
   - In Sprachen ohne [[Mehrfachvererbung]] (z. B. Java) müssen [[Schnittstellen]] oder [[Mixin_Pattern]] genutzt werden, um Polymorphie über mehrere Hierarchien zu ermöglichen.
   - Ein übermäßiger Einsatz kann die [[Lesbarkeit]] des [[Codes]] beeinträchtigen, wenn die Hierarchien zu tief oder unübersichtlich werden. Alternativen wie einfache [[Vererbung]] oder [[Komposition]] können in solchen Fällen sinnvoller sein.
- **Beispiel / Code:** {'beschreibung': 'Die folgenden Beispiele zeigen Polymorphie anhand von [[Basisklassen]] mit abgeleiteten [[Klassen]]. Die [[Methoden]] werden polymorph aufgerufen, obwohl der Container nur [[Objekte]] vom Typ der [[Basisklasse]] kennt. Das [[Klassendiagramm]] würde eine [[Vererbungsbeziehung]] zwischen der [[Basisklasse]] und den abgeleiteten [[Klassen]] zeigen, mit einer abstrakten [[Methode]].', 'uml_klassendiagramm': '```mermaid\nclassDiagram\n    class Form {\n        <<abstract>>\n        +berechneFlaeche()* double\n    }\n    class Kreis {\n        -radius: double\n        +berechneFlaeche() double\n    }\n    class Rechteck {\n        -breite: double\n        -hoehe: double\n        +berechneFlaeche() double\n    }\n    Form <|-- Kreis\n    Form <|-- Rechteck\n\n    class Tier {\n        <<abstract>>\n        +macheGeräusch()* void\n    }\n    class Hund {\n        +macheGeräusch() void\n    }\n    class Katze {\n        +macheGeräusch() void\n    }\n    Tier <|-- Hund\n    Tier <|-- Katze\n```', 'code_beispiele': [{'sprache': 'Java', 'beschreibung': 'Beispiel mit geometrischen [[Formen|Formen]] (Basisklasse `Form`).', 'inhalt': '```java\npublic abstract class Form {\n    public abstract double berechneFlaeche();\n}\n\npublic class Kreis extends Form {\n    private double radius;\n    \n    public Kreis(double radius) {\n        this.radius = radius;\n    }\n    \n    @Override\n    public double berechneFlaeche() {\n        return Math.PI * radius * radius;\n    }\n}\n\npublic class Rechteck extends Form {\n    private double breite;\n    private double hoehe;\n    \n    public Rechteck(double breite, double hoehe) {\n        this.breite = breite;\n        this.hoehe = hoehe;\n    }\n    \n    @Override\n    public double berechneFlaeche() {\n        return breite * hoehe;\n    }\n}\n\n// Nutzung der Polymorphie:\npublic class Main {\n    public static void main(String[] args) {\n        Form[] formen = {new Kreis(5), new Rechteck(4, 6)};\n        for (Form form : formen) {\n            System.out.println("Fläche: " + form.berechneFlaeche()); // Polymorpher Aufruf\n        }\n    }\n}\n```'}, {'sprache': 'Java', 'beschreibung': 'Beispiel mit [[Tieren]] (Basisklasse `Tier`).', 'inhalt': '```java\n// Oberklasse\nabstract class Tier {\n    abstract void macheGeräusch();\n}\n\n// Unterklassen\nclass Hund extends Tier {\n    void macheGeräusch() {\n        System.out.println("Wuff!");\n    }\n}\n\nclass Katze extends Tier {\n    void macheGeräusch() {\n        System.out.println("Miau!");\n    }\n}\n\npublic class Main {\n    public static void main(String[] args) {\n        Tier meinTier1 = new Hund();\n        Tier meinTier2 = new Katze();\n        \n        meinTier1.macheGeräusch(); // Ausgabe: Wuff!\n        meinTier2.macheGeräusch(); // Ausgabe: Miau!\n    }\n}\n```'}]}

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d2b
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
