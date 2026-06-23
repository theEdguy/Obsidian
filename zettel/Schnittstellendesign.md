---
id: 118b19a8-081f-4780-8803-1f3c700e26fd
title: "Schnittstellendesign"
date: 2026-06-23
tags:
  - software_engineering
  - schnittstellen
  - design
  - abstraktion
  - draft
source: "software_engineering_kapitel_14"
---

# [[Schnittstellendesign]]

- **Kernkonzept:** Schnittstellendesign bezeichnet die systematische Gestaltung von [[Schnittstelle|Schnittstellen]] zwischen [[Softwarekomponente|Softwarekomponenten]], [[Modul|Modulen]] oder [[System|Systemen]], um eine klare, stabile und wartbare [[Kommunikation]] zu ermöglichen. Es definiert das Verhalten und die [[Vertrag (Programmierung)|Verträge]] für die Interaktion, ohne die interne [[Implementierung]] offenzulegen, und trennt somit [[Spezifikation]] von [[Realisierung]], um [[Flexibilität]] und [[Austauschbarkeit]] zu gewährleisten.
- **Nutzen & Zweck:** Schnittstellendesign löst das Problem der [[Kopplung]] und Abhängigkeit zwischen [[Softwarekomponente|Komponenten]], indem es eine klare Trennung von Verantwortlichkeiten schafft und explizite [[Vertrag (Programmierung)|Verträge]] für die Interaktion definiert. Dadurch ermöglicht es die unabhängige Entwicklung, [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Wiederverwendbarkeit]] von [[Modul|Modulen]], reduziert Fehleranfälligkeit durch definierte [[Vor- und Nachbedingung|Vor- und Nachbedingungen]] sowie [[Ausnahmebehandlung|Ausnahmen]] und fördert die [[Testbarkeit]] durch isolierte [[Schnittstelle|Schnittstellen]]. Es verbessert die Zusammenarbeit in [[Team|Teams]] durch ein gemeinsames Verständnis der [[Schnittstelle|Schnittstellen]] und erleichtert die Integration externer [[System|Systeme]]. Besonders in [[Verteilte Systeme|verteilten Systemen]] oder bei der Anwendung von [[Entwurfsmuster|Mustern]] wie [[Facade]], [[Adapter]] oder [[Strategy]] ist ein durchdachtes Schnittstellendesign essenziell für [[Lose Kopplung|lose Kopplung]] und [[Hohe Kohäsion|hohe Kohäsion]]. Zudem ermöglicht es die einfache Austauschbarkeit von [[Implementierung|Implementierungen]], ohne den aufrufenden Code zu ändern, was die [[Flexibilität]] und [[Skalierbarkeit]] von Softwaresystemen erhöht.
- **Abgrenzung & Grenzen:** Schnittstellendesign sollte nicht genutzt werden, wenn die [[Kommunikation]] zwischen [[Softwarekomponente|Komponenten]] trivial, einmalig oder extrem einfach ist, da der Overhead der [[Schnittstelle|Schnittstellendefinition]] den Nutzen übersteigt. Es unterscheidet sich von [[Implementierung|Implementierungsdetails]], die interne Logik beschreiben, und von [[Kommunikationsprotokoll|Protokollen]], die sich auf niedrigere Ebenen (z. B. Netzwerkprotokolle) konzentrieren. Alternativen wie direkte [[Funktionsaufruf|Funktionsaufrufe]], monolithische [[Architektur]] oder enge [[Kopplung]] können in kleinen Projekten oder Performance-kritischen Szenarien effizienter sein, bieten jedoch keine langfristige [[Wartbarkeit]] oder [[Flexibilität]]. Zudem ist Schnittstellendesign ungeeignet, wenn die Anforderungen an die Interaktion zwischen [[Softwarekomponente|Komponenten]] noch unklar oder stark im Fluss sind, da stabile [[Vertrag (Programmierung)|Verträge]] eine gewisse Stabilität der Anforderungen voraussetzen. In solchen Fällen können agile Ansätze wie [[Refactoring]] oder [[Prototyping]] sinnvoller sein, bevor eine feste [[Schnittstelle]] definiert wird. Häufige Änderungen an [[Schnittstelle|Schnittstellen]] können zu [[Breaking Change|Breaking Changes]] führen, die die [[Kompatibilität]] beeinträchtigen.
- **Beispiel / Code:** ```java
/**
 * Schnittstelle für die Verwaltung von Vereinsmitgliedern.
 * Definiert die Operationen, die ein Mitglied im System ausführen kann,
 * inklusive Vorbedingungen, Nachbedingungen und Ausnahmen.
 */
public interface MitgliedService {
    /**
     * Fügt ein neues Mitglied hinzu.
     * @param mitglied Das hinzuzufügende Mitglied
     * @return Die ID des neuen Mitglieds
     * @throws IllegalArgumentException wenn das Mitglied ungültige Daten enthält
     * @throws SecurityException wenn der Aufrufer nicht berechtigt ist
     */
    String mitgliedHinzufuegen(Mitglied mitglied);

    /**
     * Aktualisiert die Daten eines bestehenden Mitglieds.
     * @param mitgliedId Die ID des zu aktualisierenden Mitglieds
     * @param neueDaten Die aktualisierten Daten
     * @throws MitgliedNichtGefundenException wenn kein Mitglied mit der ID existiert
     * @throws IllegalArgumentException wenn die neuen Daten ungültig sind
     */
    void mitgliedAktualisieren(String mitgliedId, Mitglied neueDaten);

    /**
     * Entfernt ein Mitglied aus dem System.
     * @param mitgliedId Die ID des zu entfernenden Mitglieds
     * @throws MitgliedNichtGefundenException wenn kein Mitglied mit der ID existiert
     */
    void mitgliedEntfernen(String mitgliedId);

    /**
     * Entfernt ein Mitglied aus einer Abteilung.
     * @param mitgliedId Eindeutige ID des Mitglieds
     * @param abteilungId Eindeutige ID der Abteilung
     * @throws IllegalArgumentException wenn das Mitglied nicht in der Abteilung ist
     * @throws SecurityException wenn der Aufrufer nicht berechtigt ist
     */
    void abteilungVerlassen(String mitgliedId, String abteilungId);

    /**
     * Ändert den Status eines Mitglieds (z. B. aktiv/passiv).
     * @param mitgliedId Eindeutige ID des Mitglieds
     * @param neuerStatus Neuer Status des Mitglieds
     * @throws MitgliedNichtGefundenException wenn kein Mitglied mit der ID existiert
     */
    void statusAendern(String mitgliedId, MitgliedStatus neuerStatus);
}

// Beispiel für die Trennung von Schnittstelle und Implementierung
/**
 * Definition einer Schnittstelle für Adresslabel.
 */
public interface AddressLabel {
    /**
     * Formatiert eine Adresse nach länderspezifischen Vorgaben.
     * @param name Name des Empfängers
     * @param street Straße und Hausnummer
     * @param city Stadt
     * @param country Land
     * @return Formatierte Adresse als String
     */
    String formatAddress(String name, String street, String city, String country);
}

/**
 * Konkrete Implementierung für deutsche Adressen.
 */
public class GermanAddressLabel implements AddressLabel {
    @Override
    public String formatAddress(String name, String street, String city, String country) {
        return name + "\n" + street + "\n" + city + "\n" + country;
    }
}

/**
 * Nutzung der Schnittstelle ohne Kenntnis der konkreten Implementierung.
 */
public class AddressBook {
    private AddressLabel addressLabel;

    public AddressBook(AddressLabel addressLabel) {
        this.addressLabel = addressLabel;
    }

    public String createLabel(String name, String street, String city, String country) {
        return addressLabel.formatAddress(name, street, city, country);
    }
}
```

