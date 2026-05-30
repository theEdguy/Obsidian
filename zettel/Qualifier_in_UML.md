---
id: 474ec929-19c5-47d1-851f-36044efacf3e
title: "Qualifier_in_UML"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - klassendiagramm
  - modellierung
  - assoziation
  - entwurfsmuster
  - draft
source: "Klausur_Referenz"
---

# [[Qualifier_in_UML]]

- **Kernkonzept:** Ein **Qualifier** in [[UML]] ist ein Attribut oder eine Gruppe von Attributen, die an einer [[Assoziation]] zwischen zwei [[Klassen]] angebracht werden, um die Zielmenge der verknüpften Objekte einzuschränken. Der Qualifier fungiert als Schlüssel, der die Navigation von einem Quellobjekt zu einem oder mehreren spezifischen Zielobjekten ermöglicht. Er reduziert die Kardinalität der Assoziation auf der Zielseite, indem er die Auswahl der verknüpften Objekte präzisiert (z. B. von * zu 1).
- **Nutzen & Zweck:** Qualifier werden eingesetzt, um:
1. **Präzisere Modellierung** von Beziehungen zu ermöglichen, insbesondere wenn eine [[Klasse]] über ein Schlüsselattribut auf eine andere zugreift (z. B. Zugriff auf ein `Konto` über eine `Kontonummer`).
2. **Kardinalitäten** in [[Assoziationen]] zu verfeinern, indem sie die Zielmenge der verknüpften Objekte auf Basis eines Schlüssels einschränken.
3. **Navigierbarkeit** in [[Klassendiagrammen]] zu verbessern, indem sie den Zugriffspfad zu Objekten explizit machen.
4. **Implementierungsnähe** zu fördern, da Qualifier oft direkt in [[HashMaps]] oder ähnliche Datenstrukturen übersetzt werden können.
- **Abgrenzung & Grenzen:** 1. **Kein Ersatz für Attribute**: Qualifier sind *keine* Attribute der Zielklasse, sondern gehören zur Assoziation selbst. Sie definieren keinen Zustand der Klasse, sondern einen Zugriffsmechanismus.
2. **Keine bidirektionale Wirkung**: Ein Qualifier wirkt nur in *eine* Richtung der Assoziation (von der Quell- zur Zielklasse).
3. **Stolpersteine**: 
   - **Mehrdeutigkeit**: Wenn der Qualifier-Wert nicht eindeutig ist, kann die Kardinalität auf der Zielseite unklar bleiben.
   - **Übermodellierung**: Qualifier sollten nur verwendet werden, wenn sie die Semantik der Beziehung *wesentlich* präzisieren. Andernfalls reichen einfache Assoziationen.
   - **Implementierung**: Nicht alle Programmiersprachen unterstützen Qualifier direkt (z. B. Java erfordert manuelle Umsetzung via `Map<QualifierTyp, ZielTyp>`).
4. **Abgrenzung zu [[Schlüsselattributen]]**: Qualifier sind *keine* Primärschlüssel der Zielklasse, sondern ein Konstrukt der Assoziationsebene.
- **Beispiel / Code:** {'uml_beschreibung': '```mermaid\nclassDiagram\n    class Bank {\n        +String name\n    }\n    class Konto {\n        +String kontonummer\n        +double saldo\n    }\n    Bank "1" --> "*" Konto : verwaltet\n    Bank --> Konto : {qualifier = kontonummer}\n```\n\n**Erläuterung**:\n- Eine `Bank` verwaltet mehrere `Konto`-Objekte.\n- Der Qualifier `kontonummer` an der Assoziation ermöglicht es, von einer `Bank` aus *genau ein* `Konto` über dessen Kontonummer zu referenzieren (Kardinalität auf der Zielseite wird von * zu 1 reduziert).\n- Ohne Qualifier wäre die Assoziation weniger präzise (z. B. müsste die `Bank` alle Konten durchsuchen).', 'java_umsetzung': '```java\nimport java.util.HashMap;\nimport java.util.Map;\n\nclass Bank {\n    private String name;\n    private Map<String, Konto> konten = new HashMap<>(); // Qualifier als Schlüssel\n\n    public Konto getKonto(String kontonummer) {\n        return konten.get(kontonummer); // Navigation via Qualifier\n    }\n    \n    public void addKonto(Konto konto) {\n        konten.put(konto.getKontonummer(), konto);\n    }\n}\n\nclass Konto {\n    private String kontonummer;\n    private double saldo;\n    // ...\n}\n```'}
