---
id: 18f0611e-7887-4cf7-9fca-047b9cd7075c
title: "Meta-Modell"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - metamodellierung
  - uml
  - draft
source: "software_engineering_kapitel_04"
---

# [[Meta-Modell]]

- **Kernkonzept:** Ein [[Meta-Modell]] ist ein [[Modell]], das die [[Struktur]] und [[Regel|Regeln]] einer [[Modellierungssprache]] (z. B. [[UML]]) definiert und abstrakt beschreibt, welche [[Element|Elemente]] (z. B. [[Klasse|Klassen]], [[Attribut|Attribute]], [[Assoziation|Assoziationen]]) existieren dürfen und wie sie miteinander [[Interaktion|interagieren]]. Es dient als formale Grundlage für die [[Metamodellierung]] und ermöglicht die präzise Definition von [[Syntax]] und [[Semantik]] in [[Modell|Modellen]], während das [[Meta-Meta-Modell]] (M3) die höchste Abstraktionsebene darstellt und die Infrastruktur für die Definition von [[Meta-Modell|Meta-Modellen]] bereitstellt.
- **Nutzen & Zweck:** Das [[Meta-Modell]] ermöglicht die präzise und einheitliche Definition von [[Modellierungssprache|Modellierungssprachen]] und deren [[Erweiterbarkeit]], indem es klare [[Syntax]]- und [[Semantik]]-Regeln vorgibt. Dadurch löst es Probleme der Mehrdeutigkeit und [[Inkonsistenz]] in [[Modell|Modellen]], sodass diese von verschiedenen [[Person|Personen]] oder [[Tool|Tools]] (z. B. [[UML]]-Editoren, [[Code-Generator|Code-Generatoren]]) konsistent interpretiert und verarbeitet werden können. Es bildet die Basis für domänenspezifische Anpassungen, die Automatisierung von [[Modelltransformation|Modelltransformationen]] und die Sicherstellung der [[Interoperabilität]] zwischen verschiedenen [[System|Systemen]]. Insbesondere in der [[UML]] dient es als Grundlage für die Definition von [[Klassendiagramm|Klassendiagrammen]], [[Instanzdiagramm|Instanzdiagrammen]] und anderen [[Modellierungselement|Modellierungselementen]], wodurch eine standardisierte Kommunikation und Werkzeugunterstützung in der [[Softwareentwicklung]] gewährleistet wird. Das [[Meta-Meta-Modell]] (M3) schafft eine einheitliche Struktur für die Definition von [[Meta-Modell|Meta-Modellen]] wie der [[UML]]-Spezifikation und stellt sicher, dass alle abgeleiteten [[Modell|Modelle]] (M1) und deren [[Instanz|Instanzen]] (M0) auf einer klar definierten [[Syntax]] und [[Semantik]] basieren.
- **Abgrenzung & Grenzen:** Ein [[Meta-Modell]] ist kein [[Entwurfsmuster]] oder [[Designprinzip]], sondern ein [[Konzept]] der [[Metamodellierung]], das sich auf die Definition von [[Sprache|Sprachen]] und [[Tool|Tools]] konzentriert. Es sollte nicht eingesetzt werden, wenn informelle Beschreibungen oder [[Domänenspezifische_Sprache|domänenspezifische Sprachen]] (DSLs) ausreichen, da der Aufwand für dessen Definition und Pflege hoch ist. Im Gegensatz zu konkreten [[Modell|Modellen]] (z. B. einem [[UML]]-[[Klassendiagramm]]) beschreibt es keine [[Instanz|Instanzen]], sondern die [[Regel|Regeln]] zur Erstellung solcher [[Instanz|Instanzen]]. Das [[Meta-Meta-Modell]] (M3) ist noch abstrakter und komplexer, weshalb es nicht für die direkte Modellierung von Anwendungsdomänen oder konkreten [[Softwarelösung|Softwarelösungen]] geeignet ist. Alternativen wie textuelle Beschreibungen, Ad-hoc-Diagramme oder DSLs bieten mehr [[Flexibilität]], sind jedoch weniger präzise, schwerer automatisierbar und anfälliger für [[Inkonsistenz|Inkonsistenzen]].
- **Beispiel / Code:** ```uml
// Ausschnitt aus einem UML-Meta-Modell (M2-Ebene)
class Class {
    +name: String
    +attributes: Attribute[*]
    +operations: Operation[*]
    +associations: Association[*]
}

class Attribute {
    +name: String
    +type: Classifier
    +visibility: VisibilityKind
}

class Association {
    +name: String
    +end1: Property
    +end2: Property
}
```

```java
// Beispiel: Vereinfachtes Meta-Modell für UML-Klassen (M2-Ebene) und Instanzierung (M1-Ebene)
class MetaClass {
    String name;
    List<MetaAttribute> attributes;
    List<MetaOperation> operations;
    List<MetaAssociation> associations;
}

class MetaAttribute {
    String name;
    String type;
    Visibility visibility;
}

// Instanz des Meta-Modells (M1-Ebene): Ein konkretes UML-Klassenmodell
MetaClass mitglied = new MetaClass();
mitglied.name = "Mitglied";
mitglied.attributes.add(new MetaAttribute("name", "String", Visibility.PUBLIC));

// Beispielhafte Darstellung eines Meta-Meta-Modell-Elements (M3-Ebene, konzeptionell)
interface MetaClass {
    String getName();
    List<MetaAttribute> getMetaAttributes();
    List<MetaOperation> getMetaOperations();
}

interface MetaAttribute {
    String getName();
    MetaType getType();
    boolean isRequired();
}
```

```java
// Beispiel für ein einfaches Meta-Modell in UML-Notation (vereinfacht)
class MetaKlasse {
    String name;
    List<MetaAttribut> attribute;
    List<MetaOperation> operationen;
    List<MetaAssoziation> assoziationen;
}

class MetaAttribut {
    String name;
    String typ;
    String sichtbarkeit; // z. B. public, private
}

// Ein Modell (M1) wäre eine Instanz dieses Meta-Modells (M2).
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 5a2
- **Vorgänger / Parent:** [[MOF-Schichten]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
