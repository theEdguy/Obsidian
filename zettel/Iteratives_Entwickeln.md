---
id: 22818fe0-02a5-4d16-a4c2-2e5147617cf2
title: "Iteratives_Entwickeln"
date: 2026-05-31
tags:
  - software_engineering
  - agile_methoden
  - vorgehensmodelle
  - uml
  - testen
  - entwurfsmuster
  - draft
source: "Klausur_Referenz"
---

# [[Iteratives_Entwickeln]]

- **Kernkonzept:** Iteratives_Entwickeln ist ein [[Vorgehensmodell]] in der Softwareentwicklung, bei dem ein System in wiederholten Zyklen (Iterationen) entwickelt wird. Jede Iteration umfasst die Phasen [[Anforderungsanalyse]], [[Systemdesign]], [[Implementierung]] und [[Testen]], wobei das Ergebnis einer Iteration ein ausführbares, aber unvollständiges Produkt ist. Durch schrittweise Verfeinerung und Feedback wird das System kontinuierlich verbessert, bis es die gewünschten [[Qualitätsmerkmale]] erfüllt. Im Gegensatz zu [[Wasserfallmodell]]en ermöglicht dieses Vorgehen frühzeitige Anpassungen an sich ändernde Anforderungen oder Erkenntnisse.
- **Nutzen & Zweck:** Iteratives_Entwickeln dient der Risikominimierung und Flexibilität in komplexen Projekten. Es ermöglicht:
- Frühzeitige Lieferung funktionsfähiger Teilergebnisse (z. B. für [[Prototyping]] oder Nutzerfeedback).
- Kontinuierliche Validierung von [[Anforderungen]] und [[Designentscheidungen]] durch regelmäßige Tests (z. B. [[Unit_Test]]s, [[Integrationstest]]s).
- Anpassung an geänderte Rahmenbedingungen (z. B. Marktbedürfnisse, technische Einschränkungen).
- Bessere Zusammenarbeit im Team durch klare, zeitlich begrenzte Ziele (vgl. [[Scrum]] oder [[Extreme_Programming]]).

Typische Anwendungsfälle sind agile Projekte, bei denen Unsicherheit über Anforderungen oder Technologien besteht.
- **Abgrenzung & Grenzen:** Iteratives_Entwickeln grenzt sich ab von:
- **[[Wasserfallmodell]]**: Lineare, sequentielle Phasen ohne Rücksprünge.
- **[[Inkrementelle_Entwicklung]]**: Hier werden Teilfunktionen *einmalig* hinzugefügt, während Iterationen *mehrfach* durchlaufen werden.
- **[[Chaotische_Entwicklung]]**: Fehlende Struktur oder Dokumentation, was zu technischen Schulden führt.

Stolpersteine:
- **Überlappende Iterationen**: Unklare Abgrenzung von Zielen kann zu Scope-Creep führen.
- **Dokumentationsaufwand**: Modelle und Code müssen nach jeder Iteration aktualisiert werden (vgl. [[UML]]-Diagramme wie [[Klassendiagramm]] oder [[Sequenzdiagramm]]).
- **Testlast**: Jede Iteration erfordert umfassende Tests, was bei unzureichender [[Testautomatisierung]] zeitintensiv wird.
- **Teamkoordination**: Erfordert disziplinierte [[Versionsverwaltung]] (z. B. Git) und klare [[Schnittstellen]] zwischen Modulen.
- **Beispiel / Code:** {'beschreibung': 'Ablauf einer Iteration in einem agilen Projekt (vereinfacht als UML-Sequenzdiagramm in Mermaid-Syntax):', 'uml': '```mermaid\nsequenceDiagram\n    participant ProductOwner as Product Owner\n    participant Team as Entwicklungsteam\n    participant System as System\n\n    ProductOwner->>Team: Anforderungen priorisieren (Backlog)\n    Team->>Team: Analyse & Design (z. B. [[Klassendiagramm]])\n    Team->>System: Implementierung (z. B. neue [[Schnittstelle]])\n    System->>Team: Code-Review & [[Unit_Test]]s\n    Team->>ProductOwner: Demo (Teilergebnis)\n    ProductOwner->>Team: Feedback für nächste Iteration\n```', 'code': {'sprache': 'Java', 'beispiel': '// Beispiel: Iterative Implementierung einer Job-Verarbeitung (vgl. Klausuraufgabe)\npublic class JobIterator implements Iterator<Job> {\n    private List<Job> jobs;\n    private int currentIndex = 0;\n\n    public JobIterator(List<Job> jobs) {\n        this.jobs = new ArrayList<>(jobs); // Kopie zur Isolation\n    }\n\n    @Override\n    public boolean hasNext() {\n        return currentIndex < jobs.size();\n    }\n\n    @Override\n    public Job next() {\n        if (!hasNext()) {\n            throw new NoSuchElementException("Keine weiteren Jobs");\n        }\n        return jobs.get(currentIndex++);\n    }\n}\n// Nutzung in einer Iteration:\nList<Job> backlog = new ArrayList<>();\nbacklog.add(new Job("Analyse"));\nbacklog.add(new Job("Design"));\nbacklog.add(new Job("Implementierung"));\n\nIterator<Job> iterator = new JobIterator(backlog);\nwhile (iterator.hasNext()) {\n    Job currentJob = iterator.next();\n    currentJob.execute(); // Simuliert eine Iteration\n}'}}
