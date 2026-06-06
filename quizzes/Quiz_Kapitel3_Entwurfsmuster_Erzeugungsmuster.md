---
type: quiz
chapter: 3
subtopic: "Entwurfsmuster: Erzeugungsmuster"
format: callout
generated_at: 2026-06-06 16:29:09
tags:
  - software_engineering
  - quiz
  - chapter_3
---

# 🧠 Quiz: Entwurfsmuster: Erzeugungsmuster

**Kapitel:** Kapitel 3: Design – Softwarearchitektur & Entwurfsmuster
**Details:** (Fabriken / Factories, etc.)

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zu Erzeugungsmustern (Fabriken) im geforderten Format:

---

> [!question] **Frage 1: Welches der folgenden Ziele wird durch die Anwendung von Erzeugungsmustern (wie Fabrikmethode oder Abstrakte Fabrik) primär verfolgt?**
> - [ ] A) Vermeidung von Code-Duplikaten durch zentrale Fehlerbehandlung
> - [ ] B) Verbesserung der Laufzeitperformance durch optimierte Speichernutzung
> - [ ] C) Förderung der Wiederverwendung von Entwürfen und Entkopplung von Client-Code und konkreten Klassen
> - [ ] D) Automatische Generierung von Dokumentation aus dem Quellcode

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> Erzeugungsmuster wie die **Fabrikmethode** oder **Abstrakte Fabrik** dienen der **Entkopplung** des Client-Codes von der konkreten Implementierung der zu erzeugenden Objekte. Dies ermöglicht:
> - **Wiederverwendung** bewährter Entwürfe (Gamma et al.)
> - **Flexibilität** durch Austauschbarkeit konkreter Klassen
> - **Verständlichkeit** durch klare Schnittstellen (Standardvokabular)
> Die anderen Optionen beschreiben Ziele anderer Muster (z. B. AOP für Fehlerbehandlung, B für Performance-Optimierung, D für Dokumentationsgenerierung).

---

> [!question] **Frage 2: Ein Framework nutzt die Fabrikmethode, um verschiedene UI-Komponenten (z. B. `Button`, `TextField`) zu erzeugen. Welche Aussage trifft auf die Rolle des `Erzeuger`-Elements (Factory) in diesem Kontext zu?**
> - [ ] A) Der `Erzeuger` implementiert die konkreten UI-Komponenten direkt (z. B. `Button` mit Windows-Stil).
> - [ ] B) Der `Erzeuger` definiert eine abstrakte Methode `erzeugeKomponente()`, die von Unterklassen überschrieben wird.
> - [ ] C) Der `Erzeuger` ist für die grafische Darstellung der Komponenten verantwortlich.
> - [ ] D) Der `Erzeuger` verwaltet eine Liste aller erzeugten Komponenten zur Laufzeit.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> Die **Fabrikmethode** (Factory Method) folgt dem Prinzip:
> - Der `Erzeuger` (Factory) definiert eine **abstrakte Methode** (z. B. `erzeugeKomponente()`), die von **Unterklassen** implementiert wird.
> - Der Client arbeitet nur mit der abstrakten Schnittstelle (`AbstraktesProdukt`), während die konkrete Erzeugung in den Unterklassen erfolgt.
> - **Option A** ist falsch, da der `Erzeuger` keine konkreten Klassen instanziiert (das übernimmt die Unterklasse).
> - **Option C** beschreibt eine andere Verantwortung (z. B. eines Renderers).
> - **Option D** ist kein typisches Merkmal der Fabrikmethode (hier wäre z. B. ein `ObjectPool` zuständig).

