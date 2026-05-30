---
id: 688e9e2e-1940-473e-8d34-93db06ba7151
title: "Protokoll-Automat"
date: 2026-05-30
tags:
  - software_engineering
  - modellierung
  - zustandsmaschine
  - formale_methode
  - systemmodellierung
  - verhaltensmodellierung
  - systemdesign
  - draft
source: "SWE Slides (Folien 271-285)"
---

# [[Protokoll-Automat]]

- **Kernkonzept:** Ein [[Protokoll-Automat]] (auch [[Zustandsautomat|Zustandsautomaten]] oder spezielle Form der [[Zustandsmaschine]]) ist ein [[formales_Modell|formales Modell]] zur Beschreibung von [[Zustand|Zuständen]] und [[Übergang|Übergängen]] in einem [[System]], das durch [[Ereignis|Ereignisse]] gesteuert wird. Er modelliert [[Systemoperation|Systemoperationen]] und definiert [[Vor- und Nachbedingungen]] für deren Ausführung, um das [[Systemverhalten]] explizit und nachvollziehbar zu gestalten, insbesondere in der [[Kommunikationsprotokoll|Kommunikationsprotokoll]]-Modellierung und bei [[Echtzeitsystem|Echtzeitsystemen]].
- **Nutzen & Zweck:** Der [[Protokoll-Automat]] ermöglicht die formale [[Beschreibung]] von [[Zustand|Zustandsänderungen]] und [[Verhalten]] in [[Systemen]], um [[Korrektheit]], [[Vorhersehbarkeit]], [[Konsistenz]] und [[Robustheit]] zu gewährleisten. Er löst das Problem unklarer [[Schnittstelle|Schnittstellen]] und [[Zustand|Zustände]], indem er explizit festlegt, wann welche [[Operation|Operationen]] aufgerufen werden dürfen. Dadurch dient er als Grundlage für [[Testfall|Testfälle]], [[Implementierung]], die Beherrschung von [[Komplexität]] in der [[Systemmodellierung]] sowie die Spezifikation von [[Protokoll|Protokollen]] und [[Echtzeitsystem|Echtzeitsystemen]], wo klare [[Zustand|Zustandsübergänge]] essenziell sind.
- **Abgrenzung & Grenzen:** Der [[Protokoll-Automat]] kann bei [[Systemen]] mit sehr vielen oder unvorhersehbaren [[Zustand|Zuständen]] unübersichtlich werden und ist daher nicht für alle [[Systemmodellierung|Modellierungsaufgaben]] geeignet. Alternativen wie [[Petri-Netz|Petri-Netze]] oder [[Aktivitätsdiagramm|Aktivitätsdiagramme]] eignen sich besser für [[Systeme]] mit kontinuierlichen [[Zustand|Zuständen]] oder komplexen [[Ereignis|Ereignisfolgen]]. Zudem ist er nicht geeignet für [[Systeme]], bei denen [[Operation|Operationen]] zustandsunabhängig sind – hier reichen einfache [[Schnittstelle|Schnittstellen]] oder [[Funktionsaufruf|Funktionsaufrufe]]. Die [[Abstraktion]] der [[Zustand|Zustände]] und [[Übergang|Übergänge]] ist entscheidend, um die Handhabbarkeit zu gewährleisten, da eine zu detaillierte Modellierung die [[Komplexität]] erhöhen kann.
- **Beispiel / Code:** ```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Verbunden: Verbinden
    Verbunden --> Idle: Trennen
    Verbunden --> Datenübertragung: Senden
    Datenübertragung --> Verbunden: Abschluss

    note right of Datenübertragung
        Beispiel für einen einfachen [[Protokoll-Automat|Protokoll-Automaten]]
        mit [[Zustand|Zuständen]] und [[Übergang|Übergängen]].
    end note
```

```java
// Beispiel-Implementierung eines [[Protokoll-Automat|Protokoll-Automaten]] in Java
public enum Zustand {
    IDLE, VERBUNDEN, DATENUEBERTRAGUNG, INITIALIZED
}

public class ProtokollAutomat {
    private Zustand aktuellerZustand = Zustand.IDLE;

    public void initialisieren() {
        if (aktuellerZustand == Zustand.IDLE) {
            aktuellerZustand = Zustand.INITIALIZED;
        }
    }

    public void verbinden() {
        if (aktuellerZustand == Zustand.INITIALIZED || aktuellerZustand == Zustand.IDLE) {
            aktuellerZustand = Zustand.VERBUNDEN;
        }
    }

    public void trennen() {
        if (aktuellerZustand == Zustand.VERBUNDEN) {
            aktuellerZustand = Zustand.IDLE;
        }
    }

    public void senden() {
        if (aktuellerZustand == Zustand.VERBUNDEN) {
            aktuellerZustand = Zustand.DATENUEBERTRAGUNG;
        }
    }

    public void abschluss() {
        if (aktuellerZustand == Zustand.DATENUEBERTRAGUNG) {
            aktuellerZustand = Zustand.VERBUNDEN;
        }
    }

    public void manageMembers(Token token) {
        if (aktuellerZustand != Zustand.INITIALIZED) {
            throw new IllegalStateException("System nicht initialisiert");
        }
        // Operation ausführen...
    }
}
```
