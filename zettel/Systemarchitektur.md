---
id: bd72351c-2767-4fdf-a997-ce6c5be98d57
title: "Systemarchitektur"
date: 2026-06-23
tags:
  - software_engineering
  - architektur
  - design
  - draft
source: "software_engineering_kapitel_10"
---

# [[Systemarchitektur]]

- **Kernkonzept:** Die [[Systemarchitektur]] beschreibt die strukturierte und strategische Gestaltung der grundlegenden [[Komponente|Komponenten]], [[Konnektor|Konnektoren]], [[Modul|Module]] und deren [[Beziehung|Beziehungen]] innerhalb eines [[Softwaresystem|Softwaresystems]], um dessen [[Funktionalität]], [[Skalierbarkeit]], [[Wartbarkeit]] und [[Erweiterbarkeit]] sicherzustellen. Sie legt die technischen und konzeptionellen [[Rahmenbedingung|Rahmenbedingungen]] für die [[Implementierung]] fest und dient als Fundament für die Integration aller Systembestandteile, wobei sie sowohl die statische Struktur als auch dynamische [[Interaktion|Interaktionen]] zwischen den [[Teilsystem|Teilsystemen]] berücksichtigt. Darüber hinaus bezeichnet sie die übergeordnete Planung und Organisation der Zerlegung in [[Teilsystem|Teilsysteme]], [[Schicht|Schichten]] und deren [[Interaktion|Interaktionen]], um eine stabile, wartbare und skalierbare Grundlage für die [[Implementierung]] zu schaffen.
- **Nutzen & Zweck:** Die [[Systemarchitektur]] löst das zentrale Problem der [[Komplexität]] in der [[Softwareentwicklung]], indem sie frühzeitig eine klare und nachvollziehbare Struktur vorgibt. Sie ermöglicht die [[Trennung_von_Verantwortlichkeiten|Trennung von Verantwortlichkeiten]], fördert die [[Wiederverwendbarkeit]] von [[Komponente|Komponenten]] und erleichtert die Kommunikation zwischen [[Stakeholder|Stakeholdern]] wie [[Entwickler|Entwicklern]], [[Projektmanager|Projektmanagern]] und [[Kunde|Kunden]]. Durch die Definition von [[Schnittstelle|Schnittstellen]], [[Datenfluss|Datenflüssen]] und [[Architekturprinzip|Architekturprinzipien]] schafft sie eine stabile Grundlage für die schrittweise Verfeinerung und Anpassung des Systems in späteren [[Iteration|Iterationen]]. Zudem unterstützt sie die [[Risikominimierung]] durch frühzeitige Identifikation von [[Abhängigkeit|Abhängigkeiten]] und potenziellen [[Engpass|Engpässen]], während sie nicht-funktionale Anforderungen wie [[Performance]], [[Sicherheit]], [[Verfügbarkeit]] und [[Skalierbarkeit]] adressiert. Ohne eine durchdachte [[Systemarchitektur]] entstehen oft monolithische, schwer wartbare Systeme mit hohen [[Technische_Schulden|technischen Schulden]], die langfristig zu [[Inkonsistenz|Inkonsistenzen]] und [[Wartungsproblem|Wartungsproblemen]] führen. Sie ermöglicht eine effiziente [[Arbeitsteilung]] im Team, reduziert [[Redundanz|Redundanzen]] und stellt sicher, dass das System langfristig anpassbar und erweiterbar bleibt. Zudem dient sie als Kommunikationsgrundlage zwischen [[Stakeholder|Stakeholdern]], um gemeinsame Ziele und technische Entscheidungen transparent zu machen.
- **Abgrenzung & Grenzen:** Die [[Systemarchitektur]] sollte nicht mit detaillierten [[Design|Designentscheidungen]] oder [[Implementierung|Implementierungsdetails]] verwechselt werden, da sie sich auf abstraktere Ebenen konzentriert und lediglich die grobe Struktur und [[Rahmenbedingung|Rahmenbedingungen]] des Systems definiert. Sie ist ungeeignet für kleine, kurzlebige [[Projekt|Projekte]], bei denen der Overhead einer formalen Architektur den Nutzen übersteigt – hier können Alternativen wie [[Ad-hoc-Entwicklung]] oder [[Prototyping]] sinnvoller sein, bergen jedoch langfristig das Risiko von [[Technische_Schulden|technischen Schulden]] und [[Inkonsistenz|Inkonsistenzen]]. Zudem ersetzt die [[Systemarchitektur]] keine [[Agile_Entwicklung|agilen Prozesse]], sondern ergänzt diese durch strukturelle Vorgaben, die iterativ angepasst werden müssen, sobald neue Anforderungen oder technische [[Herausforderung|Herausforderungen]] auftreten. Eine zu frühe oder zu detaillierte Ausarbeitung der [[Systemarchitektur]] in frühen [[Projektphase|Projektphasen]] kann kontraproduktiv sein, da sich [[Anforderung|Anforderungen]] und [[Rahmenbedingung|Rahmenbedingungen]] ändern können. Im Gegensatz zur [[Datenmodellierung]] oder [[Algorithmus|Algorithmenentwicklung]] liegt der Fokus der [[Systemarchitektur]] auf der Systemebene und nicht auf der konkreten Umsetzung von [[Datenstruktur|Datenstrukturen]] oder [[Berechnungsvorschrift|Berechnungsvorschriften]]. Starre Architekturen ohne iterative Anpassung sind zudem ungeeignet für [[Agile_Entwicklung|agile Projekte]], da sie Flexibilität und schnelle Reaktionen auf Veränderungen behindern.
- **Beispiel / Code:** ```java
// Beispiel für eine Schichtenarchitektur ([[Layered_Architecture]]) mit Trennung von Verantwortlichkeiten
// und klar definierten [[Schnittstelle|Schnittstellen]] zwischen den Schichten

// Präsentationsebene (UI) – verantwortlich für die Interaktion mit dem Nutzer
public class MitgliedView {
    private MitgliedService mitgliedService;
    
    public MitgliedView(MitgliedService mitgliedService) {
        this.mitgliedService = mitgliedService;
    }
    
    public void mitgliedAnlegen(String name, String abteilung) {
        mitgliedService.neuesMitgliedErstellen(name, abteilung);
    }
}

// Business-Logik (Service-Schicht) – implementiert Geschäftsregeln und Koordination
public class MitgliedService {
    private MitgliedRepository mitgliedRepository;
    private AbteilungService abteilungService;
    private BenachrichtigungsService benachrichtigungsService;
    
    public MitgliedService(MitgliedRepository mitgliedRepository, 
                          AbteilungService abteilungService, 
                          BenachrichtigungsService benachrichtigungsService) {
        this.mitgliedRepository = mitgliedRepository;
        this.abteilungService = abteilungService;
        this.benachrichtigungsService = benachrichtigungsService;
    }
    
    public void neuesMitgliedErstellen(String name, String abteilungId) {
        Mitglied mitglied = new Mitglied(name);
        mitgliedRepository.save(mitglied);
        abteilungService.mitgliedHinzufuegen(mitglied, abteilungId);
        benachrichtigungsService.sendeWillkommensnachricht(mitglied);
    }
    
    public void abteilungVerlassen(String mitgliedId, String abteilungId) {
        Mitglied mitglied = mitgliedRepository.findById(mitgliedId);
        abteilungService.entferneMitglied(mitglied, abteilungId);
        
        if (mitglied.getAbteilungen().isEmpty()) {
            mitglied.setStatus("passiv");
            mitgliedRepository.update(mitglied);
            benachrichtigungsService.sendeBenachrichtigung(mitglied);
        }
    }
}

// Datenhaltung (Repository-Schicht) – verantwortlich für Persistenz und Datenzugriff
public class MitgliedRepository {
    public Mitglied findById(String id) {
        // Logik für Datenbankzugriff oder In-Memory-Speicher
        return new Mitglied("Max Mustermann");
    }
    
    public void save(Mitglied mitglied) {
        // Persistenzlogik
    }
    
    public void update(Mitglied mitglied) {
        // Aktualisierungslogik
    }
}

// Beispiel für eine dreischichtige Architektur (vereinfacht)

// Präsentationsschicht (View)
public class MemberView {
    private MemberController controller;
    
    public void displayMember(Member member) {
        System.out.println("Mitglied: " + member.getName());
    }
}

// Logikschicht (Controller & Model)
public class MemberController {
    private MemberService memberService;
    
    public Member getMemberById(int id) {
        return memberService.findMember(id);
    }
}

public class MemberService {
    private MemberRepository repository;
    
    public Member findMember(int id) {
        return repository.findById(id);
    }
}

// Persistenzschicht (Repository)
public class MemberRepository {
    public Member findById(int id) {
        // Datenbankzugriff (z. B. via JDBC oder [[JPA]])
        return new Member(id, "Max Mustermann");
    }
}
```

// Beispiel für eine [[Microservice|Microservices-Architektur]]
// Frontend: Webanwendung ([[React]])
// Backend: [[Microservice|Microservices]] (Java/[[Spring_Boot]])
// Datenhaltung: [[PostgreSQL]]
// Kommunikation: [[REST-API]], [[Message_Queue]] ([[RabbitMQ]])

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c
- **Vorgänger / Parent:** [[Software-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Komponentenarchitektur]]
  - [[Schichtenarchitektur]]
  - [[Verteilungsarchitektur]]
  - [[Architekturentscheidungen]]
- **Querverweise:** keine