---
> [!question] **Frage 3: Welches der folgenden Szenarien ist ein typischer Anwendungsfall für die **Abstrakte Fabrik (Abstract Factory)**?**
> - [ ] A) Ein Texteditor soll zur Laufzeit zwischen verschiedenen Betriebssystem-Stilen (Windows/macOS/Linux) wechseln können.
> - [ ] B) Ein Datenbank-Client soll automatisch zwischen MySQL und PostgreSQL umschalten, wenn eine Verbindung fehlschlägt.
> - [ ] C) Ein Spiel soll zufällig Gegner-Charaktere mit unterschiedlichen Fähigkeiten generieren.
> - [ ] D) Ein Compiler soll während der Kompilierung temporäre Dateien für die Zwischenspeicherung nutzen.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: A**
>
> *Erklärung*:
> Die **Abstrakte Fabrik** wird eingesetzt, wenn:
> - **Familien verwandter Objekte** (hier: UI-Komponenten für ein Betriebssystem) **konsistent** erzeugt werden müssen.
> - Der Client **unabhängig** von der konkreten Implementierung arbeiten soll (z. B. Wechsel zwischen `WindowsFactory` und `MacOSFactory`).
> - **Beispiel**: Ein Framework wie Java Swing nutzt abstrakte Fabriken, um plattformspezifische Look-and-Feel-Komponenten zu erzeugen.
> - **Option B** beschreibt eher ein **Strategie-Muster** (Datenbank-Adapter).
> - **Option C** wäre ein **Fabrikmethode**-Szenario (einfache Objektgenerierung).
> - **Option D** ist ein **Prototyp-Muster**-Anwendungsfall (Klonen von Objekten).

---
> [!question] **Frage 4: Welcher der folgenden Nachteile ist **typisch für die Abstrakte Fabrik**, aber **nicht für die einfache Fabrikmethode**?**
> - [ ] A) Erhöhte Komplexität durch zusätzliche Abstraktionsschichten.
> - [ ] B) Starke Kopplung zwischen Client und konkreten Produkten.
> - [ ] C) Unfähigkeit, neue Produkttypen zur Laufzeit hinzuzufügen.
> - [ ] D) Notwendigkeit, alle Produktfamilien vorab zu definieren.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: D**
>
> *Erklärung*:
> **Abstrakte Fabrik vs. Fabrikmethode**:
> - **Abstrakte Fabrik**:
>   - Erzeugt **Familien verwandter Objekte** (z. B. alle UI-Komponenten für ein OS).
>   - **Nachteil**: Neue Produktfamilien erfordern **Änderungen an der abstrakten Fabrik und allen konkreten Fabriken** (Open/Closed-Prinzip verletzt).
>   - **Option D** ist korrekt, da die Produktfamilien (z. B. `Button`, `TextField`) in der abstrakten Schnittstelle fest definiert sein müssen.
> - **Fabrikmethode**:
>   - Erzeugt **einzelne Objekte** und ist flexibler für neue Produkttypen (nur Unterklasse muss angepasst werden).
> - **Option A** ist ein Nachteil beider Muster.
> - **Option B** ist falsch, da beide Muster die Kopplung reduzieren.
> - **Option C** trifft auf beide Muster zu (neue Produkttypen erfordern Anpassungen).

---
> [!question] **Frage 5: Ein Entwickler möchte ein Plugin-System entwerfen, bei dem Plugins zur Laufzeit geladen und ihre Objekte erzeugt werden. Welches Erzeugungsmuster eignet sich **am besten**, um die Plugins von der Hauptanwendung zu entkoppeln?**
> - [ ] A) Singleton
> - [ ] B) Abstrakte Fabrik
> - [ ] C) Fabrikmethode
> - [ ] D) Prototype

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> **Fabrikmethode** ist ideal für Plugin-Systeme, weil:
> - Der **Client** (Hauptanwendung) arbeitet mit einer **abstrakten Schnittstelle** (`Plugin`).
> - Die **konkrete Erzeugung** wird an die **Plugin-Implementierungen** delegiert (z. B. über `PluginFactory`).
> - **Vorteile**:
>   - Plugins können **unabhängig entwickelt** und zur Laufzeit geladen werden.
>   - Keine Notwendigkeit, alle Plugin-Typen vorab zu kennen (im Gegensatz zur Abstrakten Fabrik).
> - **Option A (Singleton)**: Wird für globale Zugriffspunkte genutzt, nicht für Objektgenerierung.
> - **Option B (Abstrakte Fabrik)**: Überkill, wenn nur einzelne Objekte erzeugt werden müssen.
> - **Option D (Prototype)**: Würde Klonen erfordern (ineffizient für Plugins mit komplexen Zuständen).

---
Das Quiz deckt die Kernkonzepte der Vorlesung ab (Gamma et al., Prof. Fuchß) und prüft sowohl theoretisches Verständnis als auch praktische Anwendungsszenarien. Die Distraktoren sind so gewählt, dass sie häufige Missverständnisse oder alternative Muster betreffen.