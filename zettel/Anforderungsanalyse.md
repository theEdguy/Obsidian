---
id: ff7c6046-30b7-4a36-995a-c5d6b7b41d6c
title: "Anforderungsanalyse"
date: 2026-06-23
tags:
  - software_engineering
  - requirements_engineering
  - analyse
  - anforderungen
  - draft
source: "software_engineering_kapitel_09"
---

# [[Anforderungsanalyse]]

- **Kernkonzept:** Die [[Anforderungsanalyse]] ist der systematische [[Prozess]] zur Erfassung, Strukturierung und Bewertung von [[Anforderung|Anforderungen]] – sowohl [[funktionale_Anforderung|funktionalen]] als auch [[nicht-funktionale_Anforderung|nicht-funktionalen]] – an ein [[Softwaresystem]], um ein gemeinsames Verständnis zwischen [[Stakeholder|Stakeholdern]] und [[Entwickler|Entwicklern]] zu schaffen. Ziel ist die Schaffung einer konsistenten Grundlage für [[Design]], [[Implementierung]], [[Use_Case|Use-Case]]-Modellierung und [[Systemdesign]], um spätere [[Änderung|Änderungen]] oder [[Fehlentwicklung|Fehlentwicklungen]] zu vermeiden und die [[Problemdomäne]] präzise zu erfassen.
- **Nutzen & Zweck:** Die [[Anforderungsanalyse]] löst das Problem unklarer oder widersprüchlicher [[Zielvorgabe|Zielvorgaben]] in [[Softwareprojekt|Softwareprojekten]] durch systematische Aufbereitung der [[Problemdomäne]] und stellt sicher, dass alle [[Stakeholder]]-Bedürfnisse verstanden und in [[überprüfbare_Anforderung|überprüfbare Anforderungen]] überführt werden. Sie reduziert [[Entwicklungsrisiko|Entwicklungsrisiken]] durch frühzeitige Klärung kritischer [[Funktion|Funktionen]] und bildet die Grundlage für [[Architektur]], [[Design]], [[Teststrategie|Teststrategien]] sowie [[Qualitätssicherung]]. Dadurch werden Missverständnisse zwischen Auftraggebern und [[Entwickler|Entwicklern]] vermieden, spätere [[Nachbesserung|Nachbesserungen]] verhindert und die [[Kosten]] für [[Fehlentwicklung|Fehlentwicklungen]] minimiert. Zudem ermöglicht sie eine klare [[Spezifikation]] für die [[Implementierung]] und dient als Referenz für [[Validierung]] und [[Verifikation]] des [[Softwaresystem|Systems]].
- **Abgrenzung & Grenzen:** Die [[Anforderungsanalyse]] ist kein Ersatz für [[Prototyping]] oder [[Benutzerfeedback]] und sollte nicht mit [[Systemanalyse]] oder [[Implementierung]] verwechselt werden – sie beschreibt ausschließlich *was* das [[System]] leisten muss, nicht *wie*. Bei extrem dynamischen [[Anforderung|Anforderungen]] oder trivialen [[Projekt|Projekten]] mit minimaler Komplexität kann der Aufwand den Nutzen übersteigen. Im Gegensatz zu [[Ad-hoc-Entwicklung|Ad-hoc-Entwicklungen]] erfordert sie strukturierte [[Methode|Methoden]] wie [[Interview|Interviews]], [[Workshop|Workshops]], [[Prototyping]] oder [[Use_Case|Use-Case]]-Modellierung. Alternativen wie [[User_Story|User Stories]] in [[agile_Entwicklung|agilen Entwicklungsprozessen]] sind weniger formal und eignen sich besser für iterative, flexible [[Entwicklungsprozess|Entwicklungsprozesse]], bieten jedoch weniger Struktur für komplexe [[System|Systeme]]. Die [[Anforderungsanalyse]] unterscheidet sich von reiner Feature-Listung durch ihren Fokus auf [[Kontext]], [[Akteur|Akteure]], [[Use_Case|Use-Cases]] und die Berücksichtigung von [[Abhängigkeit|Abhängigkeiten]] zwischen [[Anforderung|Anforderungen]]. Sie ist ungeeignet, wenn keine klaren [[Stakeholder|Stakeholder]] oder [[Zielvorgabe|Zielvorgaben]] vorhanden sind oder wenn [[Anforderung|Anforderungen]] bereits vollständig und unveränderlich vorliegen.
- **Beispiel / Code:** ```java
// Beispiel für strukturierte Anforderungserfassung in einem Use-Case-Dokument
public class UseCase_MitgliederVerwalten {
    // Funktionale Anforderung: Mitglied aus Abteilung entfernen (FR-002)
    public void abteilungVerlassen([[Mitglied|Mitglied]] mitglied, [[Abteilung|Abteilung]] abteilung) {
        if (!mitglied.istInAbteilung(abteilung)) {
            throw new IllegalArgumentException("[[Mitglied]] gehört nicht der [[Abteilung]] an.");
        }
        abteilung.entferneMitglied(mitglied);
        if (mitglied.getAbteilungen().isEmpty()) {
            mitglied.setStatus([[MitgliedStatus|MitgliedStatus.PASSIV]]);
            benachrichtigeMitglied(mitglied);
        }
    }
    
    // Nicht-funktionale Anforderung: Benachrichtigung muss innerhalb von 24h erfolgen (NFR-001)
    private void benachrichtigeMitglied([[Mitglied|Mitglied]] mitglied) {
        System.out.println("Benachrichtigung an " + mitglied.getEmail() + " gesendet.");
        // Akzeptanzkriterium: E-Mail-Versand muss asynchron und innerhalb von 24h erfolgen
    }
}
```

```plaintext
// Beispiel für tabellarische Anforderungsdokumentation
Ref.# | Funktion/Constraint                     | Kategorie | Priorität | Akzeptanzkriterium
------|------------------------------------------|-----------|-----------|---------------------
F1.1  | [[Mitglied]] anlegen                    | must      | Hoch      | Name, Adresse und Beitrittsdatum müssen erfasst werden.
F1.2  | [[Adresse]] ändern                       | must      | Hoch      | [[Adresse]] muss validiert und aktualisiert werden.
A1.1  | Zugriff nur nach [[Authentisierung]]     | must      | Hoch      | Nur autorisierte [[Akteur|Akteure]] dürfen Änderungen vornehmen.
NFR-001 | E-Mail-Benachrichtigung innerhalb 24h    | must      | Mittel    | Asynchroner Versand, Protokollierung des Sendezeitpunkts.
```

```java
// Beispiel: Strukturierte Anforderung als Use-Case-Beschreibung (nach Larman)
UseCase {
    name: "[[Mitglied]] verwalten",
    actors: ["[[Vereinsmanager]]", "[[MailClient]]"],
    systemBoundary: "MyClub",
    priority: 1,
    requirements: ["F1.1", "F1.2", "F2.1", "NFR-001"],
    description: "Der [[Vereinsmanager]] kann [[Mitglied|Mitgliederdaten]] anlegen, bearbeiten oder löschen. 
                 Bei [[Abteilungswechsel|Abteilungswechseln]] werden betroffene [[Akteur|Akteure]] per E-Mail informiert.",
    preCondition: "[[System]] ist installiert, [[Nutzer]] ist authentisiert",
    postCondition: "[[Mitglied]]-Daten sind aktualisiert, Benachrichtigungen wurden versendet"
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Anforderungserhebung]]
  - [[Anforderungsdokumentation]]
  - [[Anforderungsvalidierung]]
- **Querverweise:**
  - [[Use-Case-basierte_Analyse]]
  - [[Problemdomäne]]
