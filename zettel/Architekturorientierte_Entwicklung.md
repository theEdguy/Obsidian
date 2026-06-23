---
id: d3b58b21-c0bb-4924-9e01-920015680710
title: "Architekturorientierte Entwicklung"
date: 2026-06-23
tags:
  - software_engineering
  - architektur
  - draft
source: "software_engineering_kapitel_03"
---

# [[Architekturorientierte Entwicklung]]

- **Kernkonzept:** Architekturorientierte Entwicklung ist ein Ansatz im Software-Engineering, bei dem die Systemarchitektur als zentraler Bauplan für die Organisation, Struktur und Integration von Komponenten und Subsystemen dient. Sie bildet die Grundlage für eine durchgängige, agile und iterative Entwicklung, die funktionale und nicht-funktionale Anforderungen berücksichtigt.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem unkoordinierter oder inkonsistenter Softwareentwicklung, indem es eine klare, ganzheitliche Struktur vorgibt. Es ermöglicht die frühzeitige Identifikation von Abhängigkeiten, fördert die Wiederverwendbarkeit von Komponenten und erleichtert die Integration von Teilprodukten zu einem einheitlichen System. Zudem verbessert es die Kommunikation zwischen Entwicklern, Architekten und Stakeholdern, da die Architektur als gemeinsame Referenz dient.
- **Abgrenzung & Grenzen:** Architekturorientierte Entwicklung sollte nicht in Projekten mit extrem dynamischen oder unklaren Anforderungen eingesetzt werden, da der initiale Aufwand für die Architekturplanung hoch ist. Alternativen wie chaotische oder rein codegetriebene Ansätze (z. B. 'Code-first') können in frühen Prototypen oder explorativen Phasen sinnvoller sein. Zudem eignet sich der Ansatz weniger für kleine Projekte mit geringer Komplexität, da der Overhead der Architekturdefinition den Nutzen übersteigen kann.
- **Beispiel / Code:** ```java
// Beispiel: Grobe Architekturdefinition mit Komponenten und Schnittstellen
public interface MitgliedRepository {
    Mitglied findById(String id);
    void save(Mitglied mitglied);
}

public class MitgliedService {
    private final MitgliedRepository repository;
    
    public MitgliedService(MitgliedRepository repository) {
        this.repository = repository; // Dependency Injection für lose Kopplung
    }
    
    public int berechneLeistungsprognose(String mitgliedId, Date datum) {
        Mitglied mitglied = repository.findById(mitgliedId);
        return mitglied.leistungsprognose(datum);
    }
}
```

// Die Architektur trennt klar zwischen:
// - Domänenlogik (MitgliedService)
// - Datenzugriff (MitgliedRepository)
// - Geschäftsobjekten (Mitglied-Klasse, nicht gezeigt)
// und ermöglicht so eine flexible Integration und Testbarkeit.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c
- **Vorgänger / Parent:** [[Objektorientierte_Softwareentwicklung]]
- **Folgezettel / Unterzettel:**
  - [[Softwarearchitektur]]
  - [[Komponentenmodellierung]]
- **Querverweise:** keine
