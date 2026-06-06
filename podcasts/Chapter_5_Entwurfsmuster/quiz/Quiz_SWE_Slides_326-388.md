---
type: chapter_quiz
chapter: 5
range: "326-388"
generated_at: 2026-06-06 16:35:06
tags:
  - software_engineering
  - quiz
  - chapter_quiz_5
---

# 🧠 Chapter 5 Quiz: Entwurfsmuster

**Slide Range:** 326-388

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Grundprinzipien von Design-Patterns**
> Welche der folgenden Aussagen beschreibt **korrekt** das zentrale Prinzip von Design-Patterns nach Gamma et al.?
>
> - [ ] A) Design-Patterns ersetzen die Notwendigkeit von Unit-Tests, da sie bewährte Lösungen darstellen.
> - [ ] B) Design-Patterns ermöglichen es, Klassen direkt zu vererben und damit Implementierungsdetails festzulegen.
> - [ ] C) Design-Patterns fördern die Programmierung gegen Schnittstellen statt gegen Implementierungen und verbessern so Flexibilität und Wiederverwendbarkeit.
> - [ ] D) Design-Patterns sind nur für die Dokumentation von Entwurfsentscheidungen relevant und haben keinen Einfluss auf die Implementierung.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > Die Folien (Slide 329) betonen, dass Design-Patterns das Prinzip der Programmierung gegen Schnittstellen (Interfaces) statt gegen konkrete Implementierungen fördern. Dies ermöglicht Flexibilität, da Klienten nur die Schnittstelle kennen und nicht die konkreten Klassen. Option A ist falsch, da Design-Patterns Unit-Tests nicht ersetzen. Option B ist falsch, da Vererbung gerade **nicht** das zentrale Prinzip ist (vgl. Slide 330: "Vererbung bedeutet, man legt sich auf eine Implementierung fest"). Option D ist falsch, da Design-Patterns auch die Implementierung beeinflussen (z. B. durch Erzeugungsmuster).

---

> [!question] **Frage 2: Erzeugungsmuster und Objektkomposition**
> Welche Aussage zu **Erzeugungsmustern** und der Beziehung zwischen **Vererbung** und **Objektkomposition** ist **falsch**?
>
> - [ ] A) Erzeugungsmuster wie die "Abstrakte Fabrik" oder der "Erbauer" verstecken den Erzeugungsprozess und ermöglichen so eine Konzentration auf die Schnittstelle.
> - [ ] B) Objektkomposition (z. B. Aggregation) ist zur Laufzeit änderbar, während Vererbung zur Compile-Zeit festgelegt wird.
> - [ ] C) Erzeugungsmuster ersetzen die Notwendigkeit von Vererbung vollständig, da sie eine flexiblere Alternative bieten.
> - [ ] D) Ein Vorteil der Objektkomposition ist, dass sich die genutzte Implementierung zur Laufzeit ändern kann.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > Erzeugungsmuster (Slide 331) verstecken zwar den Erzeugungsprozess, ersetzen aber **nicht** die Notwendigkeit von Vererbung vollständig. Vererbung kann weiterhin sinnvoll sein (z. B. für gemeinsame Basisfunktionalität), während Erzeugungsmuster die konkrete Objekterzeugung steuern. Option A ist korrekt (Slide 331). Option B ist korrekt (Slide 330: "Aggregation erfolgt zur Laufzeit"). Option D ist korrekt (Slide 330: "Dieses unbekannte X kann sich auch zur Laufzeit ändern").

---

