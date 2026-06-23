---
id: af5702b9-003d-4068-ac6f-2f5b325bca12
title: "Anforderungsidentifikation"
date: 2026-06-23
tags:
  - software_engineering
  - identifikation
  - anforderungen
  - klassifikation
  - dokumentation
  - spezifikation
  - requirements_engineering
  - draft
source: "software_engineering_kapitel_09"
---

# [[Anforderungsidentifikation]]

- **Kernkonzept:** Die [[Anforderungsidentifikation]] ist der systematische Prozess zur Erkennung, Bewertung, [[Klassifikation|Klassifizierung]], [[Dokumentation]] und strukturierten Beschreibung aller [[funktionale_Anforderung|funktionalen]] und [[nicht-funktionale_Anforderung|nicht-funktionalen Anforderungen]] an ein [[Softwaresystem]]. Sie bildet die Grundlage für die [[Anforderungsspezifikation]], [[Use_Case|Use Cases]] und die weitere [[Anforderungsanalyse]] im [[Software_Engineering]] und schafft eine verbindliche Referenz für [[Stakeholder|Stakeholder]], [[Entwicklung]], [[Qualitätssicherung]] und [[Projektplanung]].
- **Nutzen & Zweck:** Dieses Konzept existiert, um sicherzustellen, dass alle relevanten Bedürfnisse von [[Anwender|Anwendern]] und [[Stakeholder|Stakeholdern]] erfasst, verstanden und strukturiert werden, bevor mit der [[Implementierung]] begonnen wird. Es löst das Problem unklarer, unvollständiger oder widersprüchlicher [[Anforderung|Anforderungen]], die zu Fehlentwicklungen, Nacharbeit und erhöhten Kosten führen können. Durch systematische [[Anforderungsidentifikation]], [[Klassifikation]] und [[Dokumentation]] wird eine zielgerichtete [[Architektur]], [[Implementierung]] und [[Qualitätssicherung]] ermöglicht. Die [[Anforderungsspezifikation]] dient als verbindliche Referenz für alle [[Projektphase|Projektphasen]], vermeidet Missverständnisse zwischen [[Stakeholder|Stakeholdern]] und unterstützt die frühzeitige Identifikation von [[Risiko|Risiken]]. Zudem ermöglicht die strukturierte Erfassung eine transparente [[Priorisierung]] und erleichtert die Zuordnung zu [[Use_Case|Use Cases]] oder [[Architekturkomponente|Architekturkomponenten]]. Ohne dokumentierte [[Anforderung|Anforderungen]] führen unklare Erwartungen häufig zu Fehlentwicklungen oder Projektverzögerungen, da zentrale [[Ablauf|Abläufe]], [[Objekt|Objekte]] und [[Schnittstelle|Schnittstellen]] nicht eindeutig identifiziert werden können.
- **Abgrenzung & Grenzen:** Die [[Anforderungsidentifikation]] und [[Anforderungsspezifikation]] sollten nicht genutzt werden, wenn das [[Problem]] oder der [[Anwendungsfall]] noch nicht ausreichend verstanden ist, da dies zu unvollständigen oder falschen [[Anforderung|Anforderungen]] führen kann. Sie unterscheiden sich von informellen Methoden wie [[Brainstorming]] oder [[User_Story|User Stories]] durch ihre Systematik und Nachvollziehbarkeit. Während [[User_Story|User Stories]] in [[agile_Methode|agilen Methoden]] für iterative, flexible Prozesse geeignet sind, bieten [[Anforderungsidentifikation]] und [[Anforderungsspezifikation]] eine umfassendere und strukturiertere Herangehensweise. In extrem agilen oder unvorhersehbaren Projekten (z. B. frühe [[Prototyping]]-Phasen) kann eine starre [[Dokumentation]] die Flexibilität einschränken; hier eignen sich informellere Methoden wie [[User_Story|User Stories]] oder Skizzen besser. Zudem ersetzt die [[Anforderungsspezifikation]] keine technischen [[Spezifikation|Spezifikationen]] (z. B. [[API]]-Verträge) oder rechtliche Rahmenbedingungen, die separat dokumentiert werden müssen. Die [[Klassifikation]] von [[Anforderung|Anforderungen]] sollte vermieden werden, wenn diese extrem dynamisch oder unklar sind, da starre [[Kategorie|Kategorien]] dann hinderlich sein können. Anforderungsdokumentation ist keine detaillierte technische Spezifikation, sondern fokussiert sich auf das *Was* (Problemdomäne) und nicht auf das *Wie* (Lösungsdesign).
- **Beispiel / Code:** ```java
// Beispiel für eine dokumentierte und klassifizierte funktionale Anforderung (F1.1) in einem Use-Case-Kontext
public enum Anforderungstyp {
    FUNKTIONAL,       // Funktionale Anforderung (z. B. "Mitglied anlegen")
    NICHT_FUNKTIONAL, // Nicht-funktionale Anforderung (z. B. "System muss in <2s antworten")
    SICHERHEIT,       // Sicherheitsanforderung (z. B. "Daten verschlüsselt speichern")
    BENUTZBARKEIT,    // Usability-Anforderung (z. B. "Barrierefreie Oberfläche")
    PERFORMANCE       // Performance-Anforderung (z. B. "95% der Anfragen in <2s verarbeiten")
}

public enum Prioritaet {
    HOCH, MITTEL, NIEDRIG
}

public class Anforderung {
    private String id;                  // Eindeutige Kennung (z. B. "F1.1")
    private String beschreibung;
    private Anforderungstyp typ;
    private Prioritaet prioritaet;
    private List<String> useCaseReferenzen; // Verweise auf zugehörige [[Use_Case|Use Cases]]
    
    public Anforderung(String id, String beschreibung, Anforderungstyp typ, Prioritaet prioritaet) {
        this.id = id;
        this.beschreibung = beschreibung;
        this.typ = typ;
        this.prioritaet = prioritaet;
        this.useCaseReferenzen = new ArrayList<>();
    }
    
    public void addUseCaseReferenz(String useCaseId) {
        this.useCaseReferenzen.add(useCaseId);
    }
    // Getter/Setter...
}

/**
 * Anforderung F1.1: Das System muss es ermöglichen, neue Mitglieder anzulegen.
 * 
 * Akteure: [[Vereinsmanager]]
 * Typ: [[funktionale_Anforderung]]
 * Priorität: HOCH
 * Vorbedingung: Der [[Vereinsmanager]] ist authentisiert.
 * Nachbedingung: Ein neues Mitglied ist im System erfasst.
 * 
 * Ablauf:
 * 1. Der [[Vereinsmanager]] wählt die Option 'Neues Mitglied anlegen'.
 * 2. Das System zeigt ein Formular zur Eingabe der Mitgliedsdaten an.
 * 3. Der [[Vereinsmanager]] gibt die Daten ein und bestätigt die Eingabe.
 * 4. Das System validiert die Daten und speichert das neue Mitglied.
 */
public class MitgliedVerwaltung {
    public void neuesMitgliedAnlegen(Mitgliedsdaten daten) {
        if (daten.validieren()) {
            datenRepository.speichern(daten);
        }
    }
}

// Beispiel für eine nicht-funktionale Anforderung (Performance):
// Anforderung F2.3: Das System muss 95% aller Anfragen innerhalb von 2 Sekunden verarbeiten.
Anforderung performanceAnforderung = new Anforderung(
    "F2.3", 
    "Das System muss 95% aller Anfragen innerhalb von 2 Sekunden verarbeiten.",
    Anforderungstyp.PERFORMANCE,
    Prioritaet.HOCH
);
performanceAnforderung.addUseCaseReferenz("UC-001");

// Beispiel: Strukturierte Anforderungsspezifikation in einem Use-Case-Dokument (auszugsweise)
UseCase mitgliederVerwalten = new UseCase(
    "Mitglieder verwalten",
    List.of("Vereinsmanager", "Mail Client"),
    Prioritaet.HOCH,
    List.of("F1.1", "F1.2", "F2.1"),
    "Der [[Vereinsmanager]] kann [[Mitgliedsdaten]] anlegen, bearbeiten oder löschen. " +
    "Bei [[Abteilungswechsel|Abteilungswechseln]] werden betroffene [[Akteur|Akteure]] per E-Mail informiert.",
    "[[Softwaresystem]] ist installiert und [[Nutzer]] authentisiert."
);
```

```markdown
# Funktionale Anforderungen (Auszug)

## FR-1: Mitgliederverwaltung
- **FR-1.1**: Das System muss es ermöglichen, neue Mitglieder mit Name, Adresse, Geburtsdatum und Mitgliedsstatus (aktiv/passiv) anzulegen.
- **FR-1.2**: Ein [[Vereinsmanager]] muss Mitglieder einer [[Abteilung]] zuordnen und aus dieser entfernen können.
- **FR-1.3**: Bei Austritt aus der letzten [[Abteilung]] muss der Mitgliedsstatus automatisch auf 'passiv' gesetzt werden.

## Nicht-funktionale Anforderungen
- **NFR-1**: Das System muss eine Antwortzeit von < 2 Sekunden für 95% aller Anfragen garantieren.
- **NFR-2**: Die Datenbank muss täglich um 02:00 Uhr automatisch gesichert werden.
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4b
- **Vorgänger / Parent:** [[Anforderungsanalyse]]
- **Folgezettel / Unterzettel:**
  - [[Anforderungsspezifikation]]
  - [[Use-Case-Dokumentation]]
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Software-Dokumentation]]
