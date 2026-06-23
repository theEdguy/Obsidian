---
id: f1b34b83-6b40-439a-af33-53e8b368cc11
title: "Sprint_Review"
date: 2026-06-23
tags:
  - software_engineering
  - scrum
  - agile_entwicklung
  - projektmanagement
  - produktentwicklung
  - feedback_schleife
  - sprint_review
  - team_motivation
  - definition_of_done
  - stakeholder_management
  - draft
source: "software_engineering_kapitel_07"
---

# [[Sprint_Review]]

- **Kernkonzept:** Das [[Sprint_Review]] ist ein zentrales Ereignis im [[Scrum]]-Framework, das am Ende jedes [[Sprint|Sprints]] stattfindet. Es dient der Präsentation der im [[Sprint]] umgesetzten [[Increment|Inkremente]] (potenziell auslieferbare [[Produkt]]versionen) an die [[Stakeholder]] und das [[Entwicklungsteam]], um Feedback zu sammeln, den Fortschritt zu bewerten und den [[Produkt_Backlog]] für zukünftige [[Sprint|Sprints]] anzupassen. Im Gegensatz zur [[Sprint_Retrospektive]] liegt der Fokus auf dem [[Produkt]] selbst und dessen Weiterentwicklung, nicht auf der Prozessoptimierung.
- **Nutzen & Zweck:** Das [[Sprint_Review]] erfüllt mehrere Zwecke und löst zentrale Herausforderungen in der [[agile_entwicklung|agilen Entwicklung]]:

- **Transparenz**: [[Stakeholder]] erhalten Einblick in den aktuellen Stand des [[Produkt|Produkts]] und können Fortschritte nachvollziehen, was Vertrauen und Alignment fördert.
- **Feedback-Schleife**: Durch direkte Rückmeldungen der [[Stakeholder]] werden [[Anforderung|Anforderungen]] präzisiert oder priorisiert, um sicherzustellen, dass das [[Produkt]] den tatsächlichen Bedürfnissen der [[Nutzer]] entspricht. Dies verhindert Fehlentwicklungen durch mangelnde Kommunikation und ermöglicht eine iterative Anpassung der [[Produktvision]].
- **Anpassung des [[Produkt_Backlog|Backlogs]]**: Basierend auf dem Feedback wird der [[Produkt_Backlog]] aktualisiert, um neue Erkenntnisse, geänderte Prioritäten oder technische Abhängigkeiten zu berücksichtigen. Dies stellt sicher, dass das Team stets an den wertvollsten [[Feature|Features]] arbeitet.
- **Motivation & Anerkennung**: Das [[Entwicklungsteam]] sieht die Ergebnisse seiner Arbeit und erhält direkte Anerkennung von [[Stakeholder|Stakeholdern]], was die [[Team_Motivation]] und das Engagement steigert.
- **Risikominimierung**: Frühzeitige Identifikation von Abweichungen zwischen [[Produktvision]] und Umsetzung reduziert spätere Korrekturkosten und vermeidet teure Nacharbeiten.
- **Datenbasierte Entscheidungen**: Das [[Sprint_Review]] liefert empirische Daten über den Fortschritt, die im [[Sprint_Planning]] für realistischere Planungen genutzt werden können.
- **Zusammenarbeit fördern**: Es stärkt die Interaktion zwischen [[Entwicklungsteam]], [[Product_Owner]] und [[Stakeholder|Stakeholdern]], indem es einen strukturierten Rahmen für den Austausch bietet und Missverständnisse frühzeitig aufdeckt.
- **Abgrenzung & Grenzen:** Das [[Sprint_Review]] ist klar von anderen [[Scrum]]-Ereignissen und traditionellen Projektmanagement-Methoden abzugrenzen:

