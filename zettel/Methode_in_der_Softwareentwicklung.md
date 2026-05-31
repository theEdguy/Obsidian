---
aliases:
- Methode
date: 2026-05-30
id: dde53423-38f4-4af8-8c95-534b8f56df5e
source: Klausur_Referenz
tags:
- software_engineering
- objektorientierte_programmierung
- kapselung
- polymorphismus
- entwurfsmuster
- uml
- java
- software_design
- draft
title: Methode_in_der_Softwareentwicklung
---

# [[Methode_in_der_Softwareentwicklung]]

- **Kernkonzept:** Eine **Methode** ist eine in einer [[Klasse]] definierte Funktion oder Prozedur, die das Verhalten von [[Objekten]] dieser Klasse beschreibt. Sie kapselt eine spezifische Logik, die auf den Attributen der Klasse operiert oder mit anderen Objekten interagiert. Methoden sind zentral für die [[Objektorientierte_Programmierung]] (OOP), da sie die [[Kapselung]] und [[Abstraktion]] von Funktionalität ermöglichen. Sie können Parameter entgegennehmen, Werte zurückgeben und den internen Zustand eines Objekts modifizieren oder abfragen. Methoden werden oft in [[Schnittstellen]] oder [[Abstrakte_Klassen]] deklariert, um Verträge für die Implementierung vorzugeben.
- **Nutzen & Zweck:** Methoden dienen folgenden Zwecken:
1. **Verhaltensdefinition**: Sie legen fest, *was* ein Objekt tun kann (z. B. `leistungsprognose(Date datum)` in der Klasse `Mitglied`).
2. **Wiederverwendbarkeit**: Durch Auslagerung von Logik in Methoden wird Code modular und wiederverwendbar.
3. **Kapselung**: Methoden verstecken Implementierungsdetails und exponieren nur eine kontrollierte Schnittstelle (z. B. öffentliche Methoden wie `public int berechneAlter()`).
4. **Polymorphismus**: Methoden ermöglichen [[Überschreiben]] (in Unterklassen) oder [[Überladen]], was flexible und erweiterbare Systeme unterstützt.
5. **Iterative Anpassung**: Wie im Kontext erwähnt, erlauben Methoden im [[Iterativer_Prozess]] eine schrittweise Verfeinerung der Logik, ohne die gesamte Klasse zu ändern.

Beispiele:
- **Getter/Setter-Methoden**: Steuern den Zugriff auf Attribute (z. B. `getName()`, `setAdresse(Anschrift a)`).
- **Geschäftslogik**: Methoden wie `leistungsprognose()` implementieren domänenspezifische Regeln.
- **Hilfsmethoden**: Private Methoden (z. B. `private boolean istVolljährig()`) strukturieren komplexe Logik intern.
- **Abgrenzung & Grenzen:** 1. **Abgrenzung zu Funktionen**: Methoden sind immer an eine Klasse gebunden, während Funktionen (in nicht-OOP-Sprachen) unabhängig existieren. In Java gibt es keine freien Funktionen – alles ist eine Methode.
2. **Abgrenzung zu Attributen**: Methoden repräsentieren *Verhalten*, Attribute repräsentieren *Zustand*. Eine Methode wie `getAlter()` gibt den Wert eines Attributs zurück, ist aber selbst kein Attribut.
3. **Stolpersteine**:
   - **Zu große Methoden**: Methoden sollten eine klare, *einzelne* Verantwortung haben (vgl. [[Single_Responsibility_Principle]]). Lange Methoden sind schwer wartbar.
   - **Seiteneffekte**: Methoden, die den Zustand unerwartet ändern (z. B. `void updateAlter()` modifiziert `name`), verletzen das [[Command-Query_Separation_Principle]].
   - **Überladung vs. Überschreiben**: Überladene Methoden (gleicher Name, unterschiedliche Parameter) sind *kein* [[Polymorphismus]]. Überschriebene Methoden (gleiche Signatur in Unterklassen) schon.
   - **Zugriffsmodifikatoren**: Falsche Sichtbarkeit (z. B. `public` statt `private`) kann die [[Kapselung]] brechen.
4. **Grenzen**: Methoden können keine Klassen oder Schnittstellen *definieren* – das ist Aufgabe der Klassendeklaration. Sie sind immer *Teil* einer Klasse.
- **Beispiel / Code:** {'beschreibung': 'Java-Implementierung der Klasse `Mitglied` aus dem Kontext, erweitert um Methoden zur Veranschaulichung von Kapselung, Polymorphismus und Geschäftslogik. Das Beispiel zeigt auch eine private Hilfsmethode und eine überschreibbare Methode für Unterklassen.', 'code': 'public class Mitglied {\n    private String name;\n    private Anschrift adresse;\n    private Date geburtsdatum; // Statt \'alter\' für bessere Berechnung\n\n    // Konstruktor\n    public Mitglied(String name, Anschrift adresse, Date geburtsdatum) {\n        this.name = name;\n        this.adresse = adresse;\n        this.geburtsdatum = geburtsdatum;\n    }\n\n    // Öffentliche Methode zur Leistungsprognose (Geschäftslogik)\n    public int leistungsprognose(Date datum) {\n        int alter = berechneAlter(datum);\n        if (alter < 18) {\n            return 50; // Standardwert für Jugendliche\n        } else if (alter >= 18 && alter < 65) {\n            return 100; // Standardwert für Erwachsene\n        } else {\n            return 75; // Standardwert für Senioren\n        }\n    }\n\n    // Private Hilfsmethode (Kapselung)\n    private int berechneAlter(Date datum) {\n        // Vereinfachte Berechnung (Jahr - Geburtsjahr)\n        return datum.getYear() - this.geburtsdatum.getYear();\n    }\n\n    // Getter/Setter (Kontrollierter Zugriff)\n    public String getName() {\n        return name;\n    }\n\n    public void setAdresse(Anschrift adresse) {\n        this.adresse = adresse;\n    }\n\n    // Überschreibbare Methode (Polymorphismus)\n    public void druckeMitgliedsdaten() {\n        System.out.println("Name: " + name + ", Adresse: " + adresse);\n    }\n}\n\n// Beispiel für eine Unterklasse, die die Methode überschreibt\npublic class PremiumMitglied extends Mitglied {\n    private int bonusPunkte;\n\n    public PremiumMitglied(String name, Anschrift adresse, Date geburtsdatum, int bonusPunkte) {\n        super(name, adresse, geburtsdatum);\n        this.bonusPunkte = bonusPunkte;\n    }\n\n    @Override\n    public int leistungsprognose(Date datum) {\n        // Erweiterte Logik für Premium-Mitglieder\n        int basisPrognose = super.leistungsprognose(datum);\n        return basisPrognose + (bonusPunkte / 10);\n    }\n}', 'uml_diagramm': '```mermaid\nclassDiagram\n    class Mitglied {\n        -String name\n        -Anschrift adresse\n        -Date geburtsdatum\n        +Mitglied(String, Anschrift, Date)\n        +leistungsprognose(Date) int\n        +getName() String\n        +setAdresse(Anschrift) void\n        +druckeMitgliedsdaten() void\n        -berechneAlter(Date) int\n    }\n    class PremiumMitglied {\n        -int bonusPunkte\n        +PremiumMitglied(String, Anschrift, Date, int)\n        +leistungsprognose(Date) int\n    }\n    Mitglied <|-- PremiumMitglied\n```'}
