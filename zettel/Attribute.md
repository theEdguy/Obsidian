---
id: 8f07d38b-a6d8-4d53-84c8-404705cbcc1c
title: "Attribute"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_04"
---

# [[Attribute]]

- **Kernkonzept:** Attribute sind strukturelle [[Bestandteil|Bestandteile]] von [[Klasse|Klassen]] in der [[objektorientierte_Modellierung|objektorientierten Modellierung]] und [[Programmierung]], die die [[Eigenschaft|Eigenschaften]] oder Daten von [[Objekt|Objekten]] beschreiben. Sie definieren den [[Zustand]] eines [[Objekt|Objekts]] und repräsentieren dessen Merkmale in einem [[Modell]] oder System, einschließlich Typ, Sichtbarkeit, Multiplizität und möglichen [[Einschränkung|Einschränkungen]] gemäß [[UML]].
- **Nutzen & Zweck:** Attribute ermöglichen die präzise Abbildung realer oder abstrakter [[Eigenschaft|Eigenschaften]] von [[Objekt|Objekten]] in einem System und lösen das Problem der unklaren oder impliziten Datenhaltung, indem sie explizit festlegen, welche Informationen eine [[Klasse]] speichern und verwalten muss. Sie tragen zur [[Konsistenz]], [[Wiederverwendbarkeit]] und [[Verständlichkeit]] von [[Modell|Modellen]] in der [[objektorientierte_Analyse|objektorientierten Analyse]] und [[Designphase]] bei. Durch die klare Definition von Daten und deren [[Zusammenhang|Zusammenhängen]] wird die [[Modellierung]] von [[Objekt|Objekten]] intuitiver, kommunikativer und methodisch durchgängig – von der Analyse bis zur Implementierung. Attribute unterstützen zudem die [[Kapselung]] von Daten und deren [[Strukturierung]], was die [[Kohäsion]] innerhalb einer [[Klasse]] erhöht.
- **Abgrenzung & Grenzen:** Attribute sollten nicht genutzt werden, wenn es um dynamisches [[Verhalten]] oder funktionale Logik geht – hierfür sind [[Operation]]en oder [[Methode|Methoden]] zuständig. Im Gegensatz zu [[Attribut|Attributen]], die den [[Zustand]] eines [[Objekt|Objekts]] beschreiben, definieren [[Operation]]en dessen [[Verhalten]]. Sie sind zudem ungeeignet für abgeleitete oder berechnete Werte, die sich aus anderen [[Attribut|Attributen]] oder [[Operation]]en ergeben; hier sind abgeleitete [[Attribut|Attribute]] (mit vorangestelltem '/') oder [[Methode|Methoden]] vorzuziehen. Für die Abbildung komplexer [[Beziehung|Beziehungen]] zwischen [[Klasse|Klassen]] (z. B. [[Assoziation|Assoziationen]], [[Aggregation]], [[Vererbung]]) sind separate [[Modellierungselement|Modellierungselemente]] wie [[Relation]]en oder [[Vererbungshierarchie|Vererbungshierarchien]] besser geeignet. In rein prozeduralen Ansätzen oder datenbankzentrierten Systemen können [[Attribut|Attribute]] durch einfache Datensätze ersetzt werden, verlieren dann jedoch die Vorteile der [[Kapselung]] und [[Objektidentität]].
- **Beispiel / Code:** ```java
class Mitglied {
    // Attribute definieren den Zustand des Objekts mit Sichtbarkeit, Typ und Initialwerten
    private String name;               // Sichtbarkeit: private, Typ: String
    protected String adresse;          // Sichtbarkeit: protected, Typ: String
    public int alter;                  // Sichtbarkeit: public, Typ: int
    private int leistungspunkte = 0;   // Initialwert: 0
    
    // Abgeleitetes Attribut (berechnet aus anderen Attributen)
    public int getVolljaehrigkeit() {
        return (alter >= 18) ? 1 : 0;
    }
    
    // UML-Notation als Kommentar (Sichtbarkeit, Name, Typ, Multiplizität, Initialwert, Einschränkung):
    // +name: String [1] = "Unbekannt"
    // #adresse: String [1]
    // -alter: int [1]
    // ~ /leistungspunkte: Integer = 0 {leistungspunkte >= 0}
    
    // Konstruktor zur Initialisierung der Attribute
    public Mitglied(String name, String adresse, int alter) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
    }
    
    // Methode zur Aktualisierung eines Attributs
    public void aktualisiereLeistung(int neuePunkte) {
        if (neuePunkte >= 0) {
            this.leistungspunkte = neuePunkte;
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4b
- **Vorgänger / Parent:** [[UML-Klassendiagramm]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
