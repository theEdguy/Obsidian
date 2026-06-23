---
id: b79737d4-6840-4e25-bef1-26429632719c
title: "Dynamisches Modell"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - uml
  - draft
source: "software_engineering_kapitel_09"
---

# [[Dynamisches Modell]]

- **Kernkonzept:** Das dynamische Modell im Software-Engineering beschreibt die zeitlichen Abläufe, Interaktionen und Zustandsänderungen von Objekten innerhalb eines Systems. Es visualisiert, wie Systemkomponenten zur Laufzeit zusammenwirken, um Use Cases umzusetzen.
- **Nutzen & Zweck:** Das dynamische Modell dient dazu, die funktionalen Anforderungen eines Systems in konkrete Abläufe zu übersetzen und Schnittstellen zwischen Objekten zu identifizieren. Es löst das Problem, dass statische Modelle (wie Klassen- oder Objektdiagramme) keine Aussagen über das Verhalten zur Laufzeit treffen können. Dadurch wird sichergestellt, dass alle notwendigen Operationen und Interaktionen erfasst werden, bevor mit dem Design begonnen wird.
- **Abgrenzung & Grenzen:** Das dynamische Modell sollte nicht genutzt werden, um strukturelle Aspekte des Systems (z. B. Klassenhierarchien oder Attribute) zu definieren – hierfür sind statische Modelle wie Klassendiagramme besser geeignet. Es unterscheidet sich von Zustandsdiagrammen, die sich auf den Lebenszyklus eines einzelnen Objekts konzentrieren, während das dynamische Modell die Interaktion *mehrerer* Objekte abbildet. Zudem ist es kein Ersatz für detaillierte Implementierungsvorgaben, sondern dient der Analysephase.
- **Beispiel / Code:** ```java
// Beispiel: System-Sequenzdiagramm (textuelle Notation) für den Use Case "Mitglied verlässt Abteilung"
actor Vereinsmanager
participant System
participant Mitglied
participant Abteilung

Vereinsmanager -> System: abteilungVerlassen(mitgliedID, abteilungID)
System -> Mitglied: prüfeMitgliedschaft(abteilungID)
alt Mitglied gehört zur Abteilung
    System -> Abteilung: entferneMitglied(mitgliedID)
    System -> Mitglied: setzeStatus("passiv", falls keine Abteilung mehr)
    System -> Mitglied: sendeBenachrichtigung()
else
    System --> Vereinsmanager: Fehler("Mitglied nicht in Abteilung")
end
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2c
- **Vorgänger / Parent:** [[Objektorientierte_Analyse]]
- **Folgezettel / Unterzettel:**
  - [[Zustandsübergangsdiagramm]]
  - [[Aktivitätsdiagramm]]
- **Querverweise:**
  - [[UML]]
  - [[Verhaltensmodellierung]]
