---
id: 3da74902-bc76-4b7e-a0f5-484ecd25beeb
title: "Evaluierungsphase"
date: 2026-06-23
tags:
  - software_engineering
  - projektmanagement
  - agile_methoden
  - prozess
  - entwicklung
  - draft
source: "software_engineering_kapitel_06"
---

# [[Evaluierungsphase]]

- **Kernkonzept:** Die [[Evaluierungsphase]] (Phase I) ist der initiale Abschnitt eines [[Softwareprojekt|Softwareprojekts]], in dem zentrale [[Anforderung|Anforderungen]] erfasst, strukturiert und priorisiert werden, um ein grundlegendes [[Problemverständnis]] zu entwickeln. Sie dient der Bewertung von [[Machbarkeit]], [[Risiko|Risiken]] und [[Architektur]] sowie als Entscheidungsgrundlage für die weitere [[Projektumsetzung]] oder einen möglichen [[Projektabbruch]]. Durch die Erstellung einer [[Vorversion]] wird die [[Komplexität]] des Vorhabens greifbar und [[Planungssicherheit]] geschaffen.
- **Nutzen & Zweck:** Die [[Evaluierungsphase]] löst das Problem unklarer [[Projektziel|Projektziele]], unkalkulierbarer [[Risiko|Risiken]] und fehlender [[Planungssicherheit]] zu Beginn eines [[Softwareprojekt|Softwareprojekts]]. Durch systematische Analyse der [[Anforderung|Anforderungen]], Erstellung einer [[Vorversion]] und frühzeitige [[Architekturentscheidung|Architekturentscheidungen]] wird die [[Komplexität]] des Vorhabens reduziert und eine fundierte Basis für die [[Projektplanung]] geschaffen. Dies verhindert teure [[Fehlentwicklung|Fehlentwicklungen]], unvorhergesehene [[Kosten]] oder spätere [[Umsetzungsproblem|Umsetzungsprobleme]]. Zudem ermöglicht die Phase eine klare Priorisierung von [[Funktionalität|Funktionalitäten]] und die Identifikation kritischer [[Nicht-funktionale_Anforderung|nicht-funktionaler Anforderungen]] wie [[Performance]] oder [[Sicherheit]].
- **Abgrenzung & Grenzen:** Die [[Evaluierungsphase]] sollte nicht genutzt werden, wenn das [[Softwareprojekt]] bereits klar definierte [[Anforderung|Anforderungen]] und eine stabile [[Architektur]] besitzt oder wenn es sich um sehr kleine, triviale Vorhaben handelt, bei denen der Aufwand der Evaluierung den Nutzen übersteigt. Im Gegensatz zu [[Agile_Entwicklung|agilen Iterationen]], die kontinuierlich [[Anforderung|Anforderungen]] anpassen, ist die Evaluierungsphase ein einmaliger, initialer Schritt mit Fokus auf [[Machbarkeitsprüfung]]. Sie ersetzt keine detaillierte [[Anforderungsanalyse]] in späteren Phasen, sondern bereitet diese vor. Zudem ist sie kein Ersatz für eine umfassende [[Risikoanalyse]] oder [[Projektplanung]], sondern dient als deren Grundlage.
- **Beispiel / Code:** ```java
// Beispiel: Grobe Architekturentscheidung in der Evaluierungsphase (UML-ähnliche Notation als Code-Kommentar)
// Zeigt zentrale [[Komponente|Komponenten]], [[Schnittstelle|Schnittstellen]] und [[Nicht-funktionale_Anforderung|nicht-funktionale Anforderungen]]

/*
 * Systemkomponenten (Vorversion):
 * - [[Mitgliederverwaltung]] (Kernfunktionalität)
 *   - Methoden: addMitglied(), updateAdresse(), sendWelcomeMail()
 * - [[Datenbankschnittstelle]] ([[Abstraktionsebene]] zur Datenpersistenz)
 *   - Methoden: persistMitglied(), loadMitglied()
 * - [[Authentifizierung]] ([[Sicherheitsanforderung]])
 *   - Methoden: authenticateUser(), encryptData()
 *
 * Nicht-funktionale Anforderungen:
 * - [[Performance]]: Antwortzeit < 500ms für 90% der [[Anfrage|Anfragen]]
 * - [[Sicherheit]]: AES-256-Verschlüsselung für personenbezogene Daten
 * - [[Erweiterbarkeit]]: [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]] für spätere Anpassungen
 */
public class MitgliederVerwaltung {
    private DatenbankSchnittstelle db;
    private Authentifizierung auth;
    
    public void addMitglied(Mitglied mitglied) {
        auth.encryptData(mitglied.getDaten());
        db.persistMitglied(mitglied);
    }
    
    public void updateAdresse(String mitgliedId, Adresse neueAdresse) {
        Mitglied mitglied = db.loadMitglied(mitgliedId);
        mitglied.setAdresse(neueAdresse);
        db.persistMitglied(mitglied);
        sendWelcomeMail(mitglied);
    }
    
    private void sendWelcomeMail(Mitglied mitglied) {
        // Implementierung der E-Mail-Logik
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b2
- **Vorgänger / Parent:** [[Iterative_Entwicklung]]
- **Folgezettel / Unterzettel:**
  - [[Vorversion]]
  - [[Prototyp]]
  - [[Plan_verfeinern]]
- **Querverweise:** keine
