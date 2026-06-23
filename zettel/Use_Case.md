---
id: 17e40a72-ea2d-491b-8fd3-95a8a7c9312d
title: "Use_Case"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - anforderung
  - anforderungserhebung
  - requirements_engineering
  - uml
  - modellierung
  - draft
source: "software_engineering_kapitel_10"
---

# [[Use_Case]]

- **Kernkonzept:** Ein [[Use_Case|Use Case]] beschreibt eine strukturierte [[Interaktion]] zwischen einem oder mehreren [[Akteur|Akteuren]] (z. B. [[Endbenutzer|Endbenutzern]], [[Fremdsystem|Fremdsystemen]] oder [[Stakeholder|Stakeholdern]]) und einem [[System]] oder [[Softwaresystem]], um ein spezifisches [[Ziel]] aus [[Nutzer|Nutzersicht]] zu erreichen. Er formalisiert [[funktionale_Anforderung|funktionale Anforderungen]] durch [[szenariobasierte_Beschreibung|szenariobasierte Beschreibungen]] und dient als zentrales Element in der [[objektorientierte_Analyse|objektorientierten Analyse]] und [[Modellierung]], um [[Systemverhalten]] nutzerzentriert und systematisch zu erfassen.
- **Nutzen & Zweck:** Ein [[Use_Case|Use Case]] löst das zentrale Problem unklarer oder widersprüchlicher [[Anforderung|Anforderungen]] in der [[Anforderungsanalyse]] und [[Anforderungserhebung]], indem er [[Funktionalität]] aus der Perspektive der [[Akteur|Akteure]] systematisch erfasst, priorisiert und verständlich dokumentiert. Dadurch verbessert er die [[Kommunikation]] zwischen [[Stakeholder|Stakeholdern]], [[Entwickler|Entwicklern]] und [[Kunde|Kunden]], reduziert [[Missverständnisse]] und schafft eine belastbare Grundlage für [[Systemdesign]], [[Analysemodell|Analysemodelle]], [[Testfall|Testfälle]], [[Geschäftsprozessmodellierung]] und iterative [[Entwicklungszyklus|Entwicklungszyklen]]. Use Cases vereinfachen die [[Kommunikation]] zwischen technischen und nicht-technischen [[Projektbeteiligte|Beteiligten]], indem sie [[Systemfunktion|Systemfunktionen]] in [[zielorientierte_Beschreibung|zielorientierten Szenarien]] darstellen und so ein gemeinsames Verständnis der [[Systemanforderung|Systemanforderungen]] fördern. Sie bilden die Grundlage für die weitere [[Systemmodellierung]], z. B. für die Erstellung von [[Aktivitätsdiagramm|Aktivitätsdiagrammen]], [[Klassendiagramm|Klassendiagrammen]] oder [[Sequenzdiagramm|Sequenzdiagrammen]], und helfen, den [[Scope]] eines [[Projekt|Projekts]] frühzeitig zu definieren. Zudem ermöglichen sie die Identifikation von [[Schnittstelle|Schnittstellen]], [[Abhängigkeit|Abhängigkeiten]] und [[Risiko|Risiken]] im [[Softwareentwicklungsprozess]] und dienen als Referenz für [[agile_Entwicklung|agile Entwicklungsmethoden]] wie [[Scrum]] oder [[Kanban]]. In [[hybride_Entwicklungsmodell|hybriden Entwicklungsmodellen]] werden sie oft durch [[User_Story|User Stories]] ergänzt, um Flexibilität und Präzision zu kombinieren.
- **Abgrenzung & Grenzen:** Ein [[Use_Case|Use Case]] ist kein Ersatz für [[Technische_Spezifikation|technische Spezifikationen]], [[Datenmodell|Datenmodelle]] oder nicht-funktionale [[Anforderung|Anforderungen]] wie [[Performance]], [[Sicherheit]], [[Skalierbarkeit]] oder [[Benutzerfreundlichkeit]]. Er eignet sich nicht für [[Projekt|Projekte]] mit rein internen oder technischen [[Anforderung|Anforderungen]], die keine [[Akteur|Akteure]] involvieren, oder für die Darstellung zeitlicher [[Ablauf|Abläufe]] (hier sind [[Flussdiagramm|Flussdiagramme]] oder [[BPMN]] besser geeignet). Zudem sollte er nicht mit [[Einzelschritt|Einzelschritt]]-Beschreibungen (z. B. "[[Button_klicken]]") oder [[technisches_Detail|technischen Details]] (z. B. "[[Datenbankabfrage]]") überladen werden, da dies die Übersichtlichkeit und [[Kohäsion]] des Modells beeinträchtigt. Bei zu vielen [[Use_Case|Use Cases]] kann die [[Modellkomplexität]] steigen, weshalb eine sinnvolle [[Granularität]] und [[Abstraktionsebene]] gewählt werden muss. Im Gegensatz zu [[User_Story|User Stories]] ist er weniger agil, aber präziser, und wird oft durch diese in [[agile_Entwicklung|agilen Entwicklungsprozessen]] ergänzt. Use Cases sind ungeeignet für die Modellierung von [[Echtzeitsystem|Echtzeitsystemen]] mit komplexen [[Zustandsübergang|Zustandsübergängen]], hier sind [[Zustandsdiagramm|Zustandsdiagramme]] oder [[Petri-Netz|Petri-Netze]] vorzuziehen. Für rein [[datenflussorientierte_System|datenflussorientierte Systeme]] (z. B. [[Batch-Verarbeitung]]) ohne [[Benutzerinteraktion]] sind [[Datenflussdiagramm|Datenflussdiagramme]] oder [[ER-Modell|ER-Modelle]] besser geeignet. In [[algorithmisch_komplexe_System|algorithmisch komplexen Systemen]] ohne Nutzerinteraktion können formale Methoden wie [[OCL]] oder [[Z-Notation]] präzisere Spezifikationen liefern.
- **Beispiel / Code:** ```plaintext
// Beispiel 1: Benutzeranmeldung (klassische Struktur)
Use Case: Benutzer anmelden
Primärer Akteur: [[Endbenutzer]]
Sekundäre Akteure: [[Authentifizierungssystem]]
Vorbedingung: [[Endbenutzer]] ist registriert
Hauptszenario:
1. [[Endbenutzer]] gibt [[Benutzername]] und [[Passwort]] ein.
2. [[System]] validiert die Eingaben.
3. [[System]] gewährt Zugriff und leitet zur Startseite weiter.
Nachbedingung: [[Endbenutzer]] ist authentifiziert
Erweiterungen:
2a. Eingaben sind ungültig → [[System]] zeigt Fehlermeldung an und fordert erneute Eingabe.

// Beispiel 2: Geld abheben (mit Systemgrenze und Priorisierung)
UseCase {
    name: "Geld abheben",
    systemgrenze: "Bankautomatensystem",
    akteure: ["[[Bankkunde]]", "[[Bankserver]]"],
    prioritaet: 2,
    vorbedingung: "[[Bankkunde]] ist authentifiziert, Kontostand ist verfügbar.",
    beschreibung: "Der [[Bankkunde]] wählt den Betrag aus und erhält das Geld. 
                 Bei unzureichendem Kontostand wird eine Fehlermeldung angezeigt.",
    hauptszenario: [
        "[[Bankkunde]] wählt 'Geld abheben' aus.",
        "[[System]] fragt nach Betrag.",
        "[[Bankkunde]] gibt Betrag ein.",
        "[[System]] prüft Kontostand.",
        "[[System]] gibt Geld aus und aktualisiert Kontostand."
    ],
    alternativen: [
        "4a. Kontostand unzureichend → [[System]] zeigt Fehlermeldung an."
    ],
    nachbedingung: "Kontostand ist aktualisiert, Transaktion ist protokolliert.",
    referenzen: ["F3.2", "NF1.5"]
}

// Beispiel 3: Mitglieder verwalten (erweitert mit Mail-Integration)
Use Case: [[Mitglieder_verwalten]]
Akteure: [[Vereinsmanager]], [[Mail_Client]], [[Abteilungsleiter]]
Vorbedingung: [[Vereinsmanager]] ist authentifiziert, [[Mitglied|Mitgliederdatenbank]] ist verfügbar
Hauptszenario:
1. [[Vereinsmanager]] wählt Aktion (anlegen/bearbeiten/löschen) aus.
2. [[System]] zeigt Formular an.
3. [[Vereinsmanager]] gibt Daten ein und bestätigt.
4. [[System]] validiert Eingaben.
5. [[System]] aktualisiert [[Mitglied|Mitgliederdaten]].
6. Bei [[Abteilungswechsel]]: [[System]] sendet Benachrichtigung an [[Abteilungsleiter]] und [[Mitglied]] via [[Mail_Client]].
Nachbedingung: [[Mitglied|Mitgliederdaten]] sind aktualisiert, [[Mail_Client]] hat Benachrichtigung versendet
Alternativszenario:
4a. Eingaben sind ungültig → [[System]] zeigt Fehlermeldung an.

// Beispiel 4: Mitglied anmelden (strukturierter Text für Modellierung)
Use Case: Mitglied anmelden
Akteur: [[Vereinsmitglied]]
Vorbedingung: [[Vereinsmitglied]] ist im System nicht angemeldet
Nachbedingung: [[Vereinsmitglied]] ist angemeldet und hat Zugriff auf seine Daten
Hauptszenario:
1. [[Vereinsmitglied]] gibt Benutzername und Passwort ein.
2. [[System]] validiert die Eingaben.
3. [[System]] gewährt Zugriff auf die Mitgliederfunktionen.
Alternativszenario (Fehlerfall):
2a. Eingaben sind ungültig.
2a1. [[System]] zeigt Fehlermeldung an.
2a2. [[Vereinsmitglied]] kann Eingaben korrigieren (Rückkehr zu Schritt 1).
```

