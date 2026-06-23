---
id: 56d42c9d-2368-4f2d-a5ea-2c7543776f5e
title: "Modularität"
date: 2026-06-23
tags:
  - software_engineering
  - designprinzip
  - architektur
  - modularität
  - design
  - draft
source: "software_engineering_kapitel_07"
---

# [[Modularität]]

- **Kernkonzept:** [[Modularität]] ist ein zentrales [[Designprinzip]] im [[Software_Engineering]], bei dem ein [[System]] in unabhängige, austauschbare [[Modul|Module]] oder [[Komponente|Komponenten]] zerlegt wird. Jedes [[Modul]] kapselt eine spezifische [[Funktionalität]] und interagiert über klar definierte [[Schnittstelle|Schnittstellen]], ohne interne [[Implementierung]]sdetails preiszugeben.
- **Nutzen & Zweck:** [[Modularität]] löst das Problem der [[Komplexität]] und Unübersichtlichkeit großer [[Softwaresystem|Softwaresysteme]], indem sie die [[Entwicklung]], [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Wiederverwendbarkeit]] von [[Code]] signifikant verbessert. Durch die Aufteilung in [[Modul|Module]] können [[Team|Teams]] parallel arbeiten, [[Fehler]] lokalisiert und behoben werden, ohne das gesamte [[System]] zu beeinträchtigen. Zudem fördert sie die [[Wiederverwendbarkeit]] von [[Code]] und reduziert [[Abhängigkeit|Abhängigkeiten]], was die [[Skalierbarkeit]] und [[Anpassungsfähigkeit]] des [[Systems]] erhöht. [[Modularität]] ermöglicht zudem die gezielte [[Optimierung]] einzelner [[Komponente|Komponenten]], ohne andere Teile des [[Systems]] zu beeinflussen.
- **Abgrenzung & Grenzen:** [[Modularität]] ist kein Allheilmittel und sollte nicht eingesetzt werden, wenn das [[System]] zu klein oder trivial ist, da der Overhead durch [[Schnittstelle|Schnittstellen]] und [[Abstraktion|Abstraktionen]] die [[Entwicklung]] unnötig verkompliziert. Im Gegensatz zu [[Monolith]]-Architekturen, bei denen alle [[Funktionalität|Funktionalitäten]] eng verzahnt sind, erfordert [[Modularität]] zusätzliche [[Planung]] und [[Disziplin]] bei der Definition von [[Schnittstelle|Schnittstellen]]. Bei hochgradig [[Performance]]-kritischen [[System|Systemen]] können modulare Ansätze durch zusätzlichen Overhead nachteilig sein, insbesondere wenn [[Latenz]] oder [[Ressourcenverbrauch]] entscheidend sind. Zudem ersetzt [[Modularität]] keine guten [[Designentscheidung|Designentscheidungen]] oder [[Dokumentation]], sondern setzt diese voraus. Sie ist kein Ersatz für [[Kohäsion]] oder [[Lose_Kopplung]], sondern ein übergeordnetes [[Prinzip]], das diese [[Konzept|Konzepte]] unterstützt.
- **Beispiel / Code:** ```java
// Beispiel für ein modulares Design in Java: Trennung von Schnittstelle und Implementierung

// Schnittstelle (Interface) als Vertrag für das Modul [[Schnittstelle|Schnittstellen]]
public interface MitgliedVerwaltung {
    void mitgliedHinzufuegen([[Mitglied]] mitglied);
    void mitgliedAktualisieren([[Mitglied]] mitglied);
    void mitgliedLoeschen(String mitgliedId);
}

// Implementierung des Moduls (kann ausgetauscht werden, ohne andere [[Modul|Module]] zu beeinflussen)
public class MitgliedVerwaltungImpl implements MitgliedVerwaltung {
    @Override
    public void mitgliedHinzufuegen([[Mitglied]] mitglied) {
        // Logik zum Hinzufügen eines [[Mitglied|Mitglieds]]
    }
    
    @Override
    public void mitgliedAktualisieren([[Mitglied]] mitglied) {
        // Logik zum Aktualisieren eines [[Mitglied|Mitglieds]]
    }
    
    @Override
    public void mitgliedLoeschen(String mitgliedId) {
        // Logik zum Löschen eines [[Mitglied|Mitglieds]]
    }
}

// Beispiel für ein modulares System mit mehreren [[Komponente|Komponenten]]
public class ECommerceSystem {
    private MitgliedVerwaltung mitgliedVerwaltung;
    private Bestellabwicklung bestellabwicklung;
    private Produktkatalog produktkatalog;
    
    public ECommerceSystem() {
        this.mitgliedVerwaltung = new MitgliedVerwaltungImpl();
        this.bestellabwicklung = new BestellabwicklungImpl();
        this.produktkatalog = new ProduktkatalogImpl();
    }
    
    // Weitere Methoden zur Interaktion zwischen den [[Modul|Modulen]]
}
```

**Modulares System (textuelle Darstellung):**
- [[Modul]]: [[Benutzerverwaltung]] ([[Authentifizierung]], [[Profilverwaltung]])
- [[Modul]]: [[Bestellabwicklung]] ([[Warenkorb]], [[Zahlung]])
- [[Modul]]: [[Produktkatalog]] ([[Suche]], [[Filter]])
- Jedes [[Modul]] kann unabhängig entwickelt, getestet und gewartet werden.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a1
- **Vorgänger / Parent:** [[Architekturprinzipien]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Architekturprinzipien]]
  - [[Software-Design]]
