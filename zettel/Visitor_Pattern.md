---
id: 7c7f32ef-300e-4fd3-bd8d-88fcbd050a64
title: "Visitor_Pattern"
date: 2026-05-30
tags:
  - software_engineering
  - entwurfsmuster
  - verhaltensmuster
  - objektstruktur
  - double_dispatch
  - uml
  - refactoring
  - draft
source: "Klausur_Referenz"
---

# [[Visitor_Pattern]]

- **Kernkonzept:** Das **Visitor_Pattern** ist ein [[Verhaltensmuster]] in der [[Softwarearchitektur]], das die Trennung von Algorithmen und den Objekten, auf denen sie operieren, ermöglicht. Es erlaubt das Hinzufügen neuer Operationen zu einer [[Objektstruktur]] ohne deren Klassen zu modifizieren, indem die Operationen in separate [[Besucher]]-Klassen ausgelagert werden. Der Kern besteht aus zwei zentralen Schnittstellen: `Element` (akzeptiert einen Besucher) und `Visitor` (definiert Operationen für verschiedene Elementtypen).
- **Nutzen & Zweck:** Das Pattern wird eingesetzt, um:
- **Erweiterbarkeit** zu verbessern: Neue Operationen können hinzugefügt werden, ohne bestehende Klassen zu ändern (offen für Erweiterung, geschlossen für Modifikation – vgl. [[Open_Closed_Principle]]).
- **Kohäsion** zu erhöhen: Verwandte Operationen werden in einer Klasse gebündelt, statt über mehrere Klassen verteilt.
- **Komplexe Objektstrukturen** (z. B. [[Kompositum_Pattern]]) effizient zu traversieren, ohne die Struktur selbst mit Logik zu überladen.

Typische Anwendungsfälle sind:
- Compilerbau (z. B. AST-Traversierung),
- Serialisierung/Deserialisierung,
- Datenbankabfragen oder
- GUI-Frameworks (z. B. Rendering von UI-Komponenten).
- **Abgrenzung & Grenzen:** Grenzen und Stolpersteine:
- **Verletzung des [[Information_Hiding]]**: Besucher benötigen oft Zugriff auf interne Details der Elementklassen, was die Kapselung schwächt.
- **Hoher Aufwand bei häufigen Änderungen**: Jede neue Elementklasse erfordert Anpassungen aller Besucher (vgl. [[Double_Dispatch]]).
- **Überdesign-Risiko**: Bei einfachen Strukturen oder seltenen Erweiterungen ist das Pattern unnötig komplex.
- **Zyklische Abhängigkeiten**: Besucher und Elemente hängen voneinander ab, was die Wartbarkeit erschweren kann.

Alternativen:
- **[[Strategy_Pattern]]** für austauschbare Algorithmen ohne Traversierung.
- **[[Iterator_Pattern]]** für reine Traversierung ohne Operationen.
- **[[Decorator_Pattern]]** für dynamische Funktionserweiterung einzelner Objekte.
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel zeigt eine vereinfachte Implementierung des Visitor_Patterns zur Summierung von Werten in einer verketteten Liste (vgl. Kontext). Die `Elem`-Klasse repräsentiert die [[Objektstruktur]], während `Sum` als konkreter Besucher agiert. Das [[Klassendiagramm]] würde die Schnittstellen `Visitor` und `Element` sowie deren Implementierungen darstellen.', 'java_code': {'element_interface': 'public interface Element {\n    void accept(Visitor v);\n    int getVal();\n    Element getNext();\n    boolean isEmpty();\n}', 'concrete_element': 'public class Elem implements Element {\n    private final int val;\n    private final Element tail;\n\n    public Elem(int val, Element tail) {\n        this.val = val;\n        this.tail = tail;\n    }\n\n    @Override\n    public void accept(Visitor v) {\n        v.visit(this);\n    }\n\n    @Override\n    public int getVal() {\n        return val;\n    }\n\n    @Override\n    public Element getNext() {\n        return tail;\n    }\n\n    @Override\n    public boolean isEmpty() {\n        return tail == null;\n    }\n}', 'visitor_interface': 'public interface Visitor {\n    void visit(Element e);\n}', 'concrete_visitor': 'public class Sum implements Visitor {\n    private int sum = 0;\n\n    public Sum(Element e) {\n        e.accept(this);\n    }\n\n    @Override\n    public void visit(Element e) {\n        sum += e.getVal();\n        if (!e.isEmpty()) {\n            e.getNext().accept(this);\n        }\n    }\n\n    public int getSum() {\n        return sum;\n    }\n}', 'anwendung': 'public class Main {\n    public static void main(String[] args) {\n        Element list = new Elem(1, new Elem(2, new Elem(3, null)));\n        Sum sumVisitor = new Sum(list);\n        System.out.println("Summe: " + sumVisitor.getSum()); // Ausgabe: 6\n    }\n}'}, 'uml_beschreibung': {'mermaid_diagramm': 'classDiagram\n    class Element {\n        <<interface>>\n        +accept(Visitor v)\n        +getVal() int\n        +getNext() Element\n        +isEmpty() boolean\n    }\n    \n    class Elem {\n        -val: int\n        -tail: Element\n        +accept(Visitor v)\n        +getVal() int\n        +getNext() Element\n        +isEmpty() boolean\n    }\n    \n    class Visitor {\n        <<interface>>\n        +visit(Element e)\n    }\n    \n    class Sum {\n        -sum: int\n        +Sum(Element e)\n        +visit(Element e)\n        +getSum() int\n    }\n    \n    Element <|-- Elem\n    Visitor <|-- Sum\n    Element --> Visitor : <<uses>>\n    Sum --> Element : <<traverses>>'}}