**Erläuterung:**
Die Beispiele zeigen zwei Anwendungsfälle von [[Schnittstelle|Schnittstellen]]: 
1. **MitgliedService**: Definiert einen [[Vertrag (Programmierung)|Vertrag]] für ein Mitgliederverwaltungssystem mit klaren [[Operation|Operationen]], [[Parameter|Parametern]], Rückgabewerten und [[Ausnahmebehandlung|Ausnahmen]]. Dies ermöglicht [[Lose Kopplung|lose Kopplung]] zwischen der [[Schnittstelle]] und ihren [[Implementierung|Implementierungen]].
2. **AddressLabel**: Demonstriert die Trennung von [[Spezifikation]] und [[Realisierung]] durch eine [[Schnittstelle]] und eine konkrete [[Implementierung]]. Die nutzende Klasse `AddressBook` ist unabhängig von der konkreten Formatierung und kann leicht um weitere [[Implementierung|Implementierungen]] (z. B. für andere Länder) erweitert werden, ohne den Code zu ändern. Dies fördert [[Wiederverwendbarkeit]] und [[Erweiterbarkeit]].

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c
- **Vorgänger / Parent:** [[Software_Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Programmieren_gegen_Schnittstellen]]
  - [[Abstraktion_durch_Schnittstellen]]
  - [[Beispiel_Component-Interface]]
- **Querverweise:**
  - [[Design-Prinzipien]]
  - [[Polymorphie]]
