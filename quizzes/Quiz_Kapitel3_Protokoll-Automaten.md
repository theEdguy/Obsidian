---
type: quiz
chapter: 3
subtopic: "Protokoll-Automaten"
format: callout
generated_at: 2026-06-06 16:28:43
tags:
  - software_engineering
  - quiz
  - chapter_3
---

# 🧠 Quiz: Protokoll-Automaten

**Kapitel:** Kapitel 3: Design – Softwarearchitektur & Entwurfsmuster
**Details:** (Zustandsmaschinen / State Machines)

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zu **Protokoll-Automaten / Zustandsmaschinen** im geforderten Format:

---

> [!question] **Frage 1: Welche Aussage beschreibt korrekt die Rolle von Vor- und Nachbedingungen in einem Protokoll-Automaten?**
> - [ ] A) Vorbedingungen definieren die Menge der Zustände *nach* Ausführung einer Operation, Nachbedingungen die Menge der Zustände *vor* der Ausführung.
> - [ ] B) Vorbedingungen und Nachbedingungen sind identisch und beschreiben nur die erlaubten Systemoperationen.
> - [ ] C) Vorbedingungen spezifizieren die Menge der Zustände, in denen ein Aufruf einer Systemoperation *zulässig* ist, Nachbedingungen die Menge der Zustände, die *nach* der Operation eingenommen werden.
> - [ ] D) Vor- und Nachbedingungen sind optional und dienen nur der Dokumentation, haben aber keine Auswirkung auf die Zustandsübergänge.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> - **Vorbedingungen** (Preconditions) legen fest, *in welchen Zuständen* eine Operation aufgerufen werden darf (z. B. "Nur im Zustand `LoggedIn` darf `logout()` aufgerufen werden").
> - **Nachbedingungen** (Postconditions) beschreiben die *Zustandsänderungen* nach Ausführung der Operation (z. B. "Nach `logout()` wechselt das System in den Zustand `LoggedOut`").
> - Option A ist falsch, weil die Definitionen vertauscht sind.
> - Option B ist falsch, da Vor- und Nachbedingungen unterschiedliche Zwecke haben.
> - Option D ist falsch, weil beide Bedingungen *kausal* für die Zustandsübergänge sind.

---

> [!question] **Frage 2: Welche der folgenden Aussagen trifft auf die Implementierung eines Protokoll-Automaten in der Software-Architektur zu?**
> - [ ] A) Protokoll-Automaten sollten *implizit* in der Geschäftslogik verborgen bleiben, um Flexibilität zu erhöhen.
> - [ ] B) Die Zustände werden typischerweise in einer *zentralen Klasse* (z. B. `StateMachineImpl`) verwaltet, während die Systemoperationen in den jeweiligen Komponenten implementiert sind.
> - [ ] C) Protokoll-Automaten eignen sich nur für *sequenzielle* Systeme und scheitern bei parallelen Abläufen.
> - [ ] D) Die Observer-Schnittstelle (wie im MVC-Pattern) ist ungeeignet für die Kommunikation zwischen Protokoll-Automaten und anderen Komponenten.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - **Option B** entspricht der Vorlesungsinhalten (vgl. Folien 376–388): Die `StateMachineImpl` verwaltet den aktuellen Zustand (`currentState`), während die *Systemoperationen* (z. B. `login()`, `logout()`) in den jeweiligen Komponenten (z. B. `UserService`) implementiert sind. Die Zustandsmaschine bietet eine *Schnittstelle* für diese Operationen.
> - **Option A** ist falsch, weil Protokoll-Automaten *explizit* modelliert werden müssen, um die Ablauflogik klar zu definieren (vgl. Folie 196–210).
> - **Option C** ist falsch, da Protokoll-Automaten durchaus für *parallele Systeme* erweitert werden können (z. B. durch hierarchische oder nebenläufige Zustandsmaschinen).
> - **Option D** ist falsch, weil der Observer-Mechanismus (wie in Folie 264 gezeigt) eine gängige Methode ist, um Zustandsänderungen an andere Komponenten (z. B. Views) zu propagieren.

---

> [!question] **Frage 3: Welche der folgenden Aktionen entspricht einem *Trigger* in einem Protokoll-Automaten?**
> - [ ] A) Die Änderung eines Attributs in der Datenbank.
> - [ ] B) Der Aufruf einer Systemoperation (z. B. `right-mouse-down(location)`), die im Protokoll definiert ist.
> - [ ] C) Ein Zeitüberschreitungsevent (Timeout) in einem Netzwerkprotokoll.
> - [ ] D) Die manuelle Eingabe eines Benutzers in ein Textfeld.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - Ein **Trigger** in einem Protokoll-Automaten ist definiert als *Aufruf einer Systemoperation*, die im zu modellierenden Protokoll erlaubt ist (vgl. Folie 271–285: "Trigger: Aufruf einer Systemoperation im zu modellierenden Protokoll").
> - **Option B** beschreibt genau diesen Fall (`right-mouse-down(location)` als Systemoperation).
> - **Option A** ist falsch, weil Attributänderungen in der Datenbank *keine* Systemoperationen des Protokolls sind.
> - **Option C** ist ein *Event*, aber kein Trigger im Sinne eines Protokoll-Automaten (es sei denn, es ist explizit als Systemoperation modelliert).
> - **Option D** ist zu allgemein – nur wenn die Eingabe als Systemoperation (z. B. `submitForm()`) definiert ist, wäre es ein Trigger.

