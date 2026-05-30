---
id: e56e0abb-4f84-446f-91e9-3f1202a48093
title: "Generics"
date: 2026-05-30
tags:
  - software_engineering
  - typsystem
  - entwurfsmuster
  - uml
  - java
  - wiederverwendbarkeit
  - draft
source: "Klausur_Referenz"
---

# [[Generics]]

- **Kernkonzept:** Generics (auch als parametrisierte Typen bezeichnet) sind ein Mechanismus in modernen Programmiersprachen, der es ermöglicht, [[Algorithmen]] und [[Datenstrukturen]] so zu definieren, dass sie mit verschiedenen Datentypen arbeiten können, ohne ihre Implementierung für jeden Typ neu schreiben zu müssen. Sie erlauben die Definition von [[Klassen]], [[Schnittstellen]] oder [[Methoden]] mit Platzhaltern (Typ-Parametern), die erst bei der Verwendung durch konkrete Typen ersetzt werden. Dies fördert die [[Typsicherheit]] zur Compile-Zeit und reduziert Code-Duplikation. In UML werden Generics oft als [[Templates]] dargestellt, z. B. mit dem Stereotyp `<<bind>>`.
- **Nutzen & Zweck:** Generics dienen primär der **Wiederverwendbarkeit** und **Typsicherheit** von Code. Sie ermöglichen:
- Die Erstellung generischer [[Datenstrukturen]] (z. B. Listen, Mengen, Maps) oder [[Algorithmen]] (z. B. Sortierverfahren), die unabhängig vom konkreten Datentyp funktionieren.
- Die Vermeidung von [[Type_Casting]] und damit verbundenen Laufzeitfehlern (z. B. `ClassCastException`).
- Eine klarere [[API]]-Gestaltung, da der Compiler Typfehler bereits zur Compile-Zeit erkennt.
- Die Reduktion von Code-Duplikation, da dieselbe Logik für verschiedene Typen genutzt werden kann.

Ein weiterer Vorteil ist die Unterstützung von [[Entwurfsmuster]]n wie der [[Abstrakte_Fabrik]], wo Generics die Erstellung typisierter Objekte vereinfachen (siehe Beispiel).
- **Abgrenzung & Grenzen:** Generics sind **kein Ersatz** für:
- [[Vererbung]]: Sie ermöglichen keine Polymorphie über eine Typhierarchie, sondern arbeiten mit Typ-Parametern.
- [[Dynamische_Typisierung]]: Generics sind statisch typisiert und bieten keine Laufzeitflexibilität wie z. B. in Python.
- [[Reflection]]: Sie operieren auf Typ-Ebene zur Compile-Zeit, nicht zur Laufzeit.

**Grenzen und Stolpersteine:**
- **Type Erasure** (in Java): Zur Laufzeit gehen Typ-Informationen verloren, was zu Einschränkungen führt (z. B. keine `instanceof`-Prüfung mit generischen Typen).
- **Komplexität**: Übermäßige Verwendung von Generics kann Code schwer lesbar machen (z. B. verschachtelte Typ-Parameter).
- **Einschränkungen bei primitiven Typen**: In Java müssen primitive Typen (z. B. `int`) durch Wrapper-Klassen (z. B. `Integer`) ersetzt werden.
- **Keine Kovarianz**: Generics sind standardmäßig invariant (z. B. `List<String>` ist **nicht** ein Subtyp von `List<Object>`). Dies kann durch Wildcards (`? extends T`) umgangen werden, erfordert aber sorgfältiges Design.
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel zeigt eine generische Klasse `Box<T>` in Java, die einen beliebigen Typ `T` kapselt, sowie eine Anwendung der [[Abstrakte_Fabrik]] mit Generics zur Erstellung typisierter Objekte:', 'java_code': {'generische_klasse': '// Generische Klasse zur Kapselung eines beliebigen Typs\npublic class Box<T> {\n    private T content;\n\n    public Box(T content) {\n        this.content = content;\n    }\n\n    public T getContent() {\n        return content;\n    }\n\n    public void setContent(T content) {\n        this.content = content;\n    }\n}\n\n// Verwendung\nBox<String> stringBox = new Box<>("Hallo Generics!");\nBox<Integer> intBox = new Box<>(42);', 'abstrakte_fabrik_mit_generics': '// Abstrakte Fabrik mit Generics zur Erstellung typisierter Objekte\npublic interface LabelFactory<T extends Label> {\n    T createLabel();\n}\n\npublic class AddressLabelFactory implements LabelFactory<AddressLabel> {\n    @Override\n    public AddressLabel createLabel() {\n        return new AddressLabel();\n    }\n}\n\n// Verwendung der Fabrik\nLabelFactory<AddressLabel> factory = new AddressLabelFactory();\nAddressLabel label = factory.createLabel();'}, 'uml_beschreibung': {'mermaid_diagramm': 'classDiagram\n    class Set~T~ {\n        -elements: T[0..*]\n        +addElem(T)\n        +rmElem(T)\n        +member(T): boolean\n    }\n    class Mitglied {\n        <<entity>>\n    }\n    Set~T~ <|-- MitgliederSet : <<bind>> T=Mitglied\n    note for Set~T~ "Generische Klasse mit Typ-Parameter T"\n    note for MitgliederSet "Konkrete Instanz von Set mit T=Mitglied"'}}
