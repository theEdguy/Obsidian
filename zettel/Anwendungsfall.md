---
id: 0661e932-898c-487a-b8ee-4ec15ca8921d
title: "Anwendungsfall"
date: 2026-06-23
tags:
  - software_engineering
  - anforderungsanalyse
  - modellierung
  - analyse
  - draft
source: "software_engineering_kapitel_08"
---

# [[Anwendungsfall]]

- **Kernkonzept:** Ein [[Anwendungsfall]] beschreibt eine funktionale [[Anforderung]] aus Sicht eines [[Akteur|Akteurs]], der mit dem [[System]] interagiert, um ein bestimmtes Ziel zu erreichen. Er definiert die [[Interaktion]] zwischen [[Akteur|Akteuren]] und [[System]] und ist zentraler Bestandteil der [[Anwendungsfallanalyse]], einer Methode zur systematischen Erfassung und Strukturierung von [[Anforderung|Anforderungen]] aus [[Nutzer|Nutzersicht]].
- **Nutzen & Zweck:** Ein [[Anwendungsfall]] hilft, die [[Systemgrenze|Systemgrenzen]] zu klären und [[Anforderung|Anforderungen]] aus [[Benutzer|Benutzersicht]] zu dokumentieren. Er dient als Grundlage für [[Use-Case-Diagramm|Use-Case-Diagramme]] und die [[Priorisierung]] von Entwicklungsaufgaben. Die [[Anwendungsfallanalyse]] erleichtert die Kommunikation zwischen [[Stakeholder|Stakeholdern]] (z. B. [[Entwickler|Entwicklern]], [[Kunde|Kunden]], [[Domänenexperte|Domänenexperten]]) und verhindert Missverständnisse bei der [[Anforderungserhebung]]. Durch die Fokussierung auf [[Nutzer|Nutzerziele]] und konkrete [[Ablauf|Abläufe]] wird die [[Softwareentwicklung]] zielgerichtet und nachvollziehbar gestaltet. Zudem bildet sie eine Brücke zwischen [[Anforderung|Anforderungen]] und [[Implementierung]].
- **Abgrenzung & Grenzen:** Ein [[Anwendungsfall]] ist kein Ersatz für nicht-funktionale [[Anforderung|Anforderungen]] (z. B. [[Performance]], [[Sicherheit]]). Im Gegensatz zu [[User_Story|User Stories]] sind [[Anwendungsfall|Anwendungsfälle]] detaillierter und formaler dokumentiert. Die [[Anwendungsfallanalyse]] eignet sich weniger für stark algorithmische oder datenintensive [[System|Systeme]], bei denen [[Ablauf|Abläufe]] weniger [[nutzerzentriert]] sind. Alternativen wie [[User_Story|User Stories]] (agile [[Softwareentwicklung]]) oder formale [[Spezifikation|Spezifikationen]] (z. B. [[Z-Notation]]) können in solchen Fällen besser geeignet sein. Zudem ersetzt sie kein detailliertes technisches [[Design]], sondern dient als Vorstufe zur [[Implementierung]].
- **Beispiel / Code:** ```text
Anwendungsfall: Bestellung aufgeben
Akteur: [[Kunde]]
Vorbedingung: [[Kunde]] ist eingeloggt
Hauptszenario:
1. [[Kunde]] wählt [[Produkt|Produkte]] aus.
2. [[System]] zeigt [[Warenkorb]] an.
3. [[Kunde]] bestätigt [[Bestellung]].
4. [[System]] leitet zur [[Zahlung]] weiter.
Erweiterungen:
3a. [[Kunde]] bricht [[Bestellung]] ab.
    3a1. [[System]] verwirft [[Warenkorb]].
Nachbedingung: [[Bestellung]] ist im [[System]] erfasst.
```

```java
// Beispiel: Vereinfachte Use-Case-Beschreibung für "Mitglied anmelden" (als Java-Klasse)
public class MitgliedAnmelden {
    private [[Mitglied]];
    private [[SystemClub]] clubSystem;

    public void ausfuehren(String name, String email) {
        // Szenario: Neues [[Mitglied]] wird im [[System]] registriert
        mitglied = new Mitglied(name, email);
        clubSystem.speichern(mitglied);
        clubSystem.sendeWillkommensEmail(mitglied);
    }
}
```

// Pseudocode für UML-Aktivitätsdiagramm-Elemente
Startknoten: "Mitgliedsdaten eingeben"
Aktion: "Daten validieren"
Entscheidung: {
    Bedingung: "Daten gültig?",
    Ja: "[[Mitglied]] im [[System]] speichern",
    Nein: "Fehlermeldung anzeigen"
}
Ende: "Prozess abgeschlossen"

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Use_Case]]
  - [[Anforderungserfassung]]
  - [[Anwendungsfallstrukturierung]]
- **Querverweise:**
  - [[Use_Case]]
  - [[Anforderungserfassung]]