> [!question] **Frage 3: Fabrikmethoden vs. parametrisierte Fabrikmethoden**
> Welche Aussage zu **Fabrikmethoden** und ihrer **parametrisierten Variante** ist **richtig**?
>
> - [ ] A) Fabrikmethoden erfordern immer eine abstrakte Basisklasse, während parametrisierte Fabrikmethoden ohne Vererbung auskommen.
> - [ ] B) Parametrisierte Fabrikmethoden ermöglichen es, durch Parameter unterschiedliche Objekte zu erzeugen, ohne neue Unterklassen zu erstellen.
> - [ ] C) Die parametrisierte Variante der Fabrikmethode ist in der Vorlesung (Slide 339) als die einzige korrekte Implementierung dargestellt worden.
> - [ ] D) Fabrikmethoden und parametrisierte Fabrikmethoden sind identisch in ihrer Funktionsweise und unterscheiden sich nur im Namen.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Parametrisierte Fabrikmethoden (Slide 340) erlauben es, durch Parameter (z. B. `type`) unterschiedliche Objekte zu erzeugen, ohne dass jede Variante eine eigene Unterklasse erfordert. Dies erhöht die Flexibilität. Option A ist falsch, da Fabrikmethoden nicht zwingend eine abstrakte Basisklasse erfordern (vgl. Slide 337: nicht-abstrakte Fabrikmethoden). Option C ist falsch, da die abstrakte Variante (Slide 339) ebenfalls korrekt ist. Option D ist falsch, da sich die beiden Varianten in ihrer Funktionsweise unterscheiden (parametrisierte Methoden bieten mehr Flexibilität).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien, formatiert für Obsidian:

---

> [!question] **Frage 1: Fabrikmethoden vs. Abstrakte Fabrik**
> Welche der folgenden Aussagen beschreibt **korrekt** den **zentralen Unterschied** zwischen der **Fabrikmethode (Factory Method)** und der **Abstrakten Fabrik (Abstract Factory)**?
>
> - [ ] A) Die Fabrikmethode wird in einer einzelnen Klasse implementiert, während die Abstrakte Fabrik immer eine Hierarchie von Fabriken erfordert.
> - [ ] B) Die Fabrikmethode delegiert die Objekterzeugung an Unterklassen, während die Abstrakte Fabrik eine Familie zusammenhängender Objekte erzeugt und deren Konsistenz garantiert.
> - [ ] C) Die Fabrikmethode ist ein **Erzeugungsmuster**, das die Abstrakte Fabrik als **Verhaltensmuster** erweitert.
> - [ ] D) Die Abstrakte Fabrik kann nur ein einziges Produkt erzeugen, während die Fabrikmethode mehrere Produkte gleichzeitig erstellen kann.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **Fabrikmethode (Slide 342–343)**: Fokus auf **Delegation der Objekterzeugung an Unterklassen** (z. B. `mkAL()` in `FrenchAL`). Sie erzeugt **einzelne Objekte** und ist ein **Erzeugungsmuster**.
> > - **Abstrakte Fabrik (Slide 346–353)**: Erzeugt **Familien zusammenhängender Objekte** (z. B. `AddressLabel`, `TelephoneLabel`, `BusinessLabel`) und garantiert deren **Konsistenz**. Sie ist eine **Erweiterung des Factory-Method-Patterns** für Produktfamilien.
> > - Option A ist falsch, weil die Abstrakte Fabrik **nicht zwingend eine Hierarchie** erfordert (vgl. **Variante III** mit Prototypen, Slide 352).
> > - Option C ist falsch, weil beide Muster **Erzeugungsmuster** sind (Gamma et al.).
> > - Option D ist falsch, da die Abstrakte Fabrik **mehrere Produkte** erzeugt (Slide 346).

---

