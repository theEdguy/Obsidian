---
id: 3193a722-999b-4763-bd6d-ad73aa736039
title: "Liste_Datenstruktur"
date: 2026-05-31
tags:
  - software_engineering
  - datenstrukturen
  - uml
  - klassendiagramm
  - java
  - objektorientierung
  - draft
source: "Klausur_Referenz"
---

# [[Liste_Datenstruktur]]

- **Kernkonzept:** Eine [[Datenstruktur]], die eine geordnete Sammlung von Elementen gleichen oder unterschiedlichen Typs speichert. Listen ermöglichen den Zugriff auf Elemente über Indizes, das Einfügen, Löschen und Iterieren von Elementen. Im Kontext von [[Klassendiagramm|Klassendiagrammen]] (UML) wird eine Liste oft als *List Compartment* dargestellt, um Attribute, Operationen oder andere Gruppierungen zu strukturieren. Listen können sowohl auf [[Analyseebene]] (konzeptionell) als auch auf [[Designniveau]] (technisch) modelliert werden, wobei sich die Granularität der Darstellung unterscheidet (z. B. `name: Text` vs. `+name: String`).
- **Nutzen & Zweck:** Listen dienen der Organisation von Daten in sequenzieller Form und bieten folgende Vorteile:
- **Flexibilität**: Dynamische Größenanpassung (im Gegensatz zu Arrays fester Länge).
- **Wiederverwendbarkeit**: Standardisierte Schnittstellen (z. B. `List<T>` in Java) ermöglichen generische Algorithmen (z. B. Sortieren, Filtern).
- **Modellierung**: In [[Klassendiagramm|Klassendiagrammen]] helfen Listen, komplexe Beziehungen (z. B. 1-zu-n-Assoziationen) oder gruppierte Attribute (z. B. `leistung: Punkte[]`) abzubilden.
- **Datenbankdesign**: Listen können als Grundlage für [[Relationale_Datenbanken|Tabellenbeziehungen]] (z. B. Fremdschlüssel) oder NoSQL-Strukturen (z. B. JSON-Arrays) dienen.
- **Abgrenzung & Grenzen:** Listen sind abzugrenzen von:
- **Sets**: Ungeordnete Sammlungen ohne Duplikate (z. B. `Set<T>` in Java). Die Wahl zwischen Liste und Set hängt von der Anforderung an Eindeutigkeit und Reihenfolge ab.
- **Arrays**: Statische Datenstrukturen mit fester Länge und direkter Speicherallokation (performanter, aber unflexibel).
- **Maps/Dictionaries**: Assoziative Sammlungen mit Schlüssel-Wert-Paaren (z. B. `Map<K,V>`), die keinen sequenziellen Zugriff ermöglichen.

**Stolpersteine**:
- **Performance**: Listenoperationen wie Einfügen/Löschen in der Mitte können ineffizient sein (O(n) bei verketteten Listen).
- **Typisierung**: In statisch typisierten Sprachen (z. B. Java) erfordern generische Listen explizite Typangaben (z. B. `List<String>`).
- **UML-Darstellung**: Auf [[Analyseebene]] werden Listen oft vereinfacht dargestellt (z. B. `adresse` statt `adressen: List<Anschrift>`), was zu Mehrdeutigkeiten führen kann. Im [[Designniveau]] müssen Implementierungsdetails (z. B. `ArrayList` vs. `LinkedList`) spezifiziert werden.
- **Beispiel / Code:** {'uml_klassendiagramm': {'beschreibung': 'UML-Klassendiagramm auf Analyse- und Designebene für eine `Mitglied`-Klasse mit Listenattributen.', 'mermaid_syntax': 'classDiagram\n    class Mitglied {\n        <<Analyse>>\n        -name: Text\n        -adressen: Adresse[]\n        -alter: Zahl\n        -leistungen: Punkte[]\n        +leistungsprognose(datum: Datum): Punkte\n    }\n    \n    class Mitglied_Design {\n        <<Design>>\n        -name: String\n        #adressen: List~Anschrift~\n        -alter: Date\n        ~leistungen: ArrayList~Integer~ = new ArrayList() {leistung > 0 && leistung < 1441}\n        +leistungsprognose(datum: Date): Integer\n        -tableName: String\n        -mitgliedId: Integer\n    }\n    \n    class Anschrift {\n        +strasse: String\n        +plz: String\n        +ort: String\n    }'}, 'java_implementation': {'beschreibung': 'Java-Implementierung der `Mitglied`-Klasse mit Listenattributen.', 'code': 'import java.util.ArrayList;\nimport java.util.Date;\nimport java.util.List;\n\npublic class Mitglied {\n    private String name;\n    protected List<Anschrift> adressen = new ArrayList<>();\n    private Date alter;\n    List<Integer> leistungen = new ArrayList<>();\n    \n    public Mitglied(String name, Date alter) {\n        this.name = name;\n        this.alter = alter;\n    }\n    \n    public void addLeistung(int punkte) {\n        if (punkte > 0 && punkte < 1441) {\n            leistungen.add(punkte);\n        }\n    }\n    \n    public int leistungsprognose(Date datum) {\n        // Beispielhafte Implementierung\n        return leistungen.stream().mapToInt(Integer::intValue).sum();\n    }\n}\n\nclass Anschrift {\n    String strasse;\n    String plz;\n    String ort;\n}'}}
