---
id: b7890da9-3c1d-4276-b7b3-d9c96c47e94a
title: "Architekturstil"
date: 2026-06-23
tags:
  - software_engineering
  - architekturstil
  - design
  - draft
source: "software_engineering_kapitel_07"
---

# [[Architekturstil]]

- **Kernkonzept:** Ein Architekturstil definiert ein grundlegendes Muster oder eine Struktur für den Aufbau von Softwaresystemen, das wiederkehrende Prinzipien, Komponenten und deren Interaktionen festlegt. Er dient als Rahmenwerk, um die Organisation und Kommunikation von Systemteilen zu standardisieren und die Qualitätseigenschaften wie Skalierbarkeit, Wartbarkeit oder Performance zu steuern.
- **Nutzen & Zweck:** Architekturstile existieren, um die Komplexität von Softwaresystemen beherrschbar zu machen, indem sie bewährte Lösungsmuster für häufig auftretende Designprobleme bereitstellen. Sie lösen das Problem der Willkürlichkeit im Systemdesign, indem sie klare Richtlinien für die Strukturierung, Modularisierung und Integration von Komponenten vorgeben. Dadurch ermöglichen sie eine konsistente Entwicklung, vereinfachen die Kommunikation im Team und reduzieren Risiken durch vorhersehbare Systemeigenschaften. Zudem fördern sie die Wiederverwendbarkeit von Designentscheidungen und erleichtern die Anpassung an sich ändernde Anforderungen.
- **Abgrenzung & Grenzen:** Ein Architekturstil sollte nicht genutzt werden, wenn die spezifischen Anforderungen des Systems stark von den vorgegebenen Mustern abweichen oder wenn der Stil unnötige Komplexität einführt, ohne einen konkreten Nutzen zu bieten. Alternativen wie *ad-hoc-Designs* oder hybride Ansätze können sinnvoller sein, wenn Flexibilität Vorrang vor Standardisierung hat. Architekturstile wie *Schichtenarchitektur* oder *Microservices* unterscheiden sich beispielsweise in ihrer Eignung für monolithische vs. verteilte Systeme: Während Schichtenarchitekturen klare Abhängigkeiten erzwingen, bieten Microservices höhere Skalierbarkeit, aber mit erhöhtem Kommunikationsaufwand. Zudem sind Architekturstile oft schwer zu ändern, sobald sie implementiert sind, und eignen sich daher weniger für explorative oder kurzlebige Projekte.
- **Beispiel / Code:** ```java
// Beispiel: Schichtenarchitektur (Layered Architecture) mit klarer Trennung von Verantwortlichkeiten

// Präsentationsschicht (UI)
public class MitgliedView {
    private MitgliedService mitgliedService;
    
    public void anzeigenMitglieder() {
        List<Mitglied> mitglieder = mitgliedService.ladeAlleMitglieder();
        // Darstellung der Daten
    }
}

// Geschäftslogikschicht (Service)
public class MitgliedService {
    private MitgliedRepository mitgliedRepository;
    
    public List<Mitglied> ladeAlleMitglieder() {
        return mitgliedRepository.findAll();
    }
}

// Datenzugriffsschicht (Repository)
public class MitgliedRepository {
    public List<Mitglied> findAll() {
        // Datenbankabfrage
        return new ArrayList<>();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4b
- **Vorgänger / Parent:** [[Systemarchitektur]]
- **Folgezettel / Unterzettel:**
  - [[Monolithische_Architektur]]
  - [[Mikroservices]]
  - [[Client-Server]]
  - [[Schichtenarchitektur]]
- **Querverweise:**
  - [[Systemarchitektur]]
  - [[Software-Architektur]]