> [!question] **Frage 2: Problem der inkonsistenten Fabrikimplementierung**
> In **Slide 344** wird ein Beispiel gezeigt, in dem eine Unterklasse (`MyAddressBook`) die Fabrikmethoden `mkAL()`, `mkTL()` und `mkBL()` überschreibt, aber **falsche Kombinationen** zurückgibt (z. B. `FrenchAL` mit `GermanTL`).
> Welche **Lösung** wird in den Folien **explizit vorgeschlagen**, um dieses Problem zu vermeiden?
>
> - [ ] A) Verwendung eines **Singleton-Patterns** für die Fabrik, um globale Konsistenz zu erzwingen.
> - [ ] B) Einführung einer **Abstrakten Fabrik (Abstract Factory)**, die alle Produktfamilien (z. B. `LabelFactory`) zentralisiert und deren Konsistenz garantiert.
> - [ ] C) Ersetzung der Fabrikmethoden durch **Reflection**, um zur Laufzeit die korrekten Klassen zu laden.
> - [ ] D) Nutzung eines **Builder-Patterns**, um die Objekte schrittweise zu konstruieren.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **Problem (Slide 344)**: Die manuelle Kombination von Produkten (z. B. `FrenchAL` + `GermanTL`) führt zu **inkonsistenten Objekten**.
> > - **Lösung (Slide 346–348)**: Die **Abstrakte Fabrik** (`LabelFactory`) stellt sicher, dass **alle Produkte einer Familie zusammenpassen** (z. B. `GermanLabelFactory` erzeugt nur `GermanAL`, `GermanTL`, `GermanBL`).
> > - Option A ist falsch, da ein Singleton **keine Produktkonsistenz** garantiert.
> > - Option C ist falsch, weil Reflection **keine semantische Konsistenz** sicherstellt.
> > - Option D ist falsch, da der **Builder** sich auf die **schrittweise Konstruktion** eines Objekts konzentriert, nicht auf Produktfamilien.

---
> [!question] **Frage 3: Vor- und Nachteile der Abstrakten Fabrik**
> Welche der folgenden Aussagen zu den **Vor- und Nachteilen der Abstrakten Fabrik** (Slide 354) ist **falsch**?
>
> - [ ] A) Ein Vorteil ist, dass der Client-Code **unabhängig von konkreten Produktklassen** ist und nur mit der abstrakten Fabrik interagiert.
> - [ ] B) Ein Nachteil ist, dass das Hinzufügen **neuer Produktarten** (z. B. ein neues `EmailLabel`) **Änderungen in der Fabrik und allen Unterklassen** erfordert.
> - [ ] C) Ein Vorteil ist, dass die Abstrakte Fabrik die **Erzeugung zusammenhängender Produktfamilien** unterstützt, was die Konsistenz erhöht.
> - [ ] D) Ein Nachteil ist, dass die Abstrakte Fabrik **keine Polymorphie** unterstützt, da alle Produkte statisch typisiert sein müssen.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **Vorteil (Slide 354)**: Der Client-Code ist **unabhängig von konkreten Produkten** (Option A ist richtig).
> > - **Nachteil (Slide 354)**: Das Hinzufügen neuer Produktarten (z. B. `EmailLabel`) erfordert Änderungen in **allen Fabriken** (Option B ist richtig).
> > - **Vorteil**: Die Abstrakte Fabrik **garantiert Konsistenz von Produktfamilien** (Option C ist richtig).
> > - **Falsch ist Option D**, weil die Abstrakte Fabrik **Polymorphie voll unterstützt** (z. B. alle Fabriken implementieren `LabelFactory` und geben Produkte des Typs `AddressLabel` zurück). Die Typisierung ist **abstrakt**, nicht statisch.

---
Diese Fragen decken **Kernkonzepte** (Unterschiede zwischen Mustern, Lösungsansätze für Probleme, Vor-/Nachteile) ab und sind so formuliert, dass sie **tieferes Verständnis** prüfen. Die Distraktoren sind plausibel, aber eindeutig falsch.

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Grundkonzept der Bridge**
> Welche der folgenden Aussagen beschreibt **korrekt** den Hauptzweck des **Bridge-Musters**?
>
> - [ ] A) Es ermöglicht die direkte Kommunikation zwischen Client und Implementierung, um die Performance zu steigern.
> - [ ] B) Es trennt Abstraktion und Implementierung, sodass beide unabhängig voneinander variiert werden können.
> - [ ] C) Es kapselt eine Klasse vollständig, um die Wiederverwendung in anderen Kontexten zu verhindern.
> - [ ] D) Es ersetzt Vererbung durch Komposition, um die Kopplung zwischen Klassen zu erhöhen.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Das Bridge-Muster entkoppelt Abstraktion und Implementierung, sodass beide unabhängig voneinander erweitert oder geändert werden können (vgl. Slide 356 und 358).
> > - **A** ist falsch, weil die Bridge keine direkte Kommunikation fördert, sondern die Implementierung versteckt.
> > - **C** ist falsch, da die Bridge gerade die Wiederverwendung durch klare Trennung ermöglicht.
> > - **D** ist falsch, weil die Bridge Komposition nutzt, um die Kopplung zu **reduzieren**, nicht zu erhöhen.

