---
id: d9132abd-c6f0-4276-ae12-81c0d682ba5e
title: "Schichtenarchitektur"
date: 2026-06-23
tags:
  - software_engineering
  - schichtenarchitektur
  - architektur
  - schichten
  - draft
source: "software_engineering_kapitel_10"
---

# [[Schichtenarchitektur]]

- **Kernkonzept:** Die [[Schichtenarchitektur]] ist ein [[Architekturstil]] in der [[Softwareentwicklung]], bei dem ein System in horizontale [[Schicht|Schichten]] unterteilt wird, die jeweils spezifische [[Verantwortlichkeit|Verantwortlichkeiten]] übernehmen. Jede [[Schicht]] bietet der darüberliegenden [[Schicht]] Dienste an und nutzt die Dienste der darunterliegenden [[Schicht]], wodurch eine klare Trennung der [[Verantwortlichkeit|Verantwortlichkeiten]] und [[Lose_Kopplung|lose Kopplung]] zwischen den [[Komponente|Komponenten]] erreicht wird.
- **Nutzen & Zweck:** Die [[Schichtenarchitektur]] existiert, um die Komplexität großer [[Softwaresystem|Softwaresysteme]] beherrschbar zu machen, indem sie eine klare Trennung der [[Verantwortlichkeit|Verantwortlichkeiten]] und [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] ermöglicht. Sie löst konkrete Probleme wie schlechte [[Wartbarkeit]], fehlende [[Wiederverwendbarkeit]], unkontrollierte [[Abhängigkeit|Abhängigkeiten]] und mangelnde [[Skalierbarkeit]], indem sie die [[Modularität]], [[Testbarkeit]] und [[Erweiterbarkeit]] des Systems verbessert. Zudem fördert sie die parallele Arbeit in [[Team|Teams]], da [[Schicht|Schichten]] unabhängig voneinander entwickelt, getestet und ausgetauscht werden können. Durch die strikte Trennung der [[Schicht|Schichten]] wird die [[Wiederverwendbarkeit]] von [[Code]] erhöht, und Änderungen in einer [[Schicht]] haben keine direkten Auswirkungen auf andere [[Schicht|Schichten]]. Dies vereinfacht [[Refactoring]]-Maßnahmen und reduziert das Risiko von [[Seiteneffekt|Seiteneffekten]].
- **Abgrenzung & Grenzen:** Die [[Schichtenarchitektur]] sollte nicht genutzt werden, wenn das System sehr kleine Anforderungen hat oder [[Performance]]-kritisch ist, da der Overhead durch die [[Schicht|Schichten]]-Kommunikation die Effizienz beeinträchtigen kann. Sie eignet sich weniger für [[Echtzeitsystem|Echtzeitsysteme]] oder Anwendungen mit extrem niedriger Latenz, da die hierarchische Kommunikation zwischen den [[Schicht|Schichten]] zusätzliche Verzögerungen verursachen kann. Im Vergleich zu [[Monolithische_Architektur|monolithischen Architekturen]] bietet sie mehr [[Modularität]], unterscheidet sich jedoch von [[Microservices]] durch die vertikale statt horizontale Aufteilung und von [[Event-gesteuertes_System|Event-gesteuerten Systemen]] durch ihre synchrone, schichtenweise Kommunikation. Bei Systemen mit stark vernetzten [[Komponente|Komponenten]] oder komplexen [[Domänenmodell|Domänenmodellen]] können alternative [[Architekturstil|Architekturstile]] wie [[Hexagonale_Architektur]], [[CQRS]] oder [[Domain-Driven_Design]] besser geeignet sein. Eine zu starre Aufteilung in [[Schicht|Schichten]] kann zudem zu unnötiger Komplexität führen, wenn die [[Domäne]] keine klare Trennung der [[Verantwortlichkeit|Verantwortlichkeiten]] erfordert.
- **Beispiel / Code:** ```java
// Beispiel einer dreischichtigen Architektur in Java mit erweiterter Trennung der Verantwortlichkeiten

// 1. Präsentationsschicht (UI) – Verantwortlich für die Interaktion mit dem Benutzer
public class MitgliedView {
    private MitgliedController controller;
    
    public MitgliedView(MitgliedController controller) {
        this.controller = controller;
    }
    
    public void zeigeMitgliederListe(List<Mitglied> mitglieder) {
        // Logik zur Darstellung der Mitglieder in der GUI
        System.out.println("Mitgliederliste:");
        mitglieder.forEach(mitglied -> System.out.println(mitglied.getName()));
    }
    
    public void onMitgliedHinzufuegen(String name, String adresse) {
        controller.mitgliedAnlegen(name, adresse);
    }
}

// 2. Geschäftslogikschicht (Service) – Verantwortlich für die Business-Logik und Koordination
public class MitgliedController {
    private MitgliedService mitgliedService;
    
    public MitgliedController(MitgliedService mitgliedService) {
        this.mitgliedService = mitgliedService;
    }
    
    public void mitgliedAnlegen(String name, String adresse) {
        // Validierung und Vorbereitung der Daten
        if (name == null || name.isEmpty()) {
            throw new IllegalArgumentException("Name darf nicht leer sein");
        }
        mitgliedService.mitgliedSpeichern(name, adresse);
    }
}

// 3. Geschäftslogikschicht (Service) – Verantwortlich für die Domänenlogik
public class MitgliedService {
    private MitgliedRepository mitgliedRepository;
    
    public MitgliedService(MitgliedRepository mitgliedRepository) {
        this.mitgliedRepository = mitgliedRepository;
    }
    
    public void mitgliedSpeichern(String name, String adresse) {
        Mitglied mitglied = new Mitglied(name, adresse);
        // Domänenspezifische Logik, z. B. Prüfung auf Duplikate
        if (mitgliedRepository.existsByName(name)) {
            throw new IllegalStateException("Mitglied existiert bereits");
        }
        mitgliedRepository.save(mitglied);
    }
}

// 4. Datenzugriffsschicht (Repository) – Verantwortlich für die Persistenz
public class MitgliedRepository {
    public void save(Mitglied mitglied) {
        // Logik zum Speichern in der Datenbank
        System.out.println("Mitglied gespeichert: " + mitglied.getName());
    }
    
    public boolean existsByName(String name) {
        // Logik zur Prüfung auf Duplikate
        return false;
    }
}

// Domänenmodell
public class Mitglied {
    private String name;
    private String adresse;
    
    public Mitglied(String name, String adresse) {
        this.name = name;
        this.adresse = adresse;
    }
    
    public String getName() {
        return name;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c2
- **Vorgänger / Parent:** [[Systemarchitektur]]
- **Folgezettel / Unterzettel:**
  - [[Drei-Schichtenmodell]]
  - [[Präsentationsschicht]]
  - [[Logikschicht]]
  - [[Datenzugriffsschicht]]
- **Querverweise:** keine