- **Nicht zu verwechseln mit der [[Sprint_Retrospektive]]**: Während das [[Sprint_Review]] das *[[Produkt]]* evaluiert (Was wurde erreicht?), analysiert die [[Sprint_Retrospektive]] den *Prozess* (Wie wurde gearbeitet?) und die Zusammenarbeit im [[Team]]. Beide Ereignisse ergänzen sich, dienen jedoch unterschiedlichen Zielen.
- **Kein reines Statusmeeting**: Es geht nicht um die Abarbeitung von [[Sprint_Backlog]]-[[Item|Items]] oder eine reine Präsentation von Fortschrittsberichten. Stattdessen steht die Demonstration funktionsfähiger [[Increment|Inkremente]] und die Diskussion des Gesamt[[produkt|produkts]] im Vordergrund.
- **Keine detaillierte Planung**: Konkrete Aufgaben für den nächsten [[Sprint]] werden im [[Sprint_Planning]] besprochen, nicht im [[Sprint_Review]]. Letzteres dient der inhaltlichen Ausrichtung, nicht der operativen Planung.
- **Keine Abnahmeveranstaltung**: Das [[Sprint_Review]] ist kein formales Abnahmegespräch, bei dem [[Feature|Features]] lediglich abgehakt werden. Es ist ein kollaborativer Workshop, der Raum für Diskussionen, Fragen und kreative Ideen bietet.
- **Alternativen & Grenzen**: Bei Projekten mit starren [[Anforderung|Anforderungen]] oder ohne [[Stakeholder]]-Interaktion (z. B. reine Wartungsaufgaben) ist der Nutzen des [[Sprint_Review|Sprint Reviews]] begrenzt. Traditionelle Meilenstein-Reviews sind weniger iterativ und flexibel, da sie seltener stattfinden und weniger Raum für kontinuierliche Anpassungen bieten.

**Typische Stolpersteine und Anti-Patterns:**
- **Unvorbereitete [[Stakeholder]]**: Fehlende oder unklare Rückmeldungen führen zu ineffektiven [[Sprint_Review|Reviews]]. Eine gute Vorbereitung (z. B. durch vorab bereitgestellte Demo-Szenarien oder Fragen) ist essenziell.
- **Technische Fokussierung**: Zu starke Konzentration auf Implementierungsdetails (z. B. [[Algorithmus|Algorithmen]], [[Datenbank]]-Schemata) statt auf nutzbare [[Funktionalität|Funktionalitäten]] und [[Nutzer]]-Bedürfnisse.
- **Zu lange Dauer**: [[Sprint_Review|Reviews]] sollten zeitlich begrenzt sein (empfohlen: max. 1 Stunde pro [[Sprint]]-Woche). Eine klare Agenda und Moderation helfen, den Fokus zu wahren.
- **Fehlende [[Increment|Inkremente]]**: Wenn keine funktionsfähigen Ergebnisse präsentiert werden können (z. B. wegen unvollständiger [[Definition_of_Done]]), verliert das [[Sprint_Review]] seinen Zweck. Dies untergräbt die Glaubwürdigkeit des [[Teams]] und die Transparenz gegenüber [[Stakeholder|Stakeholdern]].
- **Passive [[Stakeholder]]**: Wenn [[Stakeholder]] das [[Sprint_Review]] nur als Zuschauer erleben, statt aktiv Feedback zu geben, verfehlt es seinen kollaborativen Charakter. Der [[Product_Owner]] sollte gezielt Fragen stellen und Diskussionen anregen.
- **Überladene Agenda**: Zu viele Themen oder [[Feature|Features]] in einem [[Sprint_Review]] führen zu oberflächlichen Diskussionen. Besser ist es, sich auf die wichtigsten [[Increment|Inkremente]] zu konzentrieren.
- **Beispiel / Code:** ```mermaid
sequenceDiagram
    participant Team as Entwicklungsteam
    participant PO as Product Owner
    participant SH as Stakeholder
    
    Note over Team,SH: Sprint_Review (Zeitrahmen: 2h für 4-Wochen-Sprint)
    Team->>PO: Präsentation des Inkrements (Demo der neuen Suchfunktion)
    PO->>SH: Erläutert Änderungen, Fortschritt und Kontext (z. B. Nutzerfeedback aus Usability-Tests)
    SH->>PO: Feedback und Fragen (z. B. zu Performance oder UX)
    PO->>Team: Klärung von Unklarheiten (z. B. technische Machbarkeit neuer Ideen)
    SH->>PO: Vorschläge für Backlog-Anpassungen (z. B. Priorisierung einer Merkliste-Funktion)
    PO->>Team: Diskussion über Prioritäten und nächste Schritte
    Note over PO: Aktualisierung des Produkt_Backlogs (z. B. neue User Story für Performance-Optimierung)
```