---

> [!question] **Frage 2: Problem des fehlenden Redesigns (Beispiel MyClub)**
> Warum wurde in dem **MyClub-Beispiel** (Slides 360–363) ein Redesign mit dem Bridge-Muster notwendig?
>
> - [ ] A) Weil die ursprüngliche Implementierung der Chiffrier-Algorithmen zu langsam war.
> - [ ] B) Weil die Struktur durch zusätzliche Anforderungen (z. B. neue Algorithmen oder Plattformen) unwartbar wurde und Abwärtskompatibilität verloren ging.
> - [ ] C) Weil die Client-Anwendungen die Schnittstelle der Chiffrier-Klassen nicht verstanden.
> - [ ] D) Weil die Bridge-Muster-Implementierung in der ursprünglichen Version fehlerhaft war.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Das Beispiel zeigt, wie die Erweiterung um neue Chiffrier-Algorithmen (DES3, AES, IDEA, RC6) und plattformspezifische Implementierungen zu einer unübersichtlichen Struktur führte (Slide 362–363). Die Bridge wurde eingeführt, um:
> > - Abstraktion (z. B. `Cipher`) und Implementierung (z. B. `DES3`, `AES`) zu trennen,
> > - Abwärtskompatibilität zu erhalten (Slide 364).
> > - **A** ist falsch, da Performance nicht das primäre Problem war.
> > - **C** ist falsch, weil die Schnittstelle durch das Interface `Cipher` bereits standardisiert war.
> > - **D** ist falsch, da das Problem nicht in der Bridge-Implementierung, sondern in der fehlenden Trennung lag.

---
> [!question] **Frage 3: Adapter vs. Bridge**
> Welche der folgenden Aussagen beschreibt **korrekt** den **Unterschied zwischen dem Adapter- und dem Bridge-Muster**?
>
> - [ ] A) Der Adapter passt Schnittstellen an, während die Bridge Abstraktion und Implementierung trennt.
> - [ ] B) Beide Muster nutzen Vererbung, um die Kopplung zwischen Klassen zu erhöhen.
> - [ ] C) Der Adapter wird nur für plattformspezifische Implementierungen verwendet, die Bridge für Algorithmen.
> - [ ] D) Die Bridge erfordert immer einen Objekt-Adapter, während der Adapter ohne Bridge nicht funktioniert.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: A**
> >
> > *Erklärung*:
> > - **Adapter** (Slides 368–369) passt **inkompatible Schnittstellen** an, sodass bestehende Klassen zusammenarbeiten können.
> > - **Bridge** (Slides 356–358) trennt **Abstraktion** (z. B. `Abstraction`) von **Implementierung** (z. B. `Implementor`), um beide unabhängig zu variieren.
> > - **B** ist falsch, da beide Muster die Kopplung **reduzieren** (Adapter durch Anpassung, Bridge durch Entkopplung).
> > - **C** ist falsch, da Adapter und Bridge unterschiedliche Zwecke haben (Adapter: Schnittstellenanpassung; Bridge: Entkopplung).
> > - **D** ist falsch, weil Adapter und Bridge **unabhängige Muster** sind und der Adapter sowohl als Klassen- als auch als Objekt-Adapter implementiert werden kann (Slides 368–369).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Adaptermuster vs. Brückenmuster**
> Welche der folgenden Aussagen beschreibt **korrekt** einen **zentralen Unterschied** zwischen dem Adaptermuster und dem Brückenmuster?
>
> - [ ] A) Beide Muster dienen ausschließlich dazu, die Performance von Software zu verbessern, indem sie die Anzahl der Methodenaufrufe reduzieren.
> - [ ] B) Das Adaptermuster wird verwendet, um Inkompatibilitäten zwischen Schnittstellen zu überwinden, während das Brückenmuster eine Abstraktion von der Implementierung trennt.
> - [ ] C) Das Adaptermuster ist ein strukturelles Muster, das Brückenmuster hingegen ein Verhaltensmuster.
> - [ ] D) Beide Muster erfordern die Verwendung von Mehrfachvererbung, um ihre Ziele zu erreichen.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **Option A** ist falsch, da weder Adapter noch Brücke primär der Performance-Optimierung dienen.
> > - **Option B** ist korrekt: Das Adaptermuster löst Schnittstelleninkompatibilitäten (z. B. zwischen `X` und `Y` in Slide 371), während das Brückenmuster eine Abstraktion (z. B. eine GUI-Komponente) von ihrer Implementierung (z. B. verschiedene Rendering-Backends) trennt (Slide 373).
> > - **Option C** ist falsch, da beide Muster strukturelle Muster sind (Gamma et al.).
> > - **Option D** ist falsch, da Mehrfachvererbung für keines der Muster zwingend erforderlich ist (Adapter nutzt Komposition, Brücke nutzt Delegation).

