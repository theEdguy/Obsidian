---
id: e4400ff5-0199-4e86-947b-875391ae7c8f
title: "Drei-Schichtenmodell"
date: 2026-06-23
tags:
  - software_engineering
  - architektur
  - schichten
  - draft
source: "software_engineering_kapitel_10"
---

# [[Drei-Schichtenmodell]]

- **Kernkonzept:** Das Drei-Schichtenmodell ist ein Architekturkonzept in der Softwareentwicklung, das eine Anwendung in drei klar getrennte Schichten unterteilt: Präsentationsschicht (Nutzerinteraktion), Logikschicht (Geschäftslogik) und Datenzugriffsschicht (Persistenz und externe Systeme). Jede Schicht hat eine spezifische Verantwortung und kommuniziert nur mit der direkt darunterliegenden Schicht.
- **Nutzen & Zweck:** Dieses Modell existiert, um die Komplexität von Softwareanwendungen zu reduzieren, indem es eine klare Trennung der Verantwortlichkeiten schafft. Es ermöglicht eine bessere Wartbarkeit, Skalierbarkeit und Wiederverwendbarkeit von Code, da Änderungen in einer Schicht keine direkten Auswirkungen auf die anderen Schichten haben. Zudem erleichtert es die parallele Entwicklung durch verschiedene Teams und die Integration externer Systeme.
- **Abgrenzung & Grenzen:** Das Drei-Schichtenmodell sollte nicht genutzt werden, wenn die Anwendung sehr einfach ist und keine komplexe Logik oder Datenhaltung erfordert, da der Overhead der Schichtenbildung unnötig wäre. Es unterscheidet sich von monolithischen Architekturen durch die strikte Trennung der Schichten, während bei monolithischen Ansätzen alle Komponenten eng miteinander verwoben sind. Alternativen wie Microservices oder Event-Driven-Architekturen bieten mehr Flexibilität für verteilte Systeme, sind jedoch komplexer in der Umsetzung.
- **Beispiel / Code:** ```java
// Beispiel für eine einfache Implementierung des Drei-Schichtenmodells

// Präsentationsschicht (GUI)
public class MitgliedView {
    private MitgliedController controller;
    
    public void zeigeMitgliederAn(List<Mitglied> mitglieder) {
        // Logik zur Darstellung der Mitglieder
    }
    
    public void onMitgliedHinzufuegen(String name) {
        controller.mitgliedHinzufuegen(name);
    }
}

// Logikschicht (Geschäftslogik)
public class MitgliedController {
    private MitgliedService mitgliedService;
    
    public void mitgliedHinzufuegen(String name) {
        Mitglied mitglied = new Mitglied(name);
        mitgliedService.speichern(mitglied);
    }
}

// Datenzugriffsschicht (Persistenz)
public class MitgliedService {
    private MitgliedRepository repository;
    
    public void speichern(Mitglied mitglied) {
        repository.save(mitglied);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c2a
- **Vorgänger / Parent:** [[Schichtenarchitektur]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
