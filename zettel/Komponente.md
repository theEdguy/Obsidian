---
id: 3d855729-02eb-47b1-8c42-dd21da7a2944
title: "Komponente"
date: 2026-06-23
tags:
  - software_engineering
  - verteilte_systeme
  - architektur
  - design
  - modularisierung
  - schnittstellen
  - konnektoren
  - modularität
  - wiederverwendung
  - mvc
  - ansicht
  - beobachtung
  - draft
source: "software_engineering_kapitel_12"
---

# [[Komponente]]

- **Kernkonzept:** Eine [[Komponente]] ist eine modulare, wiederverwendbare Einheit in der [[Systemarchitektur]], die eine dedizierte [[Funktionalität]] kapselt und über definierte [[Schnittstelle|Schnittstellen]] mit anderen [[Komponente|Komponenten]] oder [[Architekturmuster|Architekturmustern]] wie [[MVC]] interagiert. Sie operiert unabhängig von spezifischen [[Client|Clients]] und ermöglicht die strukturierte Zerlegung eines Systems in überschaubare, kooperierende Teile, insbesondere in [[Verteiltes_System|verteilten Systemen]] oder [[Geschichtete_Architektur|geschichteten Architekturen]]. Spezialisierte [[Komponente|Komponenten]], wie die [[View-Komponente]] im [[MVC]], trennen Verantwortlichkeiten wie Darstellung, Logik und Datenhaltung.
- **Nutzen & Zweck:** [[Komponente|Komponenten]] fördern die [[Modularität]], [[Wiederverwendbarkeit]] und [[Wartbarkeit]] von Systemen, indem sie komplexe Strukturen in beherrschbare Teile zerlegen und die [[Trennung_von_Verantwortlichkeiten|Trennung von Verantwortlichkeiten]] ermöglichen. Sie lösen Probleme der [[Skalierbarkeit]] und [[Komplexität]] in [[Verteiltes_System|verteilten Architekturen]], insbesondere durch klare [[Schnittstelle|Schnittstellen]] und [[Lose_Kopplung|lose Kopplung]]. Durch ihre definierten [[Schnittstelle|Schnittstellen]] wird die Zusammenarbeit zwischen [[Entwicklungsteam|Entwicklungsteams]] verbessert, Redundanzen reduziert und die Austauschbarkeit einzelner Systemteile vereinfacht. [[Komponente|Komponenten]] erleichtern zudem die parallele Entwicklung und Integration in verschiedene Systeme. Im Kontext von [[MVC]] ermöglicht die [[View-Komponente]] eine strikte Trennung zwischen Darstellung und Geschäftslogik, was die [[Kohäsion]] erhöht und die [[Wiederverwendbarkeit]] der [[Komponente|Komponenten]] steigert. Durch die Anwendung des [[Observer_Pattern|Observer-Patterns]] wird sichergestellt, dass die Darstellung konsistent mit den zugrundeliegenden Daten bleibt, ohne dass die [[View-Komponente]] selbst die Daten manipuliert.
- **Abgrenzung & Grenzen:** [[Komponente|Komponenten]] sind kein Ersatz für [[Klasse|Klassen]] oder [[Funktion|Funktionen]] auf Code-Ebene, da sie auf der [[Architektur]]-Ebene operieren und größer dimensioniert sind. Im Gegensatz zu [[Modul|Modulen]] besitzen sie oft explizitere [[Schnittstelle|Schnittstellen]] und sind stärker auf [[Wiederverwendbarkeit]] und Unabhängigkeit von spezifischen [[Client|Clients]] ausgelegt. Sie sind ungeeignet für zu kleine oder einfache Systeme, da der Overhead der [[Schnittstelle|Schnittstellen]]-Definition den Nutzen übersteigt. Während [[Objekt|Objekte]] feingranular und [[Service|Services]] autonom sind, sind [[Komponente|Komponenten]] oft auf spezifische [[Architekturstil|Architekturstile]] wie [[Geschichtete_Architektur|geschichtete]] oder [[Objektbasierte_Architektur|objektbasierte Systeme]] zugeschnitten. Zudem sind sie weniger geeignet für Systeme mit extrem hohen [[Performance]]-Anforderungen, bei denen feingranulare Kontrolle über jeden Systemteil notwendig ist. Monolithische Architekturen bieten hier geringere [[Komplexität]], erfordern jedoch zentrale Kontrolle und enge [[Kopplung]]. Die [[View-Komponente]] im [[MVC]] sollte nicht genutzt werden, wenn keine Benutzerinteraktion oder Darstellung erforderlich ist, z. B. in rein backend-getriebenen Systemen oder Batch-Prozessen. Bei sehr einfachen Anwendungen kann der Overhead des [[MVC]]-Musters unnötig sein, und direkte Datenbindungen oder monolithische Architekturen sind möglicherweise vorzuziehen.
- **Beispiel / Code:** ```java
// Beispiel einer generischen Komponente in Java (Spring Boot) mit definierter Schnittstelle
@Component
public class BestellService {
    public Bestellung erstelleBestellung(Warenkorb warenkorb) {
        // Logik zur Bestellungserstellung
    }
}

// Beispiel einer Komponente mit expliziter Schnittstelle und Implementierung
public interface MitgliedVerwaltung {
    void hinzufuegen(Mitglied mitglied);
    Mitglied suchen(String mitgliedsId);
    void aktualisieren(Mitglied mitglied);
    void loeschen(String mitgliedsId);
}

public class MitgliedVerwaltungImpl implements MitgliedVerwaltung {
    @Override
    public void hinzufuegen(Mitglied mitglied) {
        // Logik zum Hinzufügen eines Mitglieds
    }
    
    @Override
    public Mitglied suchen(String mitgliedsId) {
        // Logik zum Suchen eines Mitglieds
        return null;
    }
    
    @Override
    public void aktualisieren(Mitglied mitglied) {
        // Logik zum Aktualisieren eines Mitglieds
    }
    
    @Override
    public void loeschen(String mitgliedsId) {
        // Logik zum Löschen eines Mitglieds
    }
}

// Beispiel einer View-Komponente im MVC-Muster (Observer-Pattern)
public class MemberView implements Observer {
    private MemberModel model;
    
    public MemberView(MemberModel model) {
        this.model = model;
        this.model.attach(this); // View als Observer registrieren
    }
    
    @Override
    public void update(State state) {
        if (state == State.S.ManageMembers) {
            displayMembers(model.getMembers()); // Darstellung aktualisieren
        }
    }
    
    private void displayMembers(List<Member> members) {
        System.out.println("Aktuelle Mitglieder:");
        members.forEach(member -> System.out.println(member.getName()));
    }
}
```

Geschichtete Architektur (Kommunikationsprotokoll):
```
// Layer N (Anwendungsschicht)
function sendRequest(data) {
  const processedData = processData(data); // Verarbeitungsebene
  const networkPacket = encodePacket(processedData); // Datenebene
  return networkPacket;
}

// Layer N-1 (Transportschicht)
function encodePacket(data) {
  return { header: 'TCP', payload: data };
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a2
- **Vorgänger / Parent:** [[MVC-Architektur]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Observer-Pattern]]
  - [[MVC-Architektur]]
