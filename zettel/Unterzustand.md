---
id: 5b76884e-2f4f-4e26-9db2-cda55cb14fb5
title: "Unterzustand"
date: 2026-05-30
tags:
  - software_engineering
  - zustandsmaschine
  - uml
  - entwurfsmuster
  - modellierung
  - hierarchische_abstraktion
  - draft
source: "Klausur_Referenz"
---

# [[Unterzustand]]

- **Kernkonzept:** Ein **Unterzustand** (engl. *substate*) ist ein Zustand innerhalb eines [[Zusammengesetzter_Zustand|zusammengesetzten Zustands]] in einer [[Zustandsmaschine]]. Er ermöglicht die Modellierung hierarchischer Zustandsstrukturen, indem ein übergeordneter Zustand in feingranularere Teilzustände unterteilt wird. Unterzustände erben dabei die Eigenschaften und Transitionen ihres übergeordneten Zustands, können aber zusätzlich eigene, spezifischere Zustandsübergänge und Aktionen definieren. Dies folgt dem Prinzip der [[Hierarchische_Zustandsmodellierung]] und unterstützt die Strukturierung komplexer Systeme.
- **Nutzen & Zweck:** Unterzustände dienen der **Modularisierung und Vereinfachung** von [[Zustandsmaschine|Zustandsmaschinen]], indem sie:
- **Komplexität reduzieren**: Durch die Gruppierung verwandter Zustände in einem übergeordneten Zustand (z. B. `aktiv` mit Unterzuständen `wählend`, `verbunden`, `haltend`).
- **Wiederverwendung fördern**: Gemeinsame Transitionen (z. B. `Timeout`) können auf Ebene des zusammengesetzten Zustands definiert werden und gelten für alle Unterzustände.
- **Lesbarkeit verbessern**: Die Hierarchie macht die Logik intuitiver (z. B. in [[UML-Zustandsdiagramme|UML-Zustandsdiagrammen]]).
- **History-Mechanismen unterstützen**: Wie im Kontext erwähnt, können [[History_State|History-States]] den letzten aktiven Unterzustand speichern, was z. B. bei Unterbrechungen (z. B. Telefonanruf) nützlich ist.

Typische Anwendungsfälle sind eingebettete Systeme (z. B. Gerätesteuerungen), Benutzeroberflächen (z. B. Dialogabläufe) oder Geschäftsprozesse (z. B. Bestellstatus mit Unterzuständen wie `Zahlung_prüfen`, `Versand_vorbereiten`).
- **Abgrenzung & Grenzen:** - **Keine Parallelität**: Unterzustände in einem zusammengesetzten Zustand sind *sequenziell* – nur ein Unterzustand ist gleichzeitig aktiv. Für parallele Zustände werden [[Orthogonale_Regionen]] benötigt.
- **Keine Vererbung im OOP-Sinn**: Unterzustände erben *keine Attribute oder Methoden*, sondern nur Transitionen und Ein-/Ausgangsaktionen des übergeordneten Zustands.
- **Stolperstein History-State**: Der [[History_State]] merkt sich nur die *direkten* Unterzustände, nicht tiefer verschachtelte Hierarchien. Bei mehrstufigen Zuständen muss dies explizit modelliert werden.
- **Keine Zyklen**: Unterzustände dürfen nicht rekursiv auf ihren übergeordneten Zustand verweisen (z. B. `S1 → S1.1 → S1`), da dies zu unendlichen Schleifen führen kann.
- **Granularität**: Zu tiefe Verschachtelung kann die Wartbarkeit erschweren – eine Balance zwischen Detaillierung und Übersichtlichkeit ist entscheidend.
- **Beispiel / Code:** {'beschreibung': 'UML-Zustandsdiagramm (textuell mit Mermaid-Syntax) für ein Telefon mit Unterzuständen im Zustand `aktiv`:\n\n```mermaid\nstateDiagram-v2\n    [*] --> inaktiv\n    inaktiv --> aktiv: abheben\n    aktiv --> inaktiv: auflegen\n    \n    state aktiv {\n        [*] --> wählend\n        wählend --> verbunden: Nummer_eingegeben\n        verbunden --> haltend: Halten\n        haltend --> verbunden: Weiter\n        verbunden --> wählend: Trennen\n        wählend --> [*]: Timeout\n    }\n```\n\n**Java-Implementierung (vereinfacht mit State-Pattern):**\n```java\npublic interface TelefonZustand {\n    void abheben(Telefon telefon);\n    void auflegen(Telefon telefon);\n    void nummerEingegeben(Telefon telefon, String nummer);\n}\n\npublic class AktivZustand implements TelefonZustand {\n    private TelefonZustand unterzustand;\n    \n    public AktivZustand() {\n        this.unterzustand = new WählendZustand(); // Initialer Unterzustand\n    }\n    \n    @Override\n    public void abheben(Telefon telefon) {\n        // Ignorieren, da bereits aktiv\n    }\n    \n    @Override\n    public void auflegen(Telefon telefon) {\n        telefon.setZustand(new InaktivZustand());\n    }\n    \n    @Override\n    public void nummerEingegeben(Telefon telefon, String nummer) {\n        unterzustand.nummerEingegeben(telefon, nummer);\n    }\n    \n    // Unterzustände als innere Klassen\n    private class WählendZustand implements TelefonZustand {\n        @Override\n        public void nummerEingegeben(Telefon telefon, String nummer) {\n            telefon.setZustand(new VerbundenZustand());\n        }\n        // ... weitere Methoden\n    }\n    \n    private class VerbundenZustand implements TelefonZustand {\n        @Override\n        public void auflegen(Telefon telefon) {\n            telefon.setZustand(new InaktivZustand());\n        }\n        // ... weitere Methoden\n    }\n}\n```', 'hinweis': 'Das Beispiel zeigt, wie Unterzustände durch Komposition im [[State_Pattern]] abgebildet werden können. Der `AktivZustand` delegiert spezifische Aktionen an seine Unterzustände (`WählendZustand`, `VerbundenZustand`).'}
