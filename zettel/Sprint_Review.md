---
id: ee1c6515-8e08-47c3-8a94-d0765f4209c4
title: "Sprint_Review"
date: 2026-05-31
tags:
  - software_engineering
  - scrum
  - agile_entwicklung
  - projektmanagement
  - produktentwicklung
  - feedback_schleife
  - draft
source: "Klausur_Referenz"
---

# [[Sprint_Review]]

- **Kernkonzept:** Das **Sprint_Review** ist ein zentrales Ereignis im [[Scrum]]-Framework, das am Ende jedes [[Sprint]]s stattfindet. Es dient der Präsentation der im Sprint umgesetzten [[Increment]]e (potenziell auslieferbare Produktversionen) an die [[Stakeholder]] und dem Team. Ziel ist es, Feedback zu sammeln, den Fortschritt zu bewerten und den [[Produkt_Backlog]] für zukünftige Sprints anzupassen. Im Gegensatz zur [[Sprint_Retrospektive]] liegt der Fokus nicht auf der Prozessoptimierung, sondern auf dem Produkt selbst und dessen Weiterentwicklung.
- **Nutzen & Zweck:** Das Sprint_Review erfüllt mehrere Zwecke:
- **Transparenz**: Stakeholder erhalten Einblick in den aktuellen Stand des Produkts und können Fortschritte nachvollziehen.
- **Feedback-Schleife**: Durch direkte Rückmeldungen der Stakeholder können Anforderungen präzisiert oder priorisiert werden, was die Ausrichtung des Produkts an den Bedürfnissen der Nutzer sicherstellt.
- **Anpassung des Backlogs**: Basierend auf dem Feedback wird der [[Produkt_Backlog]] aktualisiert, um neue Erkenntnisse oder geänderte Prioritäten zu berücksichtigen.
- **Motivation**: Das Team sieht die Ergebnisse seiner Arbeit und erhält Anerkennung für die geleistete Arbeit.
- **Risikominimierung**: Frühzeitige Identifikation von Abweichungen zwischen Produktvision und Umsetzung reduziert spätere Korrekturkosten.
- **Abgrenzung & Grenzen:** Abgrenzung zu anderen Scrum-Ereignissen:
- **Nicht zu verwechseln mit der [[Sprint_Retrospektive]]**: Während das Sprint_Review das *Produkt* evaluiert, analysiert die Retrospektive den *Prozess* und die Zusammenarbeit im Team.
- **Kein reines Statusmeeting**: Es geht nicht um die Abarbeitung von [[Sprint_Backlog]]-Items, sondern um die Demonstration funktionsfähiger Inkremente und die Diskussion des Gesamtprodukts.
- **Keine detaillierte Planung**: Konkrete Aufgaben für den nächsten Sprint werden im [[Sprint_Planning]] besprochen, nicht im Review.

Typische Stolpersteine:
- **Unvorbereitete Stakeholder**: Fehlende oder unklare Rückmeldungen führen zu ineffektiven Reviews.
- **Technische Fokussierung**: Zu starke Konzentration auf Implementierungsdetails statt auf nutzbare Funktionalitäten.
- **Zu lange Dauer**: Reviews sollten zeitlich begrenzt sein (empfohlen: max. 1 Stunde pro Sprint-Woche).
- **Fehlende Inkremente**: Wenn keine funktionsfähigen Ergebnisse präsentiert werden können, verliert das Review seinen Zweck.
- **Beispiel / Code:** ```mermaid
sequenceDiagram
    participant Team as Entwicklungsteam
    participant PO as Product Owner
    participant SH as Stakeholder
    
    Note over Team,SH: Sprint_Review (Zeitrahmen: 2h für 4-Wochen-Sprint)
    Team->>PO: Präsentation des Inkrements (Demo)
    PO->>SH: Erläutert Änderungen und Fortschritt
    SH->>PO: Feedback und Fragen
    PO->>Team: Klärung von Unklarheiten
    SH->>PO: Vorschläge für Backlog-Anpassungen
    PO->>Team: Diskussion über Prioritäten
    Note over PO: Aktualisierung des Produkt_Backlogs
```

**Beispiel-Szenario (Textform):**
*Ein Team hat im Sprint eine neue Suchfunktion für eine E-Commerce-Plattform implementiert. Im Sprint_Review wird diese live demonstriert. Die Stakeholder testen die Funktion und geben Feedback:
- *Positiv*: Die Filteroptionen sind intuitiv.
- *Verbesserung*: Die Ladezeiten bei großen Datenmengen sind zu lang.
- *Neue Idee*: Eine „Merkliste“-Funktion wäre wünschenswert.
Der Product Owner notiert die Punkte und passt den Produkt_Backlog entsprechend an, z. B. durch Hinzufügen einer User Story für Performance-Optimierungen.*