```java
// Pseudocode zur Vorbereitung eines Sprint Reviews (z. B. in Jira/Scrum-Tool)
public class SprintReviewPreparation {
    public static void main(String[] args) {
        Sprint currentSprint = new Sprint("Sprint 42");
        List<BacklogItem> completedItems = currentSprint.getCompletedItems();
        
        // Prüfe, ob alle Definition-of-Done-Kriterien erfüllt sind
        for (BacklogItem item : completedItems) {
            if (!item.meetsDefinitionOfDone()) {
                throw new IncompleteWorkException("Item " + item.getId() + " ist nicht fertig!");
            }
        }
        
        // Erstelle Demo-Szenarien für das Review
        List<DemoScenario> demoScenarios = prepareDemoScenarios(completedItems);
        inviteStakeholders(demoScenarios);
    }
    
    private static List<DemoScenario> prepareDemoScenarios(List<BacklogItem> items) {
        // Logik zur Aufbereitung der Inkremente für die Präsentation
        // Fokus auf Nutzerperspektive und wertvolle Funktionalitäten
        return items.stream()
                   .map(item -> new DemoScenario(
                       item.getUserStory(), 
                       item.getAcceptanceCriteria(),
                       item.getBusinessValue()
                   ))
                   .collect(Collectors.toList());
    }
    
    private static void inviteStakeholders(List<DemoScenario> scenarios) {
        // Versende Einladungen mit Agenda und Vorbereitungsmaterial
        StakeholderManager.notify(
            "Sprint Review Einladung",
            "Bitte bereiten Sie sich auf folgende Demo-Szenarien vor: " + scenarios
        );
    }
}
```

**Beispiel-Szenario (Textform):**
*Ein [[Entwicklungsteam]] hat im [[Sprint]] eine neue Suchfunktion für eine [[E-Commerce]]-Plattform implementiert. Im [[Sprint_Review]] wird diese live demonstriert, wobei der [[Product_Owner]] den Kontext erläutert (z. B. Nutzerfeedback aus [[Usability_Test|Usability-Tests]] oder Marktanalysen). Die [[Stakeholder]] testen die Funktion und geben strukturiertes Feedback:
- *Positiv*: Die [[Filter|Filteroptionen]] sind intuitiv und die [[Benutzeroberfläche]] ist ansprechend gestaltet.
- *Verbesserung*: Die Ladezeiten bei großen [[Datenmenge|Datenmengen]] sind zu lang. Hier könnte eine [[Lazy_Loading|Lazy-Loading]]-Strategie helfen.
- *Neue Idee*: Eine „Merkliste“-Funktion wäre wünschenswert, um die [[Conversion_Rate]] zu steigern.
- *Frage*: Wie verhält sich die Suche bei [[Synonym|Synonymen]] oder Tippfehlern?

Der [[Product_Owner]] notiert die Punkte und passt den [[Produkt_Backlog]] entsprechend an:
1. **Neue [[User_Story]]**: "Als Nutzer möchte ich, dass die Suchfunktion auch bei großen [[Datenmenge|Datenmengen]] schnell reagiert, um ein flüssiges Einkaufserlebnis zu haben." (Priorität: Hoch)
2. **Spike**: Untersuchung der Machbarkeit einer Merkliste-Funktion und deren Integration in den [[Checkout-Prozess]].
3. **Technische Aufgabe**: Implementierung einer [[Fuzzy_Suche]] für Tippfehler-Toleranz.

Das [[Team]] diskutiert anschließend mit dem [[Product_Owner]] die Prioritäten und mögliche Abhängigkeiten, um die nächsten [[Sprint|Sprints]] optimal zu planen.*

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9b3
- **Vorgänger / Parent:** [[Scrum-Events]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Scrum-Events]]
  - [[Scrum]]
