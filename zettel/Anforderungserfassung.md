---
id: 6abda741-480d-4472-bbbe-50fadd0fc99d
title: "Anforderungserfassung"
date: 2026-06-23
tags:
  - software_engineering
  - prozess
  - analyse
  - anforderung
  - requirements_engineering
  - draft
source: "software_engineering_kapitel_09"
---

# [[Anforderungserfassung]]

- **Kernkonzept:** Die [[Anforderungserfassung]] (auch [[Anforderungserhebung]]) ist der systematische [[Prozess]] der Identifikation, Dokumentation, Strukturierung und Validierung von [[Anforderung|Anforderungen]] an ein [[Softwaresystem]], um die [[Problemdomäne]] präzise zu erfassen und die Bedürfnisse der [[Stakeholder]] als Grundlage für die weitere [[Analyse]] und [[Softwareentwicklung]] zu nutzen. Sie bildet die Brücke zwischen [[Anwender|Anwendern]] und [[Entwickler|Entwicklern]], um eine gemeinsame [[Verständnisbasis]] zu schaffen und [[Missverständnis|Missverständnisse]] zu vermeiden.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die [[Qualität]] der [[Software]] zu sichern und eine methodische Durchgängigkeit von der [[Analyse]] bis zur [[Implementierung]] zu gewährleisten. Durch strukturierte [[Anforderungserfassung]] werden unklare oder unvollständige [[Spezifikation|Spezifikationen]] vermieden, die zu [[Fehlentwicklung|Fehlentwicklungen]], Nacharbeit und erhöhten [[Kosten]] führen können. Sie verbessert die [[Kommunikation]] zwischen [[Auftraggeber|Auftraggebern]] und [[Entwickler|Entwicklern]], stellt sicher, dass das [[System]] die tatsächlichen Bedürfnisse der [[Stakeholder]] erfüllt, und ermöglicht eine frühzeitige Prüfung der technischen [[Machbarkeit]]. Zudem schafft sie eine nachvollziehbare Grundlage für alle weiteren [[Entwicklungsschritt|Entwicklungsschritte]], insbesondere in [[Projekt|Projekten]] mit klaren [[Ziel|Zielen]] und definierten [[Prozess|Prozessen]].
- **Abgrenzung & Grenzen:** Die [[Anforderungserfassung]] sollte nicht in [[Projekt|Projekten]] mit extrem dynamischen oder unklaren [[Ziel|Zielen]] eingesetzt werden, bei denen sich [[Anforderung|Anforderungen]] ständig ändern und keine stabile Basis für die Dokumentation existiert. Sie unterscheidet sich von ad-hoc-Ansätzen oder spontanen [[Brainstorming]]-Methoden durch ihre Systematik und Dokumentationspflicht und konzentriert sich ausschließlich auf das *Was* ([[Problemraum]]) und nicht auf das *Wie* ([[Lösungsraum]]). Während klassische [[Anforderungserfassung]] oft einen festen Rahmen zu Beginn eines [[Projekt|Projekts]] festlegt, bieten [[agile_Methoden|agile Methoden]] wie [[User_Story|User Stories]] oder [[Prototyping]] mehr Flexibilität in dynamischen Umgebungen. Dennoch kann die [[Anforderungserfassung]] durch solche Ansätze ergänzt, aber nicht vollständig ersetzt werden, da sie eine explizite, nachvollziehbare und validierbare Grundlage schafft. In sehr kleinen oder experimentellen [[Projekt|Projekten]] ohne klare [[Stakeholder]] oder bei trivialen [[System|Systemen]] mit minimaler [[Komplexität]] kann sie jedoch überdimensioniert wirken. Sie ist ungeeignet, wenn [[Anforderung|Anforderungen]] bereits vollständig und stabil vorliegen.
- **Beispiel / Code:** ```java
// Beispiel 1: Dokumentierte Anforderung in Form einer User Story und zugehöriger Klasse
/*
 * User Story: 
 * Als Vereinsmitglied möchte ich meine aktuelle Leistung abrufen können,
 * damit ich meinen Fortschritt überwachen kann.
 *
 * Akzeptanzkriterien:
 * - Die Leistung wird in Punkten angezeigt.
 * - Das System muss die Leistung für ein bestimmtes Datum prognostizieren können.
 * - Die Anforderung ist mit einer eindeutigen Kennung (z. B. "REQ-001") versehen.
 */

class Mitglied {
    private String name;
    private String adresse;
    private int alter;
    private int leistung;
    
    public int leistungsprognose(Date datum) {
        // Logik zur Berechnung der prognostizierten Leistung
        return this.leistung * berechneFaktor(datum);
    }
    
    private int berechneFaktor(Date datum) {
        // Implementierungsdetails
        return 1;
    }
}

// Beispiel 2: Strukturierte Anforderung in einem Use-Case-Dokument
public class MitgliedVerwaltenUseCase {
    /**
     * Anforderung: Ein Mitglied soll sich im System registrieren können.
     * Kennung: REQ-002
     * Akteur: Neues Mitglied
     * Vorbedingung: Mitglied ist nicht im System erfasst.
     * Nachbedingung: Mitglied ist im System registriert und erhält eine Bestätigungsmail.
     *
     * @param mitgliedsdaten Die Daten des neuen Mitglieds (Name, E-Mail, etc.)
     * @return Bestätigungsstatus der Registrierung
     */
    public boolean registriereMitglied(Mitgliedsdaten mitgliedsdaten) {
        // Logik zur Speicherung der Mitgliedsdaten
        sendeBestaetigungsmail(mitgliedsdaten.getEmail());
        return true;
    }
    
    private void sendeBestaetigungsmail(String email) {
        // Implementierung der E-Mail-Versandlogik
    }
}

// Beispiel 3: Strukturierte Anforderung in User-Story-Format (aus Requirements-Dokumentation)
public class UserStory {
    private String id;          // Eindeutige Kennung (z. B. "REQ-001")
    private String description; // Beschreibung der Anforderung
    private String acceptanceCriteria; // Akzeptanzkriterien
    
    public UserStory(String id, String description, String acceptanceCriteria) {
        this.id = id;
        this.description = "Als [[Rolle|Rolle]] möchte ich [Funktion], damit [Nutzen].";
        this.acceptanceCriteria = acceptanceCriteria;
    }
    
    // Beispiel-Instanz:
    // new UserStory("REQ-003", 
    //     "Als Vereinsmanager möchte ich [[Mitglied|Mitglieder]] verwalten, damit ich den Überblick über aktive Mitglieder behalte.",
    //     "- Ein Mitglied kann hinzugefügt, bearbeitet oder gelöscht werden.\n- Der Status eines Mitglieds (aktiv/passiv) ist änderbar.");
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4a
- **Vorgänger / Parent:** [[Anforderungsanalyse]]
- **Folgezettel / Unterzettel:**
  - [[Interview]]
  - [[Fragebogen]]
  - [[Beobachtung]]
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Stakeholder]]
