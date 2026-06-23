# 🧠 Study Quiz: Software Engineering (Slides 326-327)

Hier ist das anspruchsvolle Multiple-Choice-Quiz zum Thema **Software-Engineering (Erzeugungsmuster, Use-Case-Manager, Design-Prinzipien)** basierend auf den Slides 326–327:

---

> [!question] **Frage 1: Welche zentrale Rolle übernimmt der **Use-Case-Manager** in der Softwarearchitektur?**
> - [ ] A) Er optimiert die Performance der Datenbankzugriffe durch Caching-Mechanismen.
> - [ ] B) Er zentralisiert die Verantwortung für alle Operationen eines spezifischen Use-Cases und fungiert als Schnittstelle zwischen System und Komponenten.
> - [ ] C) Er ersetzt die Geschäftslogik durch generische Algorithmen, um die Wartbarkeit zu erhöhen.
> - [ ] D) Er verwaltet die Benutzerrechte und Authentifizierung im System.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Der Use-Case-Manager (vgl. Slide 326) dient als **zentrale Steuerungseinheit**, die alle Operationen eines Use-Cases bündelt und die Kommunikation zwischen den Komponenten (z. B. Datenbank, UI, Geschäftslogik) koordiniert. Dies verhindert fragmentierte Verantwortlichkeiten und erhöht die Kohäsion des Systems. Option A beschreibt eine Performance-Optimierung (nicht Kernaufgabe), Option C verwechselt den Use-Case-Manager mit generischen Algorithmen, und Option D bezieht sich auf ein anderes Muster (z. B. **Authentifizierungs-Manager**).

---

> [!question] **Frage 2: Warum ist die **Programmierung gegen Schnittstellen** (Interface-Based Programming) ein zentrales Prinzip für flexible Softwarearchitekturen?**
> - [ ] A) Sie ermöglicht die direkte Manipulation von Datenbanktabellen ohne Abstraktionsebenen.
> - [ ] B) Sie reduziert die Kopplung zwischen Komponenten, indem Abhängigkeiten abstrahiert und austauschbar werden.
> - [ ] C) Sie erzwingt die Verwendung von Singleton-Patterns, um globale Zustände zu vermeiden.
> - [ ] D) Sie standardisiert die Benutzeroberfläche durch vorgegebene UI-Komponenten.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Die Programmierung gegen Schnittstellen (vgl. Slide 327) **entkoppelt Komponenten**, indem sie konkrete Implementierungen durch abstrakte Schnittstellen ersetzt. Dies ermöglicht:
> > - **Austauschbarkeit** (z. B. Datenbank-Adapter ohne Änderung der Kernlogik),
> > - **Wiederverwendbarkeit** (gleiche Schnittstelle für verschiedene Implementierungen),
> > - **Testbarkeit** (Mock-Objekte können leicht eingesetzt werden).
> > Option A beschreibt eine anti-pattern (direkte DB-Manipulation), Option C ist falsch (Singletons sind ein anderes Muster), und Option D bezieht sich auf UI-Standards (nicht das Prinzip selbst).

---
> [!question] **Frage 3: Welche **Architekturstrategie** wird in Slide 327 als Alternative zum Use-Case-Manager vorgeschlagen, um die Kommunikation zwischen Komponenten zu zentralisieren – und unter welchem Namen ist sie bekannt?**
> - [ ] A) **Observer-Pattern**: Komponenten werden über Events synchronisiert.
> - [ ] B) **Mediator-Pattern**: Eine zentrale Instanz koordiniert die Kommunikation zwischen Komponenten.
> - [ ] C) **Repository-Pattern**: Datenzugriffe werden über eine zentrale Klasse gekapselt.
> - [ ] D) **Decorator-Pattern**: Komponenten werden dynamisch um zusätzliche Funktionalität erweitert.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Slide 326 erwähnt explizit den **Mediator** als Alternative zum Use-Case-Manager:
> > - Der **Mediator** zentralisiert die Kommunikation zwischen Komponenten, ohne dass diese direkt miteinander interagieren müssen (vermindert Kopplung).
> > - Der **Observer** (Option A) ist ein anderes Muster (Event-basierte Kommunikation).
> > - Das **Repository-Pattern** (Option C) dient der Datenabstraktion (z. B. `MemberRepository`), nicht der Koordination.
> > - Der **Decorator** (Option D) fügt Verhalten dynamisch hinzu (z. B. Logging um eine Methode).
> >
> > *Hinweis*: Slide 327 erwähnt zusätzlich die **Ports-and-Adapters-Architektur** (hexagonale Architektur), die jedoch **keine direkte Alternative zum Mediator** ist, sondern eine **Entkopplungsstrategie** für externe Abhängigkeiten (z. B. Datenbank, APIs). Die Frage bezieht sich jedoch explizit auf die **Kommunikationszentralisierung** zwischen Komponenten.

---
Das Quiz prüft:
1. **Verständnis** des Use-Case-Managers (Frage 1),
2. **Anwendung** von Design-Prinzipien (Frage 2),
3. **Abgrenzung von Mustern** (Frage 3).

Die Fragen sind auf **Master-Niveau** ausgelegt und erfordern Transferwissen (z. B. Abwägen von Alternativen). Die Distraktoren sind plausibel, aber fachlich falsch.