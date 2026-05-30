---
id: 468390a7-83b8-421a-9ca9-2a26aca8faeb
title: "Nachbedingung"
date: 2026-05-30
tags:
  - software_engineering
  - formale_methode
  - system_design
  - draft
source: "SWE Slides (Folien 256-270)"
---

# [[Nachbedingung]]

- **Kernkonzept:** Eine [[Nachbedingung]] definiert die Menge der [[Zustand|Zustände]], die nach der Ausführung einer [[Operation]] garantiert eintreten. Sie beschreibt das erwartete Ergebnis oder den neuen [[Systemzustand]].
- **Nutzen & Zweck:** Sie stellt sicher, dass eine [[Operation]] ihr Ziel erreicht und das [[System|System]] in einen definierten Zustand überführt. Dies ist essenziell für die [[Verifizierbarkeit]] und [[Testbarkeit]] von [[System|Systemen]].
- **Abgrenzung & Grenzen:** Im Gegensatz zu [[Vorbedingung|Vorbedingungen]] beschreibt eine [[Nachbedingung]] nicht die Voraussetzungen, sondern das Ergebnis einer [[Operation]]. Sie sollte nicht mit temporären oder internen [[Zustand|Zuständen]] verwechselt werden.
- **Beispiel / Code:** ```java
/**
 * Nachbedingung: Mitglieder können bearbeitet werden oder die Validierung ist fehlgeschlagen.
 */
public void manageMembers(Token token) {
    if (validateToken(token)) {
        assert membersEditable : "Mitglieder sollten bearbeitbar sein";
    } else {
        assert !membersEditable : "Validierung ist fehlgeschlagen";
    }
}
```
