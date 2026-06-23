---
id: 7dfb0df4-a01d-4f5c-912c-e203d6349144
title: "Kohäsion"
date: 2026-06-23
tags:
  - software_engineering
  - designprinzip
  - software_architektur
  - objektorientiertes_design
  - design_principle
  - oop
  - kohäsion
  - design
  - draft
source: "software_engineering_kapitel_07"
---

# [[Kohäsion]]

- **Kernkonzept:** [[Kohäsion]] ist ein zentrales [[Designprinzip]] in der [[Softwareentwicklung]], das beschreibt, wie stark die [[Funktionalität|Funktionalitäten]] und [[Verantwortung|Verantwortungen]] innerhalb eines [[Modul|Moduls]], einer [[Klasse]] oder [[Komponente]] miteinander in Beziehung stehen und ein gemeinsames, klar definiertes [[Ziel]] verfolgen. Hohe [[Kohäsion]] bedeutet, dass alle [[Element|Elemente]] einer Einheit eng auf eine logisch abgeschlossene, einheitliche [[Aufgabe]] ausgerichtet sind und keine fremden [[Verantwortlichkeit|Verantwortlichkeiten]] übernehmen.
- **Nutzen & Zweck:** [[Kohäsion]] dient primär der Verbesserung der [[Wartbarkeit]], [[Verständlichkeit]], [[Wiederverwendbarkeit]] und [[Modularität]] von [[Software]]. Durch die Bündelung verwandter [[Funktionalität|Funktionalitäten]] in einem [[Modul]] oder einer [[Klasse]] wird die [[Komplexität]] reduziert, da [[Entwickler]] sich auf klar abgegrenzte [[Aufgabe|Aufgaben]] konzentrieren können. Hohe [[Kohäsion]] verringert [[Abhängigkeit|Abhängigkeiten]] zwischen [[Modul|Modulen]], was [[Änderung|Änderungen]] erleichtert, [[Fehlerquelle|Fehlerquellen]] minimiert und das [[Refactoring]] unterstützt. Zudem fördert sie die [[Wiederverwendbarkeit]], da stark kohäsive Einheiten leichter in anderen [[Kontext|Kontexten]] eingesetzt werden können. Ein weiterer Vorteil ist die verbesserte [[Testbarkeit]], da isolierte [[Funktionalität|Funktionalitäten]] einfacher zu überprüfen sind. [[Kohäsion]] steht in enger Beziehung zum [[Single_Responsibility_Principle]], das fordert, dass eine [[Klasse]] oder ein [[Modul]] nur eine einzige [[Verantwortung]] übernehmen sollte.
- **Abgrenzung & Grenzen:** Hohe [[Kohäsion]] ist nicht immer trivial umzusetzen, insbesondere wenn [[Anforderung|Anforderungen]] komplex, widersprüchlich oder unklar sind. Ein übermäßiger Fokus auf [[Kohäsion]] kann zu einer Zersplitterung des [[Code|Codes]] in viele kleine [[Klasse|Klassen]] oder [[Modul|Module]] führen, was die [[Komplexität]] des [[Systems]] erhöhen und die [[Navigierbarkeit]] erschweren kann. Zudem ist [[Kohäsion]] von [[Lose_Kopplung]] abzugrenzen: Während [[Kohäsion]] die innere Stärke einer Einheit beschreibt, bezieht sich [[Lose_Kopplung]] auf die Minimierung der [[Abhängigkeit|Abhängigkeiten]] zwischen [[Modul|Modulen]] oder [[Klasse|Klassen]]. Ein Verstoß gegen das [[Single_Responsibility_Principle]] führt oft zu [[Geringe_Kohäsion|geringer Kohäsion]], da eine Einheit zu viele [[Verantwortlichkeit|Verantwortlichkeiten]] übernimmt. In Fällen, in denen [[Funktionalität|Funktionalitäten]] systemweit benötigt werden (z. B. [[Logging]] oder [[Authentifizierung]]), kann eine starke [[Kohäsion]] kontraproduktiv sein. Hier sind Alternativen wie [[Aspect-Oriented_Programming|aspektorientierte Programmierung]] oder zentrale [[Dienstmodul|Dienstmodule]] sinnvoller. Zu hohe [[Kohäsion]] kann zudem zu übermäßig granularen [[Modul|Modulen]] führen, die keine eigenständige Bedeutung haben und die [[Übersichtlichkeit]] beeinträchtigen.
- **Beispiel / Code:** ```java
// Beispiel für HOHE Kohäsion: Jede Klasse hat eine klare, fokussierte Verantwortung
class Order {
    private List<Item> items;

    public double calculateTotal() {
        return items.stream().mapToDouble(Item::getPrice).sum();
    }

    public void addItem(Item item) {
        items.add(item);
    }
}

// Weitere Beispiele für hohe Kohäsion durch klare Aufgabentrennung
public class AddressLabel {
    private String address;

    public String format() {
        return "Address: " + address;
    }
}

public class TelephoneLabel {
    private String phoneNumber;

    public String format() {
        return "Phone: " + phoneNumber;
    }
}

// Beispiel für HOHE Kohäsion: Eine Klasse mit klar abgegrenzter Verantwortlichkeit
public class MitgliedVerwaltung {
    private List<Mitglied> mitglieder;

    public void mitgliedHinzufuegen(Mitglied mitglied) {
        mitglieder.add(mitglied);
        benachrichtigeAbteilungsleiter(mitglied);
    }

    public void mitgliedAktualisieren(Mitglied mitglied) {
        // Logik zur Aktualisierung eines Mitglieds
    }

    private void benachrichtigeAbteilungsleiter(Mitglied mitglied) {
        // Logik zur Benachrichtigung
    }
}

// Beispiel für GERINGE Kohäsion: Eine Klasse mit gemischten Verantwortlichkeiten
public class MitgliedUndRechnungsVerwaltung {
    private List<Mitglied> mitglieder;
    private List<Rechnung> rechnungen;

    public void mitgliedHinzufuegen(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }

    public void rechnungErstellen(Rechnung rechnung) {
        rechnungen.add(rechnung);
    }
    // Weitere Methoden für Rechnungsverwaltung
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a2
- **Vorgänger / Parent:** [[Architekturprinzipien]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Architekturprinzipien]]
  - [[Software-Design]]