```java
// Beispiel 5: Use Case "Mitglied verwalten" in UML-ähnlicher Notation (programmatische Umsetzung)
@UseCase(name = "Manage Members", actor = "Club Administrator")
public class ManageMembersUseCase {
    private final [[Mitglied|MitgliederRepository]] database;
    private final [[Logger]] logger;
    
    public ManageMembersUseCase([[Mitglied|MitgliederRepository]] database, [[Logger]] logger) {
        this.database = database;
        this.logger = logger;
    }
    
    // Hauptszenario: Mitglied hinzufügen
    public void addMember([[Mitglied]] member) {
        if (!database.exists(member.getId())) {
            database.save(member);
            logger.log("Mitglied hinzugefügt: " + member.getName());
            notifyStakeholders(member, "added");
        }
    }
    
    // Alternativszenario: Mitglied löschen
    public void removeMember(String memberId) {
        if (database.exists(memberId)) {
            [[Mitglied]] member = database.findById(memberId);
            database.delete(memberId);
            logger.log("Mitglied gelöscht: ID " + memberId);
            notifyStakeholders(member, "removed");
        }
    }
    
    // Erweiterter Use Case: Benachrichtigung an Stakeholder senden
    private void notifyStakeholders([[Mitglied]] member, String action) {
        [[Mail_Client]] mailClient = new [[Mail_Client]]();
        String message = String.format("Mitglied %s wurde %s.", member.getName(), action);
        mailClient.sendNotification(member.getEmail(), "Mitgliederstatus geändert", message);
        mailClient.sendNotification(member.getDepartmentHeadEmail(), "Mitgliederänderung", message);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1f
- **Vorgänger / Parent:** [[Software-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Use_Case-Diagramme]]
  - [[Use_Case-Beschreibungen]]
- **Querverweise:** keine
