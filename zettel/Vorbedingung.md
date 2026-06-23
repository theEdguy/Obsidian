---
id: ba2b948f-84f5-4aa6-8ef7-47c6501946a2
title: "Vorbedingung"
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

# [[Vorbedingung]]

- **Kernkonzept:** Eine [[Vorbedingung]] definiert die Menge der [[Zustand|Zustände]] oder spezifischen [[Voraussetzung|Voraussetzungen]], die erfüllt sein müssen, bevor ein Aufruf einer [[Operation]] oder ein [[Use-Case]]-Schritt ausgeführt werden kann. Sie legt fest, unter welchen [[Voraussetzung|Voraussetzungen]] eine [[Methode]] oder [[Systemoperation]] zulässig ist, um [[Korrektheit]] und [[Robustheit]] des [[System|Systems]] zu gewährleisten.
- **Nutzen & Zweck:** Vorbedingungen verhindern unerwartetes [[Verhalten]] oder [[Fehler]] durch unsachgemäße Nutzung von [[Operation|Operationen]], indem sie die Anforderungen an den [[Systemzustand]] explizit machen. Sie fördern die [[Konsistenz]] und [[Korrektheit]] des [[System|Systems]], reduzieren Missverständnisse zwischen [[Entwickler|Entwicklern]], [[Analyst|Analysten]] und [[Stakeholder|Stakeholdern]] und helfen, [[Fehler]] frühzeitig zu erkennen. Zudem tragen sie zur [[Dokumentation]] bei, indem sie die [[Schnittstelle|Schnittstellen]] von [[Operation|Operationen]] klar definieren, die [[Wartbarkeit]] erhöhen und die [[Debugging]]-Fähigkeit verbessern. Durch die explizite Festlegung von [[Voraussetzung|Voraussetzungen]] wird die [[Vorhersehbarkeit]] des [[System|Systems]] gesteigert und die [[Robustheit]] gegenüber ungültigen [[Eingabe|Eingaben]] oder falschen [[Systemzustand|Systemzuständen]] gestärkt.
- **Abgrenzung & Grenzen:** Im Gegensatz zu [[Nachbedingung|Nachbedingungen]], die den [[Zustand]] nach Ausführung einer [[Operation]] beschreiben, legen [[Vorbedingung|Vorbedingungen]] ausschließlich die [[Voraussetzung|Voraussetzungen]] für deren Ausführung fest. Sie sind keine [[Ausnahmebehandlung|Ausnahmebehandlungen]], die [[Fehler]] während der Ausführung abfangen, und sollten nicht mit technischen Implementierungsdetails oder dynamischen [[Zustand|Zuständen]] verwechselt werden, die schwer prüfbar sind. [[Vorbedingung|Vorbedingungen]] eignen sich nicht für die Beschreibung von [[Benutzerinteraktion|Benutzerinteraktionen]] oder [[Workflow|Workflows]], sondern ausschließlich für technische oder logische [[Voraussetzung|Voraussetzungen]]. In Fällen, in denen der [[Zustand]] dynamisch, schwer zu validieren oder mit hohen [[Performance]]-Einbußen verbunden ist (z. B. in [[Echtzeitsystem|Echtzeitsystemen]]), können sie unpraktikabel sein. Zudem sind sie nicht geeignet, um externe [[Fehlerquelle|Fehlerquellen]] wie [[Netzwerkproblem|Netzwerkprobleme]] oder [[Benutzereingabe|Benutzereingaben]] zu validieren, die durch separate Mechanismen wie [[Exception-Handling]] abgedeckt werden sollten. [[Assertion|Assertions]], die lediglich zur [[Entwicklungszeit]] überprüft werden, unterscheiden sich ebenfalls von [[Vorbedingung|Vorbedingungen]], die zur Laufzeit geprüft werden müssen.
- **Beispiel / Code:** ```java
/**
 * Vorbedingung: Das System muss initialisiert sein.
 * @param token Ein gültiges Authentifizierungstoken.
 * @throws SystemNotInitializedException Falls das System nicht initialisiert ist.
 * @throws IllegalStateException Falls das Mitglied nicht ausgewählt oder nicht authentifiziert ist.
 */
public void manageMembers(Token token) {
    // Vorbedingung 1: System muss initialisiert sein
    if (!system.isInitialized()) {
        throw new SystemNotInitializedException("System nicht initialisiert.");
    }
    
    // Vorbedingung 2: Mitglied muss ausgewählt und authentifiziert sein
    if (currentMember == null || !currentMember.isAusgewaehlt() || !authentifiziert) {
        throw new IllegalStateException("Vorbedingung verletzt: Mitglied nicht ausgewählt oder nicht authentifiziert.");
    }
    
    // Weitere Logik zur Verwaltung der Mitglieder...
}

/**
 * Hebt einen Betrag vom Konto ab.
 * @param betrag Der abzuhebende Betrag (muss positiv sein).
 * @throws IllegalArgumentException Wenn der Betrag negativ ist oder das Konto überzogen würde.
 */
public class Bankkonto {
    private double kontostand;
    
    public void abheben(double betrag) {
        // Vorbedingung: Betrag muss positiv sein und Kontostand ausreichend
        if (betrag <= 0) {
            throw new IllegalArgumentException("Betrag muss positiv sein.");
        }
        if (kontostand < betrag) {
            throw new IllegalArgumentException("Kontostand nicht ausreichend.");
        }
        kontostand -= betrag;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 3a
- **Vorgänger / Parent:** [[Systemoperationen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Systemoperationen]]
  - [[Nachbedingungen]]