---

> [!question] **Frage 2: Zweck des Adaptermusters**
> Welche der folgenden **Anwendungsfälle** ist **kein typischer Grund**, das Adaptermuster einzusetzen? (Basierend auf Slide 372)
>
> - [ ] A) Eine existierende Klasse soll in einem neuen System verwendet werden, dessen Schnittstelle nicht kompatibel ist.
> - [ ] B) Eine wiederverwendbare Klasse soll mit unbekannten Klassen (mit unbekannten Schnittstellen) zusammenarbeiten, ohne deren Implementierung zu kennen.
> - [ ] C) Eine gemeinsame Schnittstelle für mehrere Klassen soll definiert werden, um Mehrfachvererbung zu vermeiden.
> - [ ] D) Die Performance einer Anwendung soll durch Reduzierung von Methodenaufrufen verbessert werden.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **Option A** ist ein klassischer Anwendungsfall (Slide 372, 1. Punkt).
> > - **Option B** ist ebenfalls korrekt (Slide 372, 2. Punkt).
> > - **Option C** beschreibt einen Anwendungsfall für das Adaptermuster (Slide 372, 3. Punkt), um Mehrfachvererbung zu umgehen.
> > - **Option D** ist falsch, da das Adaptermuster **nicht** der Performance-Optimierung dient, sondern der Schnittstellenanpassung.

---
> [!question] **Frage 3: Implementierung des Observer-Patterns in der Zustandsmaschine**
> Betrachten Sie die Implementierung der `StateMachineImpl` aus Slide 380. Welche der folgenden Aussagen zur **Kopplung zwischen Zustandsmaschine und Views** ist **falsch**?
>
> - [ ] A) Die `StateMachineImpl` fungiert als `Subject` und benachrichtigt Observer (z. B. Views) bei Zustandsänderungen.
> - [ ] B) Die Methode `setState()` löst eine Benachrichtigung aller registrierten Observer aus, indem sie deren `update()`-Methode aufruft.
> - [ ] C) Die `StateMachineImpl` verwaltet die Liste der Observer und stellt sicher, dass Views immer den aktuellen Zustand anzeigen.
> - [ ] D) Die `StateMachineImpl` speichert den aktuellen Zustand in einer Datenbank, um Persistenz zu gewährleisten.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **Option A** ist korrekt: Die `StateMachineImpl` implementiert das `Subject`-Interface und benachrichtigt Observer (Slide 380).
> > - **Option B** ist korrekt: `setState()` aktualisiert den Zustand und benachrichtigt alle Observer (Slide 380).
> > - **Option C** ist korrekt: Die Klasse verwaltet Observer und stellt Konsistenz sicher (Slide 380).
> > - **Option D** ist **falsch**, da die `StateMachineImpl` **keine Persistenz** implementiert (Slide 383 behandelt Persistenz separat, z. B. durch OR-Mapper wie Hibernate).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Welche der folgenden Aussagen beschreibt **korrekt** die Rolle des System-/Architekturentwurfs im Software-Engineering-Prozess?**
> - [ ] A) Der System-/Architekturentwurf ist ausschließlich für die Implementierung der Benutzeroberfläche zuständig.
> - [ ] B) Er dient als Bindeglied zwischen Analyse und Design und definiert die Aufteilung des Systems in Teilsysteme sowie Steuerungs- und Datenhaltungsstrategien.
> - [ ] C) Der System-/Architekturentwurf ersetzt die Phase der Anforderungsanalyse und übernimmt deren Aufgaben.
> - [ ] D) Diese Phase konzentriert sich nur auf die technische Umsetzung von Algorithmen und vernachlässigt die Systemorganisation.

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist falsch, da der System-/Architekturentwurf nicht auf die Benutzeroberfläche beschränkt ist, sondern die gesamte Systemstruktur betrifft.
> > - **B** ist korrekt, da der System-/Architekturentwurf tatsächlich die Schnittstelle zwischen Analyse (Was soll das System leisten?) und Design (Wie wird es umgesetzt?) bildet und dabei die Zerlegung in Teilsysteme sowie Steuerungs- und Datenstrategien festlegt (vgl. Folie 386).
> > - **C** ist falsch, weil der System-/Architekturentwurf die Analyse nicht ersetzt, sondern auf deren Ergebnissen aufbaut.
> > - **D** ist falsch, da die technische Umsetzung von Algorithmen Teil des Objektentwurfs (funktionales Design) ist, nicht des System-/Architekturentwurfs.

