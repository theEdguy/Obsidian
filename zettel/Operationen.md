---
id: c1043f66-c829-4211-8649-3a691657573c
title: "Operationen"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - programmierung
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_04"
---

# [[Operationen]]

- **Kernkonzept:** Operationen in der [[objektorientierte_Programmierung|objektorientierten Programmierung]] und [[Modellierung]] (insbesondere in [[UML]]) beschreiben das Verhalten von [[Objekt|Objekten]], indem sie definieren, welche Aktionen oder [[Funktion|Funktionen]] ein [[Objekt]] ausführen kann. Sie sind Teil der [[Schnittstelle]] einer [[Klasse]] und ermöglichen die Interaktion mit den [[Attribut|Attributen]] eines [[Objekt|Objekts]], wobei sie die [[Kapselung]] und [[Kohäsion]] des Systems fördern.
- **Nutzen & Zweck:** Operationen existieren, um die [[Funktionalität]] von [[Objekt|Objekten]] zu kapseln und eine klare, kontrollierte [[Schnittstelle]] für deren Nutzung bereitzustellen. Sie lösen das Problem der direkten Manipulation von [[Attribut|Attributen]], indem sie sicherstellen, dass Zustandsänderungen nur über definierte [[Methode|Methoden]] erfolgen. Dadurch wird die [[Wartbarkeit]], [[Sicherheit]] und [[Konsistenz]] des Systems verbessert, da interne [[Implementierungsdetail|Implementierungsdetails]] verborgen bleiben und Änderungen zentral gesteuert werden können. Zudem ermöglichen Operationen die Modellierung von dynamischem Verhalten in [[objektorientierte_Programmierung|objektorientierten Systemen]], strukturieren die Kommunikation zwischen [[Objekt|Objekten]] und fördern die [[Wiederverwendbarkeit]] von [[Code]]. Durch die Definition des [[Interface|Interfaces]] einer [[Klasse]] wird [[lose_Kopplung|lose Kopplung]] unterstützt, was die [[Skalierbarkeit]] und [[Modularität]] des Systems erhöht.
- **Abgrenzung & Grenzen:** Operationen sollten nicht genutzt werden, wenn es um reine Datenhaltung ohne verhaltensbezogene [[Logik]] geht, wie z. B. bei einfachen [[Datenstruktur|Datenstrukturen]] ohne komplexe Geschäftsregeln. In solchen Fällen können Alternativen wie direkte [[Attribut|Attributzugriffe]] oder prozedurale [[Funktion|Funktionen]] effizienter sein. Zudem unterscheiden sich Operationen von globalen [[Funktion|Funktionen]] oder Prozeduren, da sie immer an ein [[Objekt]] gebunden sind und dessen [[Zustand]] beeinflussen. In nicht-objektorientierten Paradigmen, wie der [[funktionale_Programmierung|funktionalen Programmierung]], werden ähnliche Konzepte durch reine [[Funktion|Funktionen]] ohne Zustandsbindung realisiert. Operationen sind zudem nicht für die reine Datenrepräsentation geeignet – hierfür sind [[Attribut|Attribute]] besser geeignet. Bei rein prozeduralen Ansätzen oder in [[funktionale_Programmierung|funktionalen Sprachen]] sind Operationen weniger sinnvoll, da sie den [[Zustand]] eines [[Objekt|Objekts]] voraussetzen.
- **Beispiel / Code:** ```java
class Mitglied {
    private String name;
    private int leistung;

    // Operation zur Berechnung der Leistungsprognose (mit erweitertem Beispiel)
    public int leistungsprognose(int zusatzPunkte) {
        // Einfache Berechnung mit Validierung
        if (zusatzPunkte < 0) {
            throw new IllegalArgumentException("Zusatzpunkte dürfen nicht negativ sein.");
        }
        return this.leistung + zusatzPunkte;
    }

    // Operation zur Leistungsprognose mit Datum (aus UML-Beispiel)
    public int leistungsprognose(java.util.Date datum) {
        // Beispielhafte Logik zur Berechnung der zukünftigen Leistung
        // (kann durch komplexere Algorithmen oder [[Entwurfsmuster|Muster]] wie [[Strategy_Pattern]] erweitert werden)
        return this.leistung + 10;
    }

    // Operation zum Aktualisieren der Leistung mit Validierung
    public void aktualisiereLeistung(int neuePunkte) {
        if (neuePunkte >= 0) {
            this.leistung = neuePunkte;
        } else {
            throw new IllegalArgumentException("Leistungspunkte dürfen nicht negativ sein.");
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4c
- **Vorgänger / Parent:** [[UML-Klassendiagramm]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
