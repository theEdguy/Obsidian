---
id: ab8b1832-c3a0-4e7d-92ac-88a4ad0b62f7
title: "Zustandsuebergang"
date: 2026-05-31
tags:
  - software_engineering
  - uml
  - zustandsmaschine
  - entwurfsmuster
  - systemmodellierung
  - verhaltensmodellierung
  - draft
source: "Klausur_Referenz"
---

# [[Zustandsuebergang]]

- **Kernkonzept:** Ein **Zustandsübergang** (engl. *state transition*) beschreibt in einer [[Zustandsmaschine]] den Wechsel von einem [[Zustand]] zu einem anderen, ausgelöst durch ein definiertes [[Ereignis]] (z. B. Benutzerinteraktion, Zeitablauf oder Systembedingung). Der Übergang ist gerichtet und kann mit Bedingungen (*Guards*), Aktionen oder Eintritts-/Austrittsverhalten verknüpft sein. In der [[UML]] wird er als Pfeil zwischen zwei Zuständen dargestellt, oft annotiert mit der Syntax `Ereignis[Guard]/Aktion`.
- **Nutzen & Zweck:** Zustandsübergänge ermöglichen die Modellierung dynamischer Systeme, deren Verhalten sich abhängig von internen oder externen Einflüssen ändert. Typische Anwendungsfälle:
- **Steuerung komplexer Abläufe**: z. B. in [[Entwurfsmuster|State_Pattern]] zur Kapselung zustandsabhängiger Logik.
- **Protokollimplementierung**: z. B. Netzwerkkommunikation (TCP-Handshake) oder Gerätesteuerung (wie im Beispiel Telefon).
- **Validierung von Systemverhalten**: Durch formale Spezifikation von Übergängen können Fehler wie unerreichbare Zustände oder Deadlocks früh erkannt werden.
- **Codegenerierung**: Tools wie [[UML]]-Modellierer können aus Zustandsdiagrammen direkt ausführbaren Code erzeugen (z. B. für Embedded-Systeme).
- **Abgrenzung & Grenzen:** - **Keine Zustandsänderung ohne Ereignis**: Ein Übergang erfolgt nur bei explizitem Auslöser (Ausnahme: *automatische Übergänge* mit Zeitbedingungen).
- **Determinismus vs. Nicht-Determinismus**: In deterministischen Zustandsmaschinen führt ein Ereignis in einem Zustand zu genau einem Folgezustand. Nicht-deterministische Übergänge (mehrere mögliche Folgezustände) erfordern zusätzliche Regeln (z. B. Priorisierung).
- **Granularität**: Übergänge können zwischen einfachen Zuständen oder [[Zusammengesetzte_Zustaende|zusammengesetzten Zuständen]] (mit Unterzuständen) erfolgen. Hier sind *History-States* (z. B. `[[History_State]]`) relevant, um den letzten Unterzustand wiederherzustellen.
- **Stolpersteine**: 
  - *Zyklische Übergänge*: Können zu Endlosschleifen führen (z. B. Zustand A → B → A).
  - *Fehlende Guards*: Ohne Bedingungen können unerwünschte Übergänge ausgelöst werden.
  - *Implizite Annahmen*: Übergänge sollten alle möglichen Ereignisse abdecken, um undefiniertes Verhalten zu vermeiden.
- **Beispiel / Code:** {'beschreibung': 'UML-Zustandsdiagramm für ein Telefon (vereinfacht) in Mermaid-Syntax:', 'mermaid': 'stateDiagram-v2\n    [*] --> Erzeugung_Initialisierung\n    Erzeugung_Initialisierung --> inaktiv: initialisiert\n    inaktiv --> aktiv: abheben\n    aktiv --> inaktiv: auflegen\n    state aktiv {\n        [*] --> Waehlen\n        Waehlen --> Klingeln: Nummer_gueltig\n        Waehlen --> Besetzt: Nummer_besetzt\n        Klingeln --> Gespraech: abgenommen\n        Gespraech --> [*]: auflegen\n    }\n    note right of aktiv\n        Zusammengesetzter Zustand mit\n        Unterzuständen (Waehlen, Klingeln,\n        Gespraech) und History-State.\n    end note'}
