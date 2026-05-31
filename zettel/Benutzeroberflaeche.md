---
id: bbbee663-7a91-4d77-b2e3-0ae446482265
title: "Benutzeroberflaeche"
date: 2026-05-31
tags:
  - software_engineering
  - mensch_maschine_interaktion
  - use_case
  - gui_design
  - uml
  - softwarearchitektur
  - draft
source: "Klausur_Referenz"
---

# [[Benutzeroberflaeche]]

- **Kernkonzept:** Eine [[Benutzeroberflaeche]] (engl. *User Interface*, UI) ist die Schnittstelle zwischen Mensch und Maschine, die die Interaktion des Nutzers mit einem [[Softwaresystem]] ermöglicht. Sie umfasst alle visuellen, auditiven und haptischen Elemente, über die Nutzer Eingaben tätigen und Ausgaben des Systems wahrnehmen. Im Kontext von Software-Engineering liegt der Fokus auf grafischen Benutzeroberflächen (GUI), die durch [[Entwurfsmuster]] wie [[Model_View_Controller]] oder [[MVVM]] strukturiert werden können.
- **Nutzen & Zweck:** Die [[Benutzeroberflaeche]] dient der intuitiven und effizienten Steuerung von Anwendungen, indem sie komplexe Funktionalitäten durch interaktive Elemente (z. B. Schaltflächen, Menüs, Formulare) zugänglich macht. Sie verbessert die [[Usability]] und [[User_Experience]], reduziert Einarbeitungszeiten und minimiert Fehler durch klare Rückmeldungen (z. B. Validierungsfehler). Im [[Softwareentwicklungsprozess]] wird sie oft durch [[Use_Case_Diagramme]] oder [[Wireframes]] spezifiziert, um Anforderungen frühzeitig zu validieren.
- **Abgrenzung & Grenzen:** Eine [[Benutzeroberflaeche]] ist *nicht* gleichzusetzen mit der [[Geschäftslogik]] oder Datenhaltung – sie stellt lediglich die Präsentationsschicht dar. Typische Stolpersteine sind: (1) Vermischung von UI-Logik mit [[Domain_Logic]] (Verstoß gegen [[Separation_of_Concerns]]), (2) mangelnde Barrierefreiheit (z. B. fehlende Screenreader-Unterstützung), (3) inkonsistente Bedienmuster (z. B. unterschiedliche Shortcuts in einer Anwendung). Zudem sind plattformspezifische Unterschiede (z. B. mobile vs. Desktop-UIs) zu beachten, die durch [[Responsive_Design]] oder plattformübergreifende Frameworks (z. B. Flutter) adressiert werden können.
- **Beispiel / Code:** ```mermaid
useCaseDiagram
    actor Nutzer
    actor Entwickler
    
    Nutzer --> (Anwendung bedienen)
    Nutzer --> (Daten eingeben)
    Nutzer --> (Fehler melden)
    
    Entwickler --> (UI-Design anpassen)
    Entwickler --> (Use-Cases definieren)
    (Anwendung bedienen) <.. (Daten eingeben) : <<extends>>
    (Anwendung bedienen) <.. (Fehler melden) : <<extends>>
```

*Beispiel: Use-Case-Diagramm für eine App mit Fokus auf UI-Interaktionen (vgl. Klausurkontext).*
