---
id: 82798f08-d4c9-4160-8982-2e4d566204b1
title: "Nachbedingung"
date: 2026-06-23
tags:
  - software_engineering
  - formale_methode
  - system_design
  - analyse
  - requirements_engineering
  - bedingung
  - software
  - design
  - draft
source: "software_engineering_kapitel_12"
---

# [[Nachbedingung]]

- **Kernkonzept:** Eine [[Nachbedingung]] definiert die Menge der [[Zustand|Zustände]], die nach der erfolgreichen Ausführung einer [[Operation]] oder eines [[Use_Case|Use Cases]] garantiert eintreten müssen. Sie beschreibt das erwartete Ergebnis oder die Veränderungen im [[Systemzustand]] und stellt somit eine formale [[Spezifikation]] der korrekten Funktionsweise dar, um die [[Verifizierbarkeit]] und [[Testbarkeit]] zu gewährleisten.
- **Nutzen & Zweck:** Nachbedingungen dienen dazu, die korrekte Funktionsweise von [[Operation|Operationen]] und [[Use_Case|Use Cases]] formal zu spezifizieren und sicherzustellen, dass alle [[Stakeholder|Stakeholder]] ein einheitliches Verständnis der [[Anforderung|Anforderungen]] haben. Sie lösen das Problem divergierender Vorstellungen über das erwartete Ergebnis einer Aktion, indem sie explizit festlegen, welche Veränderungen eine [[Operation]] im [[Systemzustand]] bewirkt. Dies ermöglicht nicht nur die frühzeitige Erkennung von Fehlern durch unerwartete [[Zustand|Zustände]], sondern unterstützt auch die [[Dokumentation]] und [[Kommunikation]] im [[Requirements_Engineering|Requirements Engineering]] sowie in der [[Systemanalyse|Systemanalyse]]. Zudem erhöhen sie die Wartbarkeit und Verständlichkeit von [[Schnittstelle|Schnittstellen]] und [[Code]], da sie das Verhalten von [[Operation|Operationen]] vorhersehbar und nachvollziehbar machen.
- **Abgrenzung & Grenzen:** Nachbedingungen sollten nicht mit [[Vorbedingung|Vorbedingungen]] verwechselt werden, die den [[Zustand]] vor der Ausführung einer [[Operation]] beschreiben. Sie spezifizieren ausschließlich das *Was* (Ergebnis) und nicht das *Wie* (Implementierung). In Fällen, in denen der [[Systemzustand]] nach einer [[Operation]] nicht relevant oder nicht spezifizierbar ist, sind Nachbedingungen überflüssig. Zudem eignen sie sich nicht zur Beschreibung von [[Ausnahme|Ausnahmen]] oder Fehlerszenarien, die separat als [[Fehlerbehandlung|Fehlerbehandlungen]] oder [[Ausnahmebehandlung|Ausnahmebehandlungen]] modelliert werden sollten. Nachbedingungen beschränken sich auf den erfolgreichen Abschluss einer [[Operation]] und ignorieren temporäre oder interne [[Zustand|Zustände]]. Sie sind ungeeignet, wenn das Verhalten einer [[Operation]] stark von externen, unvorhersehbaren Faktoren abhängt oder wenn die [[Zustand|Zustandsänderungen]] zu komplex sind, um sie präzise zu formulieren. In solchen Fällen können informelle [[Kommentar|Kommentare]] oder [[Testfall|Testfälle]] ausreichen, bieten jedoch nicht die gleiche formale Sicherheit wie explizite Nachbedingungen.
- **Beispiel / Code:** ```java
/**
 * Nachbedingung: Mitglieder können bearbeitet werden oder die Validierung ist fehlgeschlagen.
 * 
 * @param token Der Authentifizierungstoken für die Operation
 * @throws SecurityException Falls der Token ungültig ist
 */
public void manageMembers(Token token) {
    if (validateToken(token)) {
        assert membersEditable : "[[Mitglied|Mitglieder]] sollten bearbeitbar sein";
    } else {
        assert !membersEditable : "Validierung ist fehlgeschlagen";
    }
}

/**
 * Entfernt ein [[Mitglied]] aus einer [[Abteilung]] und aktualisiert dessen Status.
 * 
 * @param mitglied Das zu entfernende Mitglied
 * @param abteilung Die Abteilung, aus der das Mitglied entfernt wird
 * @throws IllegalArgumentException Falls das Mitglied nicht in der Abteilung ist
 * 
 * Nachbedingungen:
 * - Das [[Mitglied]] ist nicht mehr in der [[Abteilung]] enthalten.
 * - Falls das [[Mitglied]] keiner [[Abteilung]] mehr angehört, ist sein Status auf 'passiv' gesetzt.
 * - Die [[Abteilungsleitung]] wurde per E-Mail informiert.
 */
public void abteilungVerlassen(Mitglied mitglied, Abteilung abteilung) {
    // Implementierung der Operation
}

/**
 * Überweist einen Betrag von einem Konto auf ein anderes.
 * 
 * @param betrag Der zu überweisende Betrag (muss positiv sein).
 * @param zielKonto Das Zielkonto der Überweisung.
 * @throws IllegalArgumentException Wenn der Betrag negativ ist oder das Zielkonto ungültig.
 * 
 * Nachbedingungen:
 * - Das Quellkonto.guthaben ist um den Betrag verringert.
 * - Das Zielkonto.guthaben ist um den Betrag erhöht.
 * - Der [[Kontostand]] beider Konten bleibt nicht-negativ.
 */
public void ueberweisen(double betrag, Konto zielKonto) {
    if (betrag <= 0) {
        throw new IllegalArgumentException("Betrag muss positiv sein.");
    }
    if (this.guthaben < betrag) {
        throw new IllegalStateException("Nicht ausreichend Guthaben.");
    }
    
    this.guthaben -= betrag;
    zielKonto.guthaben += betrag;
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3b
- **Vorgänger / Parent:** [[Systemoperationen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Systemoperationen]]
  - [[Vorbedingungen]]
