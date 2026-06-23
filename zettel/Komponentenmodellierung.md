---
id: e9a27a8a-ed0d-4100-b8fb-95b5f20d7c37
title: "Komponentenmodellierung"
date: 2026-06-23
tags:
  - software_engineering
  - architektur
  - komponenten
  - design
  - draft
source: "software_engineering_kapitel_09"
---

# [[Komponentenmodellierung]]

- **Kernkonzept:** Die [[Komponentenmodellierung]] ist ein architektonischer Ansatz im [[Software_Engineering]], bei dem ein [[System]] in klar abgegrenzte, wiederverwendbare und austauschbare [[Komponente|Komponenten]] zerlegt wird, die über definierte [[Schnittstelle|Schnittstellen]] interagieren. Das [[Komponentenmodell]] als spezifisches Architekturkonzept unterstreicht diese Prinzipien, indem es die [[Modularisierung]] durch [[Lose_Kopplung|lose Kopplung]] und hohe [[Kohäsion]] fördert und so die [[Komplexitätsbewältigung]] in großen [[Softwaresystem|Systemen]] ermöglicht.
- **Nutzen & Zweck:** Die [[Komponentenmodellierung]] löst das Problem der [[Komplexitätsbewältigung]] in großen [[Softwaresystem|Systemen]], indem sie die Entwicklung, [[Wartbarkeit]], [[Skalierbarkeit]] und [[Wiederverwendbarkeit]] durch [[Modularisierung]] verbessert. Sie reduziert Abhängigkeiten zwischen [[Komponente|Komponenten]] und ermöglicht die parallele Entwicklung durch klare Verantwortungsbereiche, was die [[Testbarkeit]] und [[Fehlerisolierung]] erhöht. Zudem erleichtert sie das [[Refactoring]] und die gezielte Anpassung einzelner [[Komponente|Komponenten]] ohne Auswirkungen auf das Gesamtsystem. Im Vergleich zu monolithischen Architekturen schafft das [[Komponentenmodell]] eine strukturierte Organisation von [[Subsystem|Subsystemen]] und deren Beziehungen, was die Zusammenarbeit in [[Entwicklungsteam|Teams]] und die Integration in unterschiedliche [[Kontext|Kontexte]] begünstigt. Durch die Kapselung spezifischer [[Funktionalität|Funktionalitäten]] in unabhängigen [[Komponente|Komponenten]] wird die [[Wiederverwendbarkeit]] in verschiedenen Projekten oder [[Modul|Modulen]] gefördert.
- **Abgrenzung & Grenzen:** Die [[Komponentenmodellierung]] sollte nicht eingesetzt werden, wenn das [[System]] zu klein oder trivial ist, da der Overhead durch [[Schnittstelle|Schnittstellendefinitionen]] und Kommunikation zwischen [[Komponente|Komponenten]] die Vorteile überwiegt. Im Gegensatz zu monolithischen Architekturen erfordert sie zusätzlichen Aufwand für [[Schnittstelle|Schnittstellenmanagement]], [[Versionierung]] und [[Abhängigkeitsmanagement]]. Alternativen wie [[Microservices]] bieten feinere Granularität, sind jedoch mit höherer Netzwerkkomplexität, [[Latenz|Latenzen]] und [[Verteilung|Verteilungsproblemen]] verbunden. Bei [[Echtzeitsystem|Echtzeitsystemen]] mit strengen [[Performance|Performance-Anforderungen]] können [[Komponente|Komponentengrenzen]] zu unvorhergesehenen Verzögerungen führen, da die Kommunikation über [[Schnittstelle|Schnittstellen]] zusätzliche [[Latenz|Latenz]] verursacht. Das [[Komponentenmodell]] ist zudem weniger geeignet für [[System|Systeme]] mit stark dynamischen oder verteilten Interaktionen, sofern keine zusätzliche [[Middleware]] oder spezifische [[Kommunikationsprotokoll|Protokolle]] eingesetzt werden. In solchen Fällen können [[Event-gesteuertes_System|Event-gesteuerte Architekturen]] oder [[Service-orientierte_Architektur|service-orientierte Ansätze]] besser geeignet sein.
- **Beispiel / Code:** ```java
// Beispiel einer Komponente mit klarer Schnittstelle in Java (Zahlungsdienst)
public interface Zahlungsdienst {
    boolean autorisiereZahlung(double betrag, String konto);
    void storniereZahlung(String transaktionsId);
}

// Implementierung der Komponente (PayPal)
public class PayPalZahlungsdienst implements Zahlungsdienst {
    @Override
    public boolean autorisiereZahlung(double betrag, String konto) {
        // Logik zur Autorisierung über PayPal
        return true;
    }
    
    @Override
    public void storniereZahlung(String transaktionsId) {
        // Logik zum Stornieren
    }
}

// Beispiel einer weiteren Komponente (Mitgliedverwaltung)
public interface MitgliedVerwaltung {
    void mitgliedHinzufuegen(Mitglied mitglied);
    void mitgliedEntfernen(String mitgliedId);
    void mitgliedAktualisieren(Mitglied mitglied);
    Mitglied mitgliedSuchen(String mitgliedId);
}

// Implementierung der Mitgliedverwaltung
public class MitgliedVerwaltungKomponente implements MitgliedVerwaltung {
    private List<Mitglied> mitglieder = new ArrayList<>();

    @Override
    public void mitgliedHinzufuegen(Mitglied mitglied) {
        mitglieder.add(mitglied);
    }

    @Override
    public void mitgliedEntfernen(String mitgliedId) {
        mitglieder.removeIf(m -> m.getId().equals(mitgliedId));
    }

    @Override
    public void mitgliedAktualisieren(Mitglied mitglied) {
        // Logik zum Aktualisieren eines Mitglieds
    }

    @Override
    public Mitglied mitgliedSuchen(String mitgliedId) {
        return mitglieder.stream()
                .filter(m -> m.getId().equals(mitgliedId))
                .findFirst()
                .orElse(null);
    }
}

// Nutzung der Komponenten im System
public class Bestellverwaltung {
    private Zahlungsdienst zahlungsdienst;
    private MitgliedVerwaltung mitgliedVerwaltung;
    
    public Bestellverwaltung(Zahlungsdienst zahlungsdienst, MitgliedVerwaltung mitgliedVerwaltung) {
        this.zahlungsdienst = zahlungsdienst;
        this.mitgliedVerwaltung = mitgliedVerwaltung;
    }
    
    public void bezahlen(double betrag, String konto, String mitgliedId) {
        Mitglied mitglied = mitgliedVerwaltung.mitgliedSuchen(mitgliedId);
        if (mitglied != null && zahlungsdienst.autorisiereZahlung(betrag, konto)) {
            System.out.println("Zahlung erfolgreich!");
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 6b
- **Vorgänger / Parent:** [[Architekturentwurf]]
- **Folgezettel / Unterzettel:**
  - [[Modul]]
  - [[Subsystem]]
  - [[Komponente]]
- **Querverweise:**
  - [[Software-Architektur]]
  - [[Design-Pattern]]
