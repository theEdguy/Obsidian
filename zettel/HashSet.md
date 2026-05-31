---
id: b209f606-9d14-4d55-a398-bed6f9020b8a
title: "HashSet"
date: 2026-05-31
tags:
  - software_engineering
  - java_collections
  - datenstrukturen
  - algorithmen
  - objektbeziehungen
  - performance
  - draft
source: "Klausur_Referenz"
---

# [[HashSet]]

- **Kernkonzept:** Ein `HashSet` ist eine Implementierung des [[Set]]-Interfaces in Java, die eine ungeordnete Sammlung von eindeutigen Elementen darstellt. Sie basiert auf einer [[Hash-Tabelle]] und nutzt die Methoden `hashCode()` und `equals()` der gespeicherten Objekte, um die Eindeutigkeit der Elemente zu gewährleisten. Im Gegensatz zu Listen erlaubt ein `HashSet` keine Duplikate und bietet durchschnittlich konstante Zeitkomplexität (O(1)) für Einfüge-, Lösch- und Suchoperationen.
- **Nutzen & Zweck:** Ein `HashSet` wird primär verwendet, um:
- **Eindeutigkeit** von Elementen sicherzustellen (z. B. zur Vermeidung von Duplikaten in Sammlungen).
- **Schnelle Zugriffe** auf Elemente zu ermöglichen, insbesondere wenn die Reihenfolge irrelevant ist.
- **Effiziente Mengenoperationen** wie Vereinigung, Schnitt oder Differenz durchzuführen (in Kombination mit anderen [[Collection]]-Typen).

Typische Anwendungsfälle sind:
- Verwaltung von Nachbarschaftsbeziehungen in Graphen (wie im Kontextbeispiel mit `Node`-Klassen).
- Implementierung von [[Assoziation]]en zwischen Objekten (z. B. bidirektionale Beziehungen wie im `Assigner`-Beispiel).
- Caching oder Lookup-Tabellen, bei denen schnelle Existenzprüfungen erforderlich sind.
- **Abgrenzung & Grenzen:** - **Keine garantierte Reihenfolge**: Die Iterationsreihenfolge ist nicht vorhersehbar und kann sich bei Änderungen der Sammlung ändern. Für geordnete Mengen eignet sich stattdessen ein `LinkedHashSet` oder `TreeSet`.
- **Null-Werte**: Ein `HashSet` erlaubt genau ein `null`-Element, da `null` als eindeutiger Wert behandelt wird.
- **Performance-Abhängigkeit von `hashCode()`**: Schlechte Implementierungen der `hashCode()`-Methode (z. B. mit vielen Kollisionen) können die Performance auf O(n) verschlechtern.
- **Nicht thread-sicher**: Für parallele Zugriffe muss eine Synchronisation (z. B. via `Collections.synchronizedSet()`) oder eine thread-sichere Alternative wie `ConcurrentHashMap` verwendet werden.
- **Speicherbedarf**: Durch die interne [[Hash-Tabelle]] verbraucht ein `HashSet` mehr Speicher als eine einfache Liste.
- **Beispiel / Code:** {'java': {'beschreibung': 'Beispiel zur bidirektionalen Beziehung zwischen Objekten (analog zum Kontext):', 'code': 'import java.util.HashSet;\nimport java.util.Set;\n\nclass A {\n    private Set<B> myBs = new HashSet<>();\n    \n    public void addB(B b) {\n        if (myBs.size() < 2 && b.getMyAs().size() < 2) {\n            myBs.add(b);\n            b.getMyAs().add(this);\n        }\n    }\n    \n    public Set<B> getMyBs() {\n        return new HashSet<>(myBs); // Defensives Kopieren\n    }\n}\n\nclass B {\n    private Set<A> myAs = new HashSet<>();\n    \n    public Set<A> getMyAs() {\n        return new HashSet<>(myAs); // Defensives Kopieren\n    }\n}\n\npublic class Main {\n    public static void main(String[] args) {\n        A a1 = new A();\n        A a2 = new A();\n        B b1 = new B();\n        B b2 = new B();\n        \n        a1.addB(b1); // Erfolgreich\n        a1.addB(b2); // Erfolgreich\n        a1.addB(b1); // Ignoriert (Duplikat)\n        a2.addB(b1); // Erfolgreich (b1 hat jetzt 2 As)\n        a2.addB(b2); // Ignoriert (a2 hat bereits 2 Bs)\n    }\n}'}, 'uml': {'beschreibung': 'UML-Klassendiagramm zur Veranschaulichung der bidirektionalen Beziehung (Mermaid-Syntax):', 'diagramm': 'classDiagram\n    class A {\n        -Set~B~ myBs\n        +addB(B b)\n        +getMyBs() Set~B~\n    }\n    class B {\n        -Set~A~ myAs\n        +getMyAs() Set~A~\n    }\n    A "1" --> "*" B : myBs\n    B "1" --> "*" A : myAs'}}