---
> [!question] **Frage 4: Welche Aussage zur Abgrenzung von Protokoll-Automaten gegenüber klassischen Zustandsdiagrammen ist *falsch*?**
> - [ ] A) Protokoll-Automaten modellieren *nur die erlaubten Zustandsübergänge* für ein spezifisches Protokoll, während klassische Zustandsdiagramme alle möglichen Zustände eines Systems abbilden.
> - [ ] B) Protokoll-Automaten verwenden *Vorbedingungen und Nachbedingungen* zur präzisen Definition von Zustandsübergängen, klassische Zustandsdiagramme nicht.
> - [ ] C) Protokoll-Automaten sind eine *spezielle Form* von Zustandsdiagrammen, die sich auf die Ablauflogik von Systemoperationen konzentrieren.
> - [ ] D) Protokoll-Automaten und klassische Zustandsdiagramme unterscheiden sich nicht in ihrer Implementierung, sondern nur in der Notation.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: D**
>
> *Erklärung*:
> - **Option D** ist falsch, weil Protokoll-Automaten *konzeptionell und implementatorisch* anders sind:
      - Sie fokussieren sich auf *Protokolle* (d. h. erlaubte Sequenzen von Systemoperationen) und nutzen Vor-/Nachbedingungen zur präzisen Spezifikation (vgl. Folien 256–270).
      - Klassische Zustandsdiagramme (z. B. UML) modellieren *alle* möglichen Zustände und Übergänge eines Systems, unabhängig von Protokollen.
    - **Option A** ist korrekt, da Protokoll-Automaten die Ablauflogik *einschränken* (nur erlaubte Operationen in bestimmten Zuständen).
    - **Option B** ist korrekt (Protokoll-Automaten nutzen Bedingungen explizit).
    - **Option C** ist korrekt, da Protokoll-Automaten eine *Teilmenge* von Zustandsdiagrammen sind.

---
> [!question] **Frage 5: Welche der folgenden Implementierungsstrategien für Protokoll-Automaten ist *nicht* mit den Vorlesungsinhalten vereinbar?**
> - [ ] A) Verwendung einer *Zustandsvariable* (`currentState`) in einer Klasse `StateMachineImpl`, die durch Systemoperationen (z. B. `login()`, `logout()`) aktualisiert wird.
> - [ ] B) Direkte Integration der Zustandslogik in die *Geschäftslogik-Klassen* (z. B. `UserService`), um die Kopplung zwischen Komponenten zu minimieren.
> - [ ] C) Nutzung des *Observer-Patterns*, um Zustandsänderungen an abhängige Komponenten (z. B. Views) zu propagieren.
> - [ ] D) Modellierung der Zustände als *Enum* und Verwaltung der Übergänge in einer zentralen `StateMachine`-Klasse.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - **Option B** ist *nicht vereinbar* mit den Vorlesungsinhalten:
      - Protokoll-Automaten sollen die Zustandsverwaltung *zentralisieren* (z. B. in `StateMachineImpl`), um die Ablauflogik klar von der Geschäftslogik zu trennen (vgl. Folien 376–388).
      - Eine *dezentrale* Integration der Zustandslogik in `UserService` oder ähnlichen Klassen führt zu *hoher Kopplung* und widerspricht dem Prinzip der expliziten Zustandsmaschine.
    - **Option A** ist korrekt (zentrale Zustandsverwaltung).
    - **Option C** ist korrekt (Observer-Pattern wird explizit in Folie 264 erwähnt).
    - **Option D** ist korrekt (Enum-basierte Zustände sind eine gängige Implementierung, z. B. `State.S.Login`).

---
Das Quiz deckt folgende Schlüsselkonzepte ab:
1. Vor-/Nachbedingungen in Protokoll-Automaten
2. Architekturprinzipien (zentrale vs. dezentrale Zustandsverwaltung)
3. Definition von Triggern
4. Abgrenzung zu klassischen Zustandsdiagrammen
5. Implementierungsstrategien (Observer, Enum, etc.)

Die Fragen erfordern **Anwendung** (z. B. Szenarien bewerten) und **Analyse** (z. B. Konzepte abgrenzen), wie im akademischen Kontext gefordert.