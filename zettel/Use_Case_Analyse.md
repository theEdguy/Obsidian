---
id: 62a17777-f631-49c3-bbc2-90306aead785
title: "Use_Case_Analyse"
date: 2026-06-23
tags:
  - software_engineering
  - anforderungsanalyse
  - modellierung
  - analyse
  - anforderungen
  - analysis
  - requirements
  - draft
source: "software_engineering_kapitel_11"
---

# [[Use_Case_Analyse]]

- **Kernkonzept:** Die [[Use_Case_Analyse]] ist eine zentrale [[Methode]] im [[Software_Engineering]], um [[funktionale_Anforderung|funktionale]] und [[nicht-funktionale_Anforderung|nicht-funktionale Anforderungen]] an ein [[Softwaresystem]] aus der Perspektive der beteiligten [[Akteur|Akteure]] strukturiert zu erfassen. Sie identifiziert und priorisiert die zentralen [[Anwendungsfall|Anwendungsfälle]] eines Systems, definiert [[Systemgrenze|Systemgrenzen]] und modelliert die [[Interaktion|Interaktionen]] zwischen [[Akteur|Akteuren]] und System, um ein gemeinsames [[Problemverständnis]] zwischen [[Stakeholder|Stakeholdern]] zu schaffen und spezifische [[Ziel|Ziele]] der [[Nutzer]] zu erreichen.
- **Nutzen & Zweck:** Die [[Use_Case_Analyse]] löst das Problem unklarer, unvollständiger oder unstrukturierter [[Anforderung|Anforderungen]] an ein [[Softwaresystem]], indem sie zentrale [[Ablauf|Abläufe]] und [[Interaktion|Interaktionen]] aus der Perspektive der [[Akteur|Akteure]] systematisch und nutzerzentriert erfasst. Sie dient als Grundlage für die [[Entwicklungsplanung]], [[Architekturentscheidung|Architekturentscheidungen]], [[Systemdesign]] und [[Testen]], reduziert das Risiko von [[Fehlentwicklung|Fehlentwicklungen]] oder [[Missverständnis|Missverständnissen]] und schärft das [[Problemverständnis]] durch Fokussierung auf die kritischsten [[Anwendungsfall|Anwendungsfälle]]. Im Gegensatz zu [[User_Story|User Stories]] ist sie formaler und stärker auf die Definition von [[Systemgrenze|Systemgrenzen]] sowie die strukturierte Erfassung von [[Anforderung|Anforderungen]] ausgerichtet. Sie stellt sicher, dass [[Entwickler]] und [[Stakeholder]] ein gemeinsames Verständnis der [[Systemfunktion|Systemfunktionen]] entwickeln, um diese später im [[Design]] und in der [[Implementierung]] umzusetzen.
- **Abgrenzung & Grenzen:** Die [[Use_Case_Analyse]] ist nicht geeignet für die detaillierte technische [[Umsetzung]], [[Algorithmen|Algorithmen]]-Entwicklung oder [[Datenmodellierung]]. Sie eignet sich nur bedingt für [[nicht-funktionale_Anforderung|nicht-funktionale Anforderungen]], die sich nicht als [[Interaktion|Interaktionen]] zwischen [[Akteur|Akteuren]] und System darstellen lassen (z. B. [[Performance]], [[Sicherheitsanforderung|Sicherheitsanforderungen]] oder technische [[Rahmenbedingung|Rahmenbedingungen]]). Für sehr granulare oder technisch spezifische [[Anforderung|Anforderungen]] sind Alternativen wie [[User_Story|User Stories]] (im [[agilen_Prozess|agilen Umfeld]]) oder formale [[Spezifikation|Spezifikationen]] besser geeignet. Zudem stößt die [[Use_Case_Analyse]] an Grenzen, wenn es um die Abbildung zeitlicher Abfolgen komplexer [[Workflow|Workflows]] oder [[Event-gesteuertes_System|Event-gesteuerter Systeme]] geht, da sie primär auf die Beschreibung von [[Interaktion|Interaktionen]] und nicht auf prozessuale Details oder [[Asynchronität]] fokussiert. Sie ist weniger geeignet für Systeme mit minimaler [[Nutzerinteraktion]] oder rein algorithmische [[Lösung|Lösungen]], bei denen [[funktionale_Anforderung|funktionale Anforderungen]] trivial sind.
- **Beispiel / Code:** ```plantuml
@startuml
actor Kunde
actor Vereinsmanager
actor Mail_Client as "[[Mail_Client|Mail Client]]"

Kunde -> (Bestellung aufgeben)
Kunde -> (Zahlung durchführen)
(Bestellung aufgeben) .> (Zahlung durchführen) : <<includes>>

Vereinsmanager -> (Mitglieder verwalten)
(Mitglieder verwalten) .> (E-Mail senden) : <<extends>>
(E-Mail senden) --> Mail_Client
@enduml
```

```java
// Beispiel: Struktur eines Use Case in textueller Form (Vorlage)
UseCase: "Mitglieder verwalten"
Akteure: [[Vereinsmanager]], [[Mail_Client|Mail Client]]
Systemgrenze: MyClub
Priorität: 1 (hoch)
Vorbedingung: MyClub ist installiert, [[Vereinsmanager]] ist authentisiert.
Beschreibung:
  1. [[Vereinsmanager]] wählt Option "Mitglieder verwalten".
  2. System zeigt Liste aller [[Mitglied|Mitglieder]] an.
  3. [[Vereinsmanager]] kann:
     - Neues [[Mitglied]] anlegen,
     - [[Mitglied]] bearbeiten ([[Adresse]], Name, Abteilung),
     - [[Mitglied]] löschen.
  4. Bei Abteilungsänderung: System sendet E-Mail an Abteilungsleiter und [[Mitglied]] via [[Mail_Client|Mail Client]].
  5. [[Mitglied]] ohne Abteilung wird als "passiv" markiert.
Nachbedingung: Mitgliederliste ist aktualisiert, ggf. [[Benachrichtigung|Benachrichtigungen]] versendet.
Offene Punkte: Benachrichtigungsregeln für [[Mitglied|Mitglieder]] bei Änderungen.

// Beispiel: Systemoperation für den Use Case 'Mitglieder verwalten'
public class MemberManagementService {
    /**
     * Initialisiert den Use Case 'Mitglieder verwalten' nach erfolgreicher Authentifizierung.
     * @param token Authentisierungstoken des Nutzers
     * @throws InvalidTokenException falls das Token nicht validiert werden kann
     * @throws DatabaseUnavailableException falls die [[Datenbank]] nicht erreichbar ist
     */
    public void manageMembers(Token token) throws InvalidTokenException, DatabaseUnavailableException {
        if (!validateToken(token)) {
            throw new InvalidTokenException("Token konnte nicht validiert werden.");
        }
        List<Member> members = database.loadMembers();
        // Aufbereitung der Mitgliederdaten für die weitere Verarbeitung
    }

    private boolean validateToken(Token token) {
        // Validierungslogik
        return true;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[System-Use-Cases]]
  - [[Akteure]]
  - [[Mockups]]
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Domain-Analyse]]
