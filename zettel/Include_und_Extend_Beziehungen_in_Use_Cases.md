---
id: 8717be93-95ba-497e-ae2a-ce842361b4b3
title: "Include_und_Extend_Beziehungen_in_Use_Cases"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - anforderungsanalyse
  - use_case_modellierung
  - softwareentwurf
  - modularisierung
  - draft
source: "Klausur_Referenz"
---

# [[Include_und_Extend_Beziehungen_in_Use_Cases]]

- **Kernkonzept:** In der [[Use_Case_Modellierung]] beschreiben *Include-* und *Extend-Beziehungen* spezifische Abhängigkeiten zwischen [[Use_Cases]]. 

1. **Include-Beziehung (`<<include>>`)**: Ein Use Case (Basis-Use-Case) *bindet einen anderen Use Case (eingebetteter Use Case) vollständig ein*. Die Ausführung des eingebetteten Use Cases ist *obligatorisch* und erfolgt immer, wenn der Basis-Use-Case ausgeführt wird. Beispiel: Ein Use Case `[[Bestellung_aufgeben]]` könnte den Use Case `[[Zahlung_abwickeln]]` via `<<include>>` einbinden, da jede Bestellung eine Zahlung erfordert.

2. **Extend-Beziehung (`<<extend>>`)**: Ein Use Case (erweiternder Use Case) *fügt optional zusätzliche Funktionalität* zu einem Basis-Use-Case hinzu, *falls eine definierte Bedingung* (am *Extension Point*) erfüllt ist. Der Basis-Use-Case bleibt funktionsfähig, auch wenn die Erweiterung nicht ausgeführt wird. Beispiel: Der Use Case `[[Gutschein_einlösen]]` könnte den Use Case `[[Bestellung_aufgeben]]` via `<<extend>>` erweitern, falls ein Gutschein vorhanden ist.

3. **Extension Point**: Ein markierter Punkt im Basis-Use-Case, an dem eine `<<extend>>`-Beziehung eingreifen kann. Er definiert, *wo* die Erweiterung stattfindet, und ist mit einer Bedingung verknüpft, die entscheidet, *ob* die Erweiterung ausgeführt wird.
- **Nutzen & Zweck:** Diese Beziehungen dienen der *Modularisierung* und *Wiederverwendung* von Use-Case-Logik in der [[Anforderungsanalyse]]:

- **Include**: Vermeidet Redundanz, indem gemeinsame Funktionalität zentralisiert wird (z. B. Authentifizierung in mehreren Use Cases).
- **Extend**: Ermöglicht die Modellierung *optionaler* oder *bedingter* Erweiterungen, ohne den Basis-Use-Case zu überladen. Dies fördert die *Wartbarkeit* und *Lesbarkeit* von [[Use_Case_Diagrammen]].

Typische Anwendungsfälle:
- **Include**: Wiederkehrende Teilprozesse (z. B. Login, Validierung).
- **Extend**: Sonderfälle (z. B. Rabatte, Fehlerbehandlungen).
- **Abgrenzung & Grenzen:** - **Verwechslungsgefahr**: `<<include>>` ist *obligatorisch* (wie ein Funktionsaufruf), `<<extend>>` ist *optional* (wie ein Hook).
- **Vererbung vs. Beziehungen**: Eine [[Vererbung]] zwischen Use Cases ist nur sinnvoll, wenn ein Use Case eine *spezialisierte Variante* eines anderen ist (z. B. `[[Premium_Bestellung]]` erbt von `[[Standard_Bestellung]]`). `<<include>>`/`<<extend>>` modellieren dagegen *Zusammensetzung* oder *Erweiterung*.
- **Extension Points**: Ohne klare Definition führen sie zu unklaren Bedingungen und schwer wartbaren Modellen. Sie sollten *explizit benannt* und dokumentiert werden.
- **Keine Implementierungsdetails**: Diese Beziehungen beschreiben *was* passiert, nicht *wie* (z. B. keine Algorithmen oder Datenstrukturen).
- **Missbrauch**: Zu viele `<<extend>>`-Beziehungen können das Modell unübersichtlich machen – besser ist oft eine Aufteilung in separate Use Cases.
- **Beispiel / Code:** {'uml_diagramm': '```mermaid\nuseCaseDiagram\n    actor Kunde\n    Kunde --> (Bestellung aufgeben)\n    (Bestellung aufgeben) ..> (Zahlung abwickeln) : <<include>>\n    (Gutschein einlösen) ..> (Bestellung aufgeben) : <<extend>>\n    note right of (Bestellung aufgeben)\n        Extension Point: "Gutschein prüfen"\n        Bedingung: Gutschein gültig\n    end note\n```', 'textuelle_beschreibung': '- **Include-Beispiel**: `Bestellung aufgeben` *muss* `Zahlung abwickeln` ausführen.\n- **Extend-Beispiel**: `Gutschein einlösen` *kann* `Bestellung aufgeben` erweitern, *falls* ein Gutschein vorhanden ist. Der Extension Point `"Gutschein prüfen"` entscheidet über die Ausführung.'}
