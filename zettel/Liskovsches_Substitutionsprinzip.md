---
id: 5962d9f6-9f86-4998-b626-84bde7992295
title: "Liskovsches_Substitutionsprinzip"
date: 2026-05-30
tags:
  - software_engineering
  - solid_prinzipien
  - vererbung
  - objektorientierung
  - design_by_contract
  - uml
  - entwurfsmuster
  - draft
source: "Klausur_Referenz"
---

# [[Liskovsches_Substitutionsprinzip]]

- **Kernkonzept:** Das Liskovsche Substitutionsprinzip (LSP) ist ein fundamentales Prinzip der [[Objektorientierung]], das besagt, dass Objekte einer [[Unterklasse]] ohne Beeinträchtigung der Programmlogik durch Objekte ihrer [[Oberklasse]] ersetzt werden können müssen. Formal ausgedrückt: Wenn ein Programmmodul mit einer Instanz einer Oberklasse funktioniert, muss es auch mit jeder Instanz einer Unterklasse dieser Oberklasse funktionieren, ohne dass sich das korrekte Verhalten des Programms ändert. Das Prinzip wurde von Barbara Liskov 1987 formuliert und ist eines der fünf [[SOLID_Prinzipien]].
- **Nutzen & Zweck:** Das LSP dient der Sicherstellung von **Konsistenz und Robustheit** in [[Vererbungshierarchien]] und [[Polymorphismus]]. Es ermöglicht:
- **Erweiterbarkeit**: Neue Unterklassen können eingeführt werden, ohne bestehende Code-Teile zu modifizieren (vgl. [[Open_Closed_Prinzip]]).
- **Wiederverwendbarkeit**: Oberklassen können als stabile Schnittstellen für verschiedene Implementierungen dienen.
- **Fehlervermeidung**: Durch die Einhaltung des Prinzips werden unerwartete Verhaltensänderungen bei der Nutzung von Unterklassen vermieden.
- **Testbarkeit**: Da Unterklassen die Verträge ihrer Oberklassen erfüllen müssen, vereinfacht sich das Schreiben von Unit-Tests (vgl. [[Design_by_Contract]]).
- **Abgrenzung & Grenzen:** Das LSP geht über die bloße syntaktische Kompatibilität (z. B. Methoden-Signaturen) hinaus und fordert **semantische Verträglichkeit**:
- **Verhaltensverträge**: Unterklassen dürfen Vorbedingungen nicht verschärfen oder Nachbedingungen abschwächen (vgl. [[Design_by_Contract]]).
- **Invarianten**: Klasseninvarianten der Oberklasse müssen von allen Unterklassen eingehalten werden.
- **Typische Verstöße**:
  - **Überschreiben mit leeren Methoden** (z. B. `save()` in einer Unterklasse, die nichts tut).
  - **Änderung der Semantik** (z. B. `Rectangle`-Unterklasse `Square`, die `setWidth()` und `setHeight()` so implementiert, dass beide Werte gleich bleiben).
  - **Ausnahmen erweitern** (z. B. eine Unterklasse wirft zusätzliche Ausnahmen, die die Oberklasse nicht deklariert).
- **Grenzen**: Das Prinzip ist nicht anwendbar, wenn Vererbung nur zur Code-Wiederverwendung genutzt wird, ohne dass eine echte [[Ist_ein_Beziehung]] besteht (hier wäre [[Komposition]] vorzuziehen).
- **Beispiel / Code:** {'beschreibung': 'Beispiel für einen Verstoß gegen das LSP und dessen Korrektur in Java. Das Problem entsteht, wenn eine Unterklasse (`Square`) die Semantik der Oberklasse (`Rectangle`) verletzt.', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Rectangle {\n        +int width\n        +int height\n        +setWidth(int width)\n        +setHeight(int height)\n        +int getArea()\n    }\n    class Square {\n        +setWidth(int width)\n        +setHeight(int height)\n    }\n    Rectangle <|-- Square\n```', 'code_verstoß': 'public class Rectangle {\n    protected int width;\n    protected int height;\n\n    public void setWidth(int width) {\n        this.width = width;\n    }\n\n    public void setHeight(int height) {\n        this.height = height;\n    }\n\n    public int getArea() {\n        return width * height;\n    }\n}\n\npublic class Square extends Rectangle {\n    @Override\n    public void setWidth(int width) {\n        super.setWidth(width);\n        super.setHeight(width); // Verstoß: Höhe wird mitgesetzt!\n    }\n\n    @Override\n    public void setHeight(int height) {\n        super.setHeight(height);\n        super.setWidth(height); // Verstoß: Breite wird mitgesetzt!\n    }\n}\n\n// Problem: Folgender Test schlägt fehl, obwohl Square ein Rectangle sein soll:\npublic void testArea(Rectangle r) {\n    r.setWidth(5);\n    r.setHeight(4);\n    assertEquals(20, r.getArea()); // Scheitert für Square!\n}', 'code_korrektur': 'Lösung 1: Vererbung vermeiden und [[Komposition]] nutzen:\n```java\npublic interface Shape {\n    int getArea();\n}\n\npublic class Rectangle implements Shape {\n    private int width;\n    private int height;\n\n    // ... (getter/setter wie oben)\n    @Override\n    public int getArea() {\n        return width * height;\n    }\n}\n\npublic class Square implements Shape {\n    private int side;\n\n    public void setSide(int side) {\n        this.side = side;\n    }\n\n    @Override\n    public int getArea() {\n        return side * side;\n    }\n}\n```\n\nLösung 2: Gemeinsame Oberklasse mit invarianten Regeln:\n```java\npublic abstract class Shape {\n    public abstract int getArea();\n}\n\npublic class Rectangle extends Shape {\n    private int width;\n    private int height;\n\n    // ... (getter/setter)\n    @Override\n    public int getArea() {\n        return width * height;\n    }\n}\n\npublic class Square extends Shape {\n    private int side;\n\n    // ... (getter/setter)\n    @Override\n    public int getArea() {\n        return side * side;\n    }\n}\n```'}