---

> [!question] **Frage 2: Welche der folgenden Aussagen zu **Verantwortlichkeiten im Design** ist **falsch**?**
> - [ ] A) Verantwortlichkeiten können darin bestehen, etwas zu tun (z. B. eine Operation auszuführen).
> - [ ] B) Verantwortlichkeiten können darin bestehen, etwas zu wissen (z. B. Daten zu speichern oder zu berechnen).
> - [ ] C) Verantwortlichkeiten werden ausschließlich an eine zentrale Instanz delegiert, um Komplexität zu reduzieren.
> - [ ] D) Verantwortlichkeiten umfassen auch die Entscheidung, ob eine Aufgabe selbst ausgeführt oder an ein anderes Objekt delegiert wird.

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A**, **B** und **D** sind korrekte Aussagen zu Verantwortlichkeiten im Design (vgl. Folie 387):
> >   - **A** und **B** beschreiben die beiden Hauptkategorien von Verantwortlichkeiten (Handeln vs. Wissen).
> >   - **D** betont die Delegationsmöglichkeit, die ein zentrales Prinzip des objektorientierten Designs ist.
> > - **C** ist falsch, weil Verantwortlichkeiten **nicht** zwingend an eine zentrale Instanz delegiert werden müssen. Stattdessen wird oft eine **Verteilung** der Verantwortlichkeiten angestrebt (z. B. nach dem *Single Responsibility Principle*), um Kopplung zu reduzieren.

---
> [!question] **Frage 3: Welcher der folgenden Schritte gehört **nicht** zur Phase des **Objektentwurfs** (funktionales Design) im Software-Engineering-Prozess?**
> - [ ] A) Umsetzung der im System-/Architekturentwurf definierten Strategien in konkrete Klassen und Objekte.
> - [ ] B) Zuweisung von Verantwortlichkeiten an einzelne Objekte oder Klassen.
> - [ ] C) Definition der Systemarchitektur und Aufteilung in Teilsysteme.
> - [ ] D) Entwurf von Algorithmen für die Operationen der Schnittstellen.

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A**, **B** und **D** sind typische Aktivitäten des **Objektentwurfs** (vgl. Folie 386):
> >   - **A** und **B** beschreiben die Umsetzung der Architekturvorgaben in konkrete Designentscheidungen (z. B. Klassenverantwortlichkeiten).
> >   - **D** bezieht sich auf den Entwurf von Algorithmen, der ein zentraler Bestandteil des funktionalen Designs ist.
> > - **C** gehört zur **System-/Architekturentwurfsphase**, nicht zum Objektentwurf. Die Definition der Systemarchitektur und Teilsysteme ist eine **vorherige** Aufgabe (vgl. Folie 386: "Aufbrechen des Systems in Teilsysteme" als Teil des System-/Architekturentwurfs).