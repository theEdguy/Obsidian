---
id: 0a57497e-b063-439d-acf8-ec7dfc74a3e5
title: "Guard-Condition"
date: 2026-06-23
tags:
  - software_engineering
  - verhaltensmodellierung
  - systemdesign
  - bedingung
  - zustand
  - automat
  - draft
source: "software_engineering_kapitel_12"
---

# [[Guard-Condition]]

- **Kernkonzept:** Eine [[Guard-Condition]] ist ein boolescher Ausdruck, der an [[Transition|Transitionen]] in [[Zustandsmaschine|Zustandsmaschinen]] oder [[Protokollautomat|Protokollautomaten]] geknüpft ist und definiert, unter welchen [[Bedingung|Bedingungen]] ein [[Event]] einen Zustandsübergang auslösen darf. Sie steuert die Zulässigkeit von [[Transition|Transitionen]] basierend auf dem aktuellen [[Systemzustand]] oder Parametern der [[Systemoperation|Systemoperationen]].
- **Nutzen & Zweck:** [[Guard-Condition|Guard-Conditions]] ermöglichen die präzise Steuerung von [[Transition|Transitionen]] in komplexen [[System|Systemen]], indem sie sicherstellen, dass [[Operation|Operationen]] nur dann ausgeführt werden, wenn alle Voraussetzungen erfüllt sind. Dadurch erhöhen sie die [[Robustheit]], [[Vorhersagbarkeit]] und [[Konsistenz]] des [[Systems]] und verhindern unerwünschte Zustandswechsel. Zudem machen sie die Logik von [[Zustandsmaschine|Zustandsmaschinen]] und [[Protokollautomat|Protokollautomaten]] explizit und nachvollziehbar, was die [[Wartbarkeit]] und [[Dokumentation]] verbessert. In [[Event-gesteuertes_System|Event-gesteuerten Systemen]] tragen sie zur [[Sicherheit]] bei, indem sie unerlaubte oder unsichere [[Zustandsübergang|Zustandsübergänge]] blockieren.
- **Abgrenzung & Grenzen:** [[Guard-Condition|Guard-Conditions]] sind nicht erforderlich, wenn alle [[Transition|Transitionen]] bedingungslos ausgeführt werden sollen oder die [[Zustandslogik]] trivial ist. Eine übermäßige oder zu komplexe Verwendung kann die [[Lesbarkeit]] und [[Wartbarkeit]] des [[Modell|Modells]] beeinträchtigen, insbesondere wenn die [[Bedingung|Bedingungen]] schwer nachvollziehbar sind. Alternativ können Vor- und Nachbedingungen direkt in der Implementierung der [[Systemoperation|Systemoperationen]] geprüft werden, was jedoch die [[Zustandslogik]] verteilt und weniger transparent macht. Im Gegensatz zu einfachen [[If-Bedingung|If-Bedingungen]] sind [[Guard-Condition|Guard-Conditions]] direkt in das [[Zustandsmodell]] integriert und formalisieren die Semantik von [[Zustandsübergang|Zustandsübergängen]], statt nur lokale Entscheidungen zu treffen.
- **Beispiel / Code:** ```java
// Beispiel 1: Guard-Condition in einer Prüfungs-Zustandsmaschine
transition([[Event|Event]].PRUEFUNG_BEGINNEN) [versucheVerfuegbar > 0] /
    versucheVerfuegbar--;

// Beispiel 2: Guard-Condition in einem Protokollautomaten für Benutzeroberflächen
rightMouseDown(location) [location.inWindow() && isEditable] /
    selectedObject = pickObject(location);
    selectedObject.highlight();
```

Im ersten Beispiel wird die [[Transition]] nur ausgeführt, wenn noch Versuche verfügbar sind. Im zweiten Beispiel erfolgt die [[Transition]] nur, wenn der Mausklick innerhalb des Fensters liegt **und** das Objekt editierbar ist. Die [[Guard-Condition|Guard-Conditions]] `[versucheVerfuegbar > 0]` bzw. `[location.inWindow() && isEditable]` entscheiden über die Zulässigkeit der [[Zustandsübergang|Zustandsübergänge]].

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3b
- **Vorgänger / Parent:** [[Protokoll-Automaten]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Protokoll-Automaten]]
  - [[Zustandsübergänge]]
