---
type: chapter_quiz
chapter: 4
range: "200-325"
generated_at: 2026-06-06 16:34:22
tags:
  - software_engineering
  - quiz
  - chapter_quiz_4
---

# 🧠 Chapter 4 Quiz: Systemarchitektur und Interaktion

**Slide Range:** 200-325

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Architekturentscheidungen im Software-Engineering**
> Welche der folgenden Aussagen zu Architekturentscheidungen in der Erstellungsphase (Phase II) ist **falsch**?
> - [ ] A) Die Systemarchitektur konsolidiert sich durch iterative Verfeinerung der Komponenten und Schichten.
> - [ ] B) Neue Anforderungen werden in späteren Iterationen ignoriert, um die Stabilität der Architektur nicht zu gefährden.
> - [ ] C) Die Zuweisung von Teilsystemen zu Prozessen, Threads oder Maschinen ist Teil der Architekturdefinition.
> - [ ] D) Grenzbedingungen (z. B. Performance-Anforderungen) müssen dokumentiert und in der Architektur berücksichtigt werden.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist korrekt: Die Architektur reift durch iterative Verfeinerung (Slide 202).
> > - **B** ist **falsch**: Neue Anforderungen *werden* in späteren Iterationen integriert (Slide 202).
> > - **C** ist korrekt: Die Zuweisung zu Hardware/Software-Ressourcen ist ein zentraler Architekturentscheid (Slide 203).
> > - **D** ist korrekt: Grenzbedingungen müssen erfasst und dokumentiert werden (Slide 203).

---

> [!question] **Frage 2: Komponentenmodellierung und Paketstruktur**
> Welche Aussage zur Organisation von Komponenten und Paketen (Slides 205–209) ist **zutreffend**?
> - [ ] A) Eine Komponente darf nur eine einzige Schnittstelle anbieten, um Abhängigkeiten zu minimieren.
> - [ ] B) Packages dürfen zyklische Abhängigkeiten aufweisen, solange sie logisch zusammengehören.
> - [ ] C) Die Trennung von Schnittstelle (`port`) und Implementierung (`impl`) fördert lose Kopplung und Wartbarkeit.
> - [ ] D) Ein `<<access>>`-Import ermöglicht den Zugriff auf *alle* öffentlichen Elemente eines Pakets, ohne Namensraumtrennung.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A** ist falsch: Komponenten können mehrere Schnittstellen anbieten (Slide 205).
> > - **B** ist falsch: Zyklische Paketabhängigkeiten sind explizit verboten (Slide 208).
> > - **C** ist **korrekt**: Die Trennung von Schnittstelle und Implementierung (Slide 207) ist ein Best Practice für Komponenten.
> > - **D** ist falsch: `<<access>>` erlaubt nur den Zugriff auf bestimmte öffentliche Elemente *mit* Namensraumtrennung (Slide 209).

---
> [!question] **Frage 3: Drei-Schichtenmodell und Deployment**
> Welche Aussage zum **Drei-Schichtenmodell** (Slide 214) und dessen **Deployment** (Slide 211) ist **falsch**?
> - [ ] A) Die Präsentationsschicht kann sowohl Client- als auch Server-seitig implementiert sein (z. B. Web-Frontend).
> - [ ] B) Die Logikschicht ist immer physisch auf einem separaten Server von der Datenzugriffsschicht getrennt.
> - [ ] C) Ein Deployment-Diagramm zeigt die Verteilung von Komponenten auf physische Knoten (z. B. `kundenPC` und `lzs.myclub.de`).
> - [ ] D) Die Datenzugriffsschicht kann externe Systeme wie Datenbanken oder Mail-Server einbinden.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist korrekt: Die Präsentationsschicht kann sowohl lokal (Desktop) als auch remote (Web) sein (Slide 214).
> > - **B** ist **falsch**: Die Logikschicht *muss* nicht physisch getrennt sein – sie kann auch auf demselben Knoten wie die Datenzugriffsschicht laufen (z. B. bei Desktop-Anwendungen).
> > - **C** ist korrekt: Deployment-Diagramme visualisieren die physische Verteilung (Slide 211).
> > - **D** ist korrekt: Die Persistenzschicht integriert externe Systeme (Slide 214).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Architekturprinzipien in der Schichtenarchitektur**
> Welche der folgenden Aussagen zur Schichtenarchitektur im MyClub-Projekt ist **korrekt**?
> - [ ] A) Die Persistenzschicht darf direkt auf die Präsentationsschicht zugreifen, um Daten für die GUI aufzubereiten.
> - [ ] B) Die Logikschicht ist für die Validierung von Benutzereingaben verantwortlich, während die Präsentationsschicht nur für die Darstellung zuständig ist.
> - [ ] C) Ein Verstoß gegen die Schichtenhierarchie liegt vor, wenn eine höhere Schicht Objekte aus einer tieferen Schicht nutzt, ohne dass die dazugehörende Klasse in der höheren Schicht definiert ist.
> - [ ] D) Die Datenzugriffs- und Persistenzschicht (z. B. `Database Connector`) darf eigenständig Geschäftslogik implementieren, um die Performance zu optimieren.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A** ist falsch, da die Persistenzschicht (tiefere Schicht) **nie** direkt auf die Präsentationsschicht (höhere Schicht) zugreifen darf (Verstoß gegen Hierarchieprinzip).
> > - **B** ist falsch, da die **Präsentationsschicht** für die Validierung zuständig sein kann (z. B. Eingabeprüfung), während die **Logikschicht** die eigentliche Geschäftslogik enthält.
> > - **C** ist korrekt: Laut Slide 219 muss eine Klasse, deren Objekte genutzt werden, entweder in der aktuellen Schicht definiert sein oder aus einer tieferen Schicht stammen. Ein direkter Zugriff auf Objekte aus höheren Schichten wäre ein Verstoß.
> > - **D** ist falsch, da die Persistenzschicht **keine** Geschäftslogik implementieren darf (klare Trennung der Verantwortlichkeiten).

---

> [!question] **Frage 2: Model-View-Controller (MVC) und Schichtenarchitektur**
> Im MyClub-Projekt wird das MVC-Muster diskutiert. Welche der folgenden Zuordnungen zwischen MVC-Komponenten und Schichten ist **falsch**?
> - [ ] A) Die **View** entspricht der Präsentationsschicht.
> - [ ] B) Der **Controller** ist Teil der Logikschicht.
> - [ ] C) Das **Model** enthält die Geschäftslogik und gehört zur Logikschicht.
> - [ ] D) Der **Controller** darf direkt auf die Datenbank zugreifen, um Daten zu manipulieren.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A** ist korrekt: Die View ist für die Darstellung zuständig und entspricht der Präsentationsschicht.
> > - **B** ist korrekt: Der Controller verarbeitet Benutzereingaben und leitet sie an das Model weiter – er gehört zur Logikschicht.
> > - **C** ist korrekt: Das Model enthält die Kernlogik (z. B. Geschäftsregeln) und gehört zur Logikschicht.
> > - **D** ist **falsch**: Der Controller darf **nicht** direkt auf die Datenbank zugreifen. Dies ist Aufgabe der Persistenzschicht (z. B. `Database Connector`). Ein direkter Datenbankzugriff durch den Controller wäre ein Verstoß gegen die Schichtenhierarchie (Slide 219).

---
> [!question] **Frage 3: Polling vs. Push-from-below in der UI-Architektur**
> Im Kontext der Benutzerschnittstelle (Slide 224) wird zwischen Polling- und Push-from-below-Lösungen unterschieden. Welche Aussage dazu ist **falsch**?
> - [ ] A) Polling ist ineffizient, weil es zu häufigen Abfragen führt, die unnötige Last erzeugen.
> - [ ] B) Push-from-below-Lösungen sind besser geeignet, um spontane Änderungen (z. B. Animationen) darzustellen.
> - [ ] C) Bei Polling muss die höhere Schicht (z. B. Präsentationsschicht) aktiv nach Änderungen fragen, während Push-from-below Änderungen aktiv an die höhere Schicht sendet.
> - [ ] D) Polling ist immer die bevorzugte Lösung, wenn die Datenquelle (z. B. Datenbank) keine Benachrichtigungsmechanismen unterstützt.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A**, **B** und **C** sind korrekt:
> >   - **A**: Polling ist ineffizient (Slide 224).
> >   - **B**: Push-from-below ist besser für spontane Änderungen geeignet.
> >   - **C**: Polling = aktive Abfrage; Push = passive Benachrichtigung.
> > - **D** ist **falsch**, weil Polling **nicht** die bevorzugte Lösung ist, selbst wenn die Datenquelle keine Benachrichtigungen unterstützt. In solchen Fällen sollte stattdessen eine **Entkopplung** (z. B. durch Observer-Pattern) implementiert werden, um die Schichten sauber zu trennen (Vermeidung von Punkt 2 in Slide 219).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien, formatiert für Obsidian:

---

> [!question] **Frage 1: Verantwortlichkeiten im MVC-Pattern**
> Welche der folgenden Aussagen beschreibt **korrekt** die Verantwortlichkeiten der Komponenten im Model-View-Controller-Pattern (MVC)?
> - [ ] A) Der **Controller** enthält die domänenspezifische Logik und entscheidet über die Geschäftsregeln.
> - [ ] B) Die **View** ist für die Verarbeitung von Benutzereingaben zuständig und leitet diese an das Modell weiter.
> - [ ] C) Das **Modell** stellt ausschließlich Daten bereit, während die Geschäftslogik in separaten Service-Klassen implementiert wird.
> - [ ] D) Der **Controller** empfängt Benutzereingaben, leitet sie an das Modell weiter und aktualisiert die View bei Änderungen.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A** ist falsch, da der Controller **keine domänenspezifische Logik** enthält (vgl. Slide 230). Diese gehört ins Modell.
> > - **B** ist falsch, weil die **Verarbeitung von Eingaben** Aufgabe des Controllers ist, nicht der View (Slide 233/237).
> > - **C** ist falsch, da das Modell **sowohl Daten als auch Logik** vereint (Slide 230: "Das Modell beinhaltet nicht nur Daten, sondern auch das domänenspezifische Wissen").
> > - **D** ist korrekt: Der Controller empfängt Eingaben, ruft Modell-Methoden auf (`model.service()`) und löst die Aktualisierung der View aus (Slide 236/237).

---

> [!question] **Frage 2: Observer-Pattern im MVC**
> Welche Aussage zur Rolle des **Observer-Patterns** im MVC ist **falsch**?
> - [ ] A) Das Modell agiert als **Subject** und benachrichtigt Views (Observer) bei Datenänderungen.
> > [!faq]- Hinweis
> > Betrachte Slide 235–236: Wer ist das Subject, und wer sind die Observer?
> - [ ] B) Die **View** registriert sich beim Modell, um über Änderungen informiert zu werden (`attach()`).
> - [ ] C) Der **Controller** kann als Observer fungieren, um auf Benutzereingaben zu reagieren.
> - [ ] D) Das Observer-Pattern ermöglicht eine **lose Kopplung** zwischen Modell und Views.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A**, **B** und **D** sind korrekte Beschreibungen des Observer-Patterns im MVC (Slide 235–236):
> >   - Modell = Subject, Views = Observer.
> >   - Views registrieren sich (`attach()`) und werden bei Änderungen benachrichtigt (`notify()`).
> >   - Lose Kopplung wird durch das Pattern erreicht.
> > - **C** ist falsch, weil der **Controller** **kein Observer** ist. Er empfängt zwar Eingaben, aber seine Hauptaufgabe ist die **Weiterleitung an das Modell** (Slide 236: Controller ruft `model.service()` auf). Die Aktualisierung der View erfolgt indirekt über das Modell (Observer-Pattern).

---
> [!question] **Frage 3: Implementierungsaspekte von MVC**
> Welche Aussage zur **Implementierung von MVC** ist **nicht** mit den Folien vereinbar?
> - [ ] A) Die **Initialisierung** des Systems erfolgt in der Reihenfolge: Modell → Views → Controller.
> - [ ] B) Jede View sollte einen **eigenen Controller** erhalten, der für die Abbildung von Benutzereingaben auf Systemoperationen zuständig ist.
> - [ ] C) Das Modell kann in **mehrere Subsysteme** unterteilt werden, wobei jedes Subsystem eigene Service-Routinen bereitstellt.
> - [ ] D) Die **View** ist für die Darstellung der Daten zuständig, aber sie darf **keine direkten Aufrufe** an das Modell durchführen.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A** ist korrekt (Slide 240: "Zuerst wird das Modell erzeugt, danach die Views, diese registrieren sich beim Modell und erzeugen ihre Controller").
> > - **B** ist korrekt (Slide 240: "Für jede View werden die Bedienmöglichkeiten festgelegt... Ein Controller erhält und interpretiert die Eingaben").
> > - **C** ist korrekt (Slide 241–242: "Das Modell ist kein Monolith! Für jeden Use Case... eine Komponente mit eigenen Service-Routinen").
> > - **D** ist **falsch**, weil die View **direkt Daten vom Modell anfordert** (`getData()` in Slide 234/236). Die View ist zwar für die Darstellung zuständig, aber sie **muss** mit dem Modell interagieren, um Daten zu erhalten. Die Trennung der Verantwortlichkeiten bedeutet nicht, dass die View das Modell nicht nutzen darf – sie darf es sogar **müssen** (Slide 236: `display()` ruft `model.getData()` auf).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien (245–259), die das Verständnis der Kernkonzepte prüfen:

---

> [!question] **Frage 1: Systemoperationen und Schnittstellendesign**
> Welche der folgenden Aussagen beschreibt **korrekt** die Rolle von Systemoperationen im Kontext des Use Cases „Manage Members“ nach den Folien 250–259?
>
> - [ ] A) Systemoperationen sind rein technische Implementierungsdetails und haben keine direkte Verbindung zu den Use-Case-Anforderungen.
> - [ ] B) Systemoperationen müssen nur die Parameter der GUI-Interaktionen abbilden, da die Logikschicht diese automatisch verarbeitet.
> - [ ] C) Systemoperationen präzisieren Systemereignisse, legen Parameter, Ausnahmen und Rückgabewerte fest und bilden die Schnittstelle zwischen Use Case und Systemlogik.
> - [ ] D) Systemoperationen sind identisch mit den Use-Case-Schritten und erfordern keine separate Modellierung oder Dokumentation.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > Laut Folie 250 müssen Systemoperationen **präzisiert** werden, um Systemereignisse und Schnittstellen zu definieren. Sie legen Parameter, Ausnahmen und Rückgabewerte fest (Folie 250) und dienen als Brücke zwischen Use Case und Logikschicht. Option A ist falsch, da Systemoperationen direkt mit den Anforderungen verknüpft sind. Option B ignoriert die Trennung von GUI und Logik (Folie 251). Option D ist falsch, da Systemoperationen eine **technische Verfeinerung** der Use Cases darstellen (Folie 252).

---

> [!question] **Frage 2: Asynchrone Anbindung der GUI**
> Welche der folgenden Aussagen zur asynchronen Anbindung der GUI an die Logikschicht (Folie 251) ist **falsch**?
>
> - [ ] A) Die GUI kann weiterhin auf Benutzeraktionen reagieren, während die Logik eine Operation ausführt.
> - [ ] B) Die Logikschicht führt Operationen synchron aus, während die GUI asynchron mit dem Controller kommuniziert.
> - [ ] C) Die Trennung von GUI und Logik ermöglicht eine bessere Skalierbarkeit, da die GUI nicht auf die Beendigung der Logikoperation warten muss.
> - [ ] D) Die asynchrone Kommunikation wird durch den Controller vermittelt, der Operationen an die Logik weiterleitet.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Folie 251 zeigt, dass die **Logikschicht** Operationen asynchron ausführt (z. B. „Operation ausführen“ im Model), während die GUI weiterhin reagiert. Option B ist falsch, weil die **Logik selbst asynchron** arbeitet, nicht synchron. Die anderen Optionen sind korrekt: A beschreibt das Verhalten der GUI, C die Vorteile der Trennung, und D die Rolle des Controllers (Folie 251).

---
> [!question] **Frage 3: Designschritte nach Larman**
> Welcher der folgenden Schritte gehört **nicht** zu den in Folie 252 dargestellten Designschritten nach Craig Larman?
>
> - [ ] A) Erstellung eines vorläufigen Architekturmodells basierend auf den Use-Case-Diagrammen.
> - [ ] B) Definition von System-Sequenz-Diagrammen für jeden Use Case.
> - [ ] C) Implementierung der Systemoperationen direkt in der GUI-Schicht.
> - [ ] D) Erstellung von Funktionsbeschreibungen für Systemoperationen.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > Folie 252 zeigt die Designschritte nach Larman: Requirements → Use Cases → System-Sequenz-Diagramme → Funktionsbeschreibungen → Architekturmodell → Analyse-Objektmodell. **Die Implementierung der Systemoperationen in der GUI-Schicht** (Option C) ist kein Schritt des Designs, sondern der späteren Implementierung. Die anderen Optionen entsprechen den in der Folie genannten Schritten.

---

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien, formatiert für Obsidian:

---

> [!question] **Frage 1: Systemoperationen und Protokollautomaten**
> Welche der folgenden Aussagen beschreibt **korrekt** die Beziehung zwischen der Systemoperation `manageMembers(token: Token)` und dem Konzept des Protokollautomaten (State Machine) im Kontext der Vorlesung?
>
> - [ ] A) Der Protokollautomat ersetzt die Notwendigkeit von Vor- und Nachbedingungen, da er alle möglichen Zustandsübergänge explizit modelliert.
> - [ ] B) Die Operation `manageMembers` kann nur in einem Zustand aufgerufen werden, der durch den Protokollautomaten als "initialisiert" definiert ist, und führt zu einem Zustand, in dem Mitglieder bearbeitet werden können.
> - [ ] C) Der Protokollautomat ist nur für die Darstellung der Observer-Pattern-Implementierung in MVC relevant, nicht jedoch für Systemoperationen wie `manageMembers`.
> - [ ] D) Die Vor- und Nachbedingungen der Operation `manageMembers` sind redundant, da der Protokollautomat alle möglichen Fehlerfälle (z. B. ungültiges Token) automatisch abdeckt.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A)** ist falsch, weil Protokollautomaten die Vor- und Nachbedingungen **ergänzen**, aber nicht ersetzen. Die Vorlesung betont explizit die Kombination beider Konzepte (siehe Folie 266).
> > - **B)** ist korrekt: Die Vorbedingung der Operation `manageMembers` erfordert einen initialisierten Systemzustand (Folie 261), und die Nachbedingung beschreibt den Zustand, in dem Mitglieder bearbeitet werden können. Der Protokollautomat visualisiert genau diese Zustandsübergänge (Folie 266).
> > - **C)** ist falsch, da der Protokollautomat in der Vorlesung als zentrales Werkzeug für **alle** Systemoperationen (nicht nur Observer) eingeführt wird (Folie 266–267).
> > - **D)** ist falsch, weil der Protokollautomat zwar Fehlerfälle modellieren kann (z. B. durch Zustände wie "Token invalid"), aber die expliziten Ausnahmen (z. B. "Datenbank nicht erreichbar") weiterhin in den Operationen dokumentiert werden müssen (Folie 261).

---

> [!question] **Frage 2: Komplexe Zustände und Synchronisation**
> In einem Zustandsdiagramm für ein Modulprüfungssystem sollen zwei parallele Aktivitäten modelliert werden:
> 1. **Labor Teil 1** und **Labor Teil 2** (müssen sequenziell durchlaufen werden).
> 2. **Vorlesung besuchen** (kann parallel zu den Laborteilen stattfinden).
>
> Welche der folgenden Aussagen zur Synchronisation dieser Aktivitäten ist **falsch**?
>
> - [ ] A) Der Protokollautomat muss einen **History-Zustand** verwenden, um den Fortschritt im Labor nach einem Abbruch wiederherzustellen.
> - [ ] B) Die Prüfung darf erst abgelegt werden, wenn **alle** parallelen Aktivitäten (Labor Teil 1, Labor Teil 2, Vorlesung) abgeschlossen sind.
> - [ ] C) Die Synchronisation kann durch **Synchronisationsbalken** (z. B. `*`) dargestellt werden, um sicherzustellen, dass die Prüfung erst nach Abschluss des Labors gestartet wird.
> - [ ] D) Der Zustand "Modulprüfung ablegen" ist ein **Endzustand**, der nur erreicht wird, wenn alle vorherigen Zustände erfolgreich durchlaufen wurden.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: A**
> >
> > *Erklärung*:
> > - **A)** ist **falsch**, weil History-Zustände (`H`) verwendet werden, um den letzten Zustand **innerhalb eines zusammengesetzten Zustands** wiederherzustellen (Folie 270). Für die **parallele Synchronisation** von unabhängigen Aktivitäten (wie Labor und Vorlesung) sind **Synchronisationsbalken** (`*`) oder **Join-Knoten** erforderlich (Folie 272), nicht History-Zustände.
> > - **B)** ist korrekt: Die Prüfung ist ein **Endzustand**, der nur erreicht wird, wenn alle parallelen Aktivitäten abgeschlossen sind (Folie 271).
> > - **C)** ist korrekt: Synchronisationsbalken werden in der Vorlesung explizit für die Koordination paralleler Aktivitäten verwendet (Folie 272).
> > - **D)** ist korrekt: Der Zustand "Modulprüfung ablegen" ist ein Endzustand, der nur bei Erfolg aller vorherigen Schritte erreicht wird (Folie 271).

---
> [!question] **Frage 3: Observer-Pattern und Systemoperationen**
> Welche der folgenden Aussagen zum **Observer-Pattern** im Kontext der `manageMembers`-Operation und des MVC-Modells ist **korrekt**?
>
> - [ ] A) Der Observer wird nur benachrichtigt, wenn sich der **controllerState** im Controller ändert, nicht jedoch bei Änderungen im **viewState** oder **business logic**.
> - [ ] B) Die `notify()`-Methode des Subjects sollte **alle** Observer benachrichtigen, unabhängig davon, ob die Änderung für sie relevant ist (z. B. nur Änderungen an Mitgliedern).
> - [ ] C) Die Systemoperation `manageMembers` löst eine `notify()`-Aktion aus, sobald Mitgliederdaten aus der Datenbank geladen wurden, um die Views zu aktualisieren.
> - [ ] D) Der Observer-Mechanismus ist nur für die **View**-Komponente relevant und hat keine Auswirkungen auf die **Model**- oder **Controller**-Schicht.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A)** ist falsch: Der Observer wird bei **allen Änderungen im Subject** benachrichtigt, unabhängig davon, welcher Zustand sich ändert (Folie 264). Die Relevanz der Änderung wird erst in der `update()`-Methode des Observers geprüft.
> > - **B)** ist falsch: Die Vorlesung betont, dass die Beobachtung **individualisiert** werden kann (Folie 265). Es ist nicht zwingend erforderlich, alle Observer zu benachrichtigen – nur die relevanten.
> > - **C)** ist **korrekt**: Systemoperationen wie `manageMembers` führen zu Änderungen im System (z. B. Laden von Mitgliederdaten), die über `notify()` an die Observer (Views) propagiert werden (Folie 265).
> > - **D)** ist falsch: Der Observer-Mechanismus verbindet **alle drei MVC-Komponenten** (Model, View, Controller). Das Model ist das Subject, das Views (Observer) benachrichtigt (Folie 264).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Zustandsmanagement in Protokoll-Automaten**
> Welche der folgenden Aussagen beschreibt **korrekt** die Rolle von Guard-Conditions in einem Protokoll-Automaten?
>
> - [ ] A) Guard-Conditions lösen Systemoperationen aus, sobald ein Zustand erreicht wird.
> - [ ] B) Guard-Conditions definieren die Reihenfolge der Zustandsübergänge unabhängig von Parametern.
> - [ ] C) Guard-Conditions sind Bedingungen, die sich auf Parameter der Systemoperation und den aktuellen Zustand beziehen und den Übergang zwischen Zuständen steuern.
> - [ ] D) Guard-Conditions ersetzen die Action-Expressions, um Ereignisse zu beschreiben.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A** ist falsch, da Guard-Conditions **nicht** Systemoperationen auslösen, sondern Bedingungen für Übergänge darstellen.
> > - **B** ist falsch, weil Guard-Conditions **abhängig von Parametern und Zustand** sind, nicht unabhängig.
> > - **C** ist korrekt: Guard-Conditions prüfen Bedingungen (z. B. Token-Validierung) und steuern so, ob ein Zustandsübergang erlaubt ist (vgl. Slide 275 und 282).
> > - **D** ist falsch, da Guard-Conditions und Action-Expressions unterschiedliche Rollen haben: Guard-Conditions prüfen, Action-Expressions beschreiben Ereignisse (Slide 275).

---

> [!question] **Frage 2: Implementierung der Zustandsmaschine und Observer-Pattern**
> Welche der folgenden Aussagen beschreibt **korrekt** die Implementierung der Zustandsmaschine (`StateMachineImpl`) und ihre Integration mit dem Observer-Pattern?
>
> - [ ] A) Die `StateMachineImpl` verwaltet Zustände, aber benachrichtigt Observer erst nach Abschluss aller Systemoperationen.
> - [ ] B) Die `StateMachineImpl` implementiert das Observer-Pattern, indem sie `attach()` und `detach()` nutzt, um Observer zu registrieren und bei Zustandsänderungen zu informieren.
> - [ ] C) Die `StateMachineImpl` delegiert die Zustandsverwaltung an die Fassaden (`ManagementFacade`), während Observer nur für die UI zuständig sind.
> - [ ] D) Die `StateMachineImpl` verwendet `synchronized` nur für die Methode `getState()`, um Nebenläufigkeit zu sichern.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist falsch, da Observer **sofort** bei Zustandsänderungen benachrichtigt werden (vgl. `setState()` in Slide 281: `observers.forEach(obs -> obs.update(state))`).
> > - **B** ist korrekt: Die `StateMachineImpl` implementiert das Observer-Pattern durch `attach()`/`detach()` und benachrichtigt Observer bei Zustandsänderungen (Slide 279 und 281).
> > - **C** ist falsch, da die Zustandsmaschine **zentral** für die Zustandsverwaltung zuständig ist (Slide 280) und Observer nicht nur UI-Komponenten sind.
> > - **D** ist falsch, weil `synchronized` in `setState()` **alle** Zustandsänderungen sichert (Slide 287), nicht nur `getState()`.

---
> [!question] **Frage 3: Rolle von Fassaden in der Architektur**
> Welche der folgenden Aussagen beschreibt **korrekt** die Funktion einer Fassade (`ManagementFacade`) im Kontext der vorgestellten Architektur?
>
> - [ ] A) Eine Fassade dient ausschließlich dazu, die Benutzeroberfläche von der Logik zu trennen.
> - [ ] B) Eine Fassade kapselt ein Subsystem, überwacht Zustände, sichert Nebenläufigkeit ab und delegiert Systemoperationen an die zuständigen Objekte.
> - [ ] C) Eine Fassade ersetzt die Zustandsmaschine, indem sie alle Systemoperationen direkt ausführt.
> - [ ] D) Eine Fassade wird nur für die Session-Verwaltung verwendet und hat keine Verbindung zur Zustandsmaschine.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist falsch, da eine Fassade **nicht nur UI trennt**, sondern auch Subsysteme kapselt (Slide 283–284).
> > - **B** ist korrekt: Die Fassade überwacht Zustände (via `StateMachine`), sichert Nebenläufigkeit (z. B. `synchronized` in Slide 287) und delegiert Operationen an Komponenten wie `ManageMembers` (Slide 284 und 287).
> > - **C** ist falsch, da die Fassade **nicht die Zustandsmaschine ersetzt**, sondern mit ihr zusammenarbeitet (Slide 287: `stateMachine.getState()`).
> > - **D** ist falsch, weil die Fassade **direkt mit der Zustandsmaschine interagiert** (Slide 287) und nicht nur für Sessions zuständig ist (Slide 288).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien (Slides 290–304), formatiert für Obsidian:

---

> [!question] **Frage 1: Verantwortungszuweisung nach dem *Experten-Prinzip***
> Welche der folgenden Aussagen beschreibt **korrekt** die Anwendung des *Experten-Prinzips* (Information Expert) aus Slide 297?
>
> - [ ] A) Eine Klasse sollte eine Verantwortung übernehmen, wenn sie die notwendigen Informationen **direkt speichert** oder **berechnen kann**, selbst wenn sie nicht die Hauptverantwortung für das Objekt hat.
> - [ ] B) Die Verantwortung für eine Aktion liegt immer bei der Klasse, die die Aktion **auslöst** (z. B. ein Benutzer oder ein externes System).
> - [ ] C) Das *Experten-Prinzip* priorisiert die Zuweisung von Verantwortlichkeiten an Klassen, die **am häufigsten mit anderen Klassen interagieren**, unabhängig von ihrem Wissensstand.
> - [ ] D) Verantwortlichkeiten sollten immer an **abstrakte Schnittstellen** delegiert werden, um Flexibilität zu gewährleisten, selbst wenn diese keine relevanten Daten besitzen.
>
> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: A**
> >
> > *Erklärung*:
> > Das *Experten-Prinzip* (Slide 297) besagt, dass eine Klasse die Verantwortung für eine Aktion übernehmen sollte, wenn sie **alle notwendigen Informationen** besitzt (z. B. durch gespeicherte Daten oder abgeleitete Berechnungen).
> > - **Option A** ist korrekt, da sie die Definition präzise wiedergibt.
> > - **Option B** ist falsch, weil das Prinzip nicht die *Auslöser*-Klasse, sondern die *informierte* Klasse priorisiert.
> > - **Option C** ist falsch, da Interaktionshäufigkeit kein Kriterium ist – entscheidend ist das **Wissen**.
> > - **Option D** ist falsch, da das Prinzip **konkrete Klassen** mit Wissen bevorzugt, nicht Schnittstellen.

---

> [!question] **Frage 2: Unterschied zwischen *Sequenzdiagramm* und *Kommunikationsdiagramm***
> Welche Aussage zu den in Slide 299 beschriebenen Interaktionsdiagramm-Typen ist **falsch**?
>
> - [ ] A) Ein *Sequenzdiagramm* betont den **zeitlichen Ablauf** der Nachrichten zwischen Objekten, während ein *Kommunikationsdiagramm* die **räumliche Anordnung** der Objekte zeigt.
> - [ ] B) Beide Diagrammtypen können **Schleifen** (z. B. `loop`) und **Bedingungen** (z. B. `alt`) darstellen, aber die Syntax unterscheidet sich.
> - [ ] C) *Kommunikationsdiagramme* eignen sich besser zur Visualisierung von **komplexen Systemoperationen**, da sie die Objektstruktur klarer abbilden.
> - [ ] D) In einem *Sequenzdiagramm* wird die **Lebenslinie** eines Objekts durch eine vertikale Linie dargestellt, die mit Steuerungsfoki (Activations) annotiert ist.
>
> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **Option A** ist korrekt: Sequenzdiagramme zeigen den **zeitlichen Ablauf** (Slide 300–302), Kommunikationsdiagramme die **Objektbeziehungen** (Slide 299).
> > - **Option B** ist korrekt, da beide Diagrammtypen **Kontrollstrukturen** wie Schleifen oder Alternativen darstellen können (Slides 303–304).
> > - **Option C** ist **falsch**, weil **Sequenzdiagramme** besser für komplexe Systemoperationen geeignet sind (Slide 298: "Ziel ist es, jede Funktion durch eine Menge interagierender Objekte zu beschreiben").
> > - **Option D** ist korrekt: Lebenslinien und Steuerungsfoki sind zentrale Elemente von Sequenzdiagrammen (Slide 300).

---
> [!question] **Frage 3: Rolle der *Fassade* im Software-Design**
> Welche Aussage zur Implementierung einer *Fassade* (Facade) nach Slide 292 ist **nicht zutreffend**?
>
> - [ ] A) Eine Fassade kann als **statische Variable** in einem Interface definiert werden, um eine zentrale Zugriffsstelle zu schaffen.
> - [ ] B) In Frameworks wie Spring wird eine Fassade typischerweise als **`@Component` mit `@ApplicationScope`** annotiert, um als Singleton zu agieren.
> - [ ] C) Die Fassade delegiert Aufgaben an **untergeordnete Komponenten** (z. B. `StateMachine`), ohne selbst Logik zu implementieren.
> - [ ] D) Eine Fassade sollte **alle Verantwortlichkeiten** eines Subsystems übernehmen, um die Kopplung zwischen Client und Subsystem zu erhöhen.
>
> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **Option A** ist korrekt: Slide 292 zeigt die Definition einer statischen `FACTORY`-Variable in einem Interface.
> > - **Option B** ist korrekt: Die Annotation `@Component` mit `@ApplicationScope` (Slide 292) ist eine typische Spring-Implementierung für Fassaden.
> > - **Option C** ist korrekt: Die Fassade **delegiert** Aufgaben (z. B. an `StateMachine`), wie in Slide 292 gezeigt (`class ManagementFacade implements MemberManagement` mit `@Autowired`).
> > - **Option D** ist **falsch**, weil eine Fassade **gerade die Kopplung reduzieren** soll (Slide 297: "Lose Kopplung"). Sie übernimmt **keine** Verantwortlichkeiten des Subsystems, sondern **kapselt** sie.

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien, formatiert für Obsidian:

---

> [!question] **Frage 1: Fragment-Typen in Sequenzdiagrammen**
> Welche der folgenden Aussagen zu den in der Vorlesung vorgestellten Fragment-Typen ist **falsch**?
> - [ ] A) Das `strict`-Fragment erzwingt eine strikte zeitliche Abfolge der Nachrichten **auch über Lebensliniengrenzen hinweg**.
> - [ ] B) Das `seq`-Fragment dient zur Abgrenzung reihenfolgetreuer Abläufe, hat aber **keine strikte Semantik** wie `strict`.
> - [ ] C) Das `ignore{N}`-Fragment markiert Nachrichten, die **technisch notwendig**, aber für den aktuellen Sachverhalt irrelevant sind.
> - [ ] D) Das `consider{N}`-Fragment hebt **alle Nachrichten** eines Sequenzdiagramms als besonders bedeutend hervor, unabhängig von ihrem Inhalt.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A**, **B** und **C** sind korrekt: `strict` erzwingt strikte Reihenfolge (auch über Lebenslinien), `seq` grenzt reihenfolgetreue Abläufe ab (ohne strikte Semantik), und `ignore{N}` markiert irrelevante, aber notwendige Nachrichten.
> > - **D ist falsch**, weil `consider{N}` **nur bestimmte Nachrichten** (z. B. mit Namen `N`) als bedeutend hervorhebt – nicht alle Nachrichten. Die korrekte Syntax wäre z. B. `consider{getTitle()}`.

---

> [!question] **Frage 2: Parallelität und Coregion in Sequenzdiagrammen**
> Betrachten Sie die beiden folgenden Fragmente aus den Folien (Slide 310 und 311):
> - **Fragment 1 (Slide 310)**: `par`-Fragment mit zwei parallelen Nachrichten (`getMember()` und `getDepartment()`).
> - **Fragment 2 (Slide 311)**: Zwei `Coregion`-Blöcke für dieselben Nachrichten.
> Welche der folgenden Aussagen beschreibt den **wichtigsten Unterschied** zwischen diesen beiden Ansätzen?
> - [ ] A) Das `par`-Fragment erlaubt **beliebige zeitliche Überlappung** der Nachrichten, während `Coregion` **keine Überlappung** zulässt.
> - [ ] B) Das `par`-Fragment definiert **unabhängige parallele Abläufe**, während `Coregion` **zeitliche Unordnung innerhalb eines Ablaufs** erlaubt.
> - [ ] C) `Coregion` ist eine **Erweiterung von `strict`**, während `par` eine **Erweiterung von `seq`** ist.
> - [ ] D) Beide Fragmente sind **semantisch identisch**, da sie Parallelität darstellen – der Unterschied liegt nur in der Syntax.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A ist falsch**: `par` erlaubt **parallele Ausführung** (zeitliche Überlappung möglich), während `Coregion` **keine strikte Reihenfolge** innerhalb des Blocks erzwingt, aber auch keine echte Parallelität modelliert.
> > - **B ist korrekt**: `par` definiert **unabhängige parallele Abläufe** (z. B. zwei Threads), während `Coregion` **zeitliche Unordnung innerhalb eines Ablaufs** erlaubt (z. B. Nachrichten können in beliebiger Reihenfolge auftreten, aber nicht parallel).
> > - **C ist falsch**: `Coregion` ist **keine Erweiterung von `strict`**, sondern ein separates Konzept für lose zeitliche Abhängigkeiten.
> > - **D ist falsch**: Die Fragmente sind **nicht semantisch identisch** – sie dienen unterschiedlichen Zwecken (echte Parallelität vs. lose Reihenfolge).

---

> [!question] **Frage 3: Verantwortliche in System-Sequenzdiagrammen**
> In Slide 315–317 wird das Prinzip der "Verantwortlichen" für Systemoperationen erläutert. Welche der folgenden Aussagen ist **kein gültiges Kriterium** für die Auswahl eines Verantwortlichen gemäß dem vorgestellten Managementprinzip?
> - [ ] A) Der Verantwortliche sollte **ein Manager-Objekt** sein, das alle Operationen eines Use Cases bündelt (z. B. `ManageMembers`).
> - [ ] B) Der Verantwortliche muss **immer eine Instanz der Systemklasse** sein (z. B. `MyClub`), die das gesamte System repräsentiert.
> - [ ] C) Der Verantwortliche sollte **naheliegend, leicht identifizierbar und unverwechselbar** sein (z. D. `ManageMembers` für den Use Case "Mitglieder verwalten").
> - [ ] D) Der Verantwortliche kann ein **Port oder eine Schnittstelle** sein, die den Use Case nach außen repräsentiert (z. B. `ManagerImpl`).

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A ist korrekt**: Ein Use-Case-Manager (z. B. `ManageMembers`) ist ein typischer Verantwortlicher, der alle Operationen eines Use Cases bündelt.
> > - **B ist falsch**: Der Verantwortliche **muss nicht zwingend die Systemklasse** (z. B. `MyClub`) sein. Stattdessen wird ein **spezialisierter Manager** (z. B. `ManageMembers`) bevorzugt, der den Use Case direkt repräsentiert.
> > - **C ist korrekt**: Das Prinzip betont, dass der Verantwortliche **naheliegend und unverwechselbar** sein sollte.
> > - **D ist korrekt**: Ein Verantwortlicher kann auch ein **Port oder eine Schnittstelle** sein (z. B. `ManagerImpl`), der den Use Case nach außen kapselt.

---
Diese Fragen decken zentrale Konzepte der Sequenzdiagramme (Fragmente, Parallelität) und des Designprozesses (Verantwortliche) ab und erfordern ein tiefes Verständnis der Vorlesungsinhalte. Die Distraktoren sind so gewählt, dass sie plausible, aber eindeutig falsche Alternativen bieten.

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien (320–325), die das Verständnis für Software-Engineering-Konzepte wie Iterationsplanung, Design vs. Implementierung und Risikomanagement prüfen:

---

> [!question] **Frage 1: Iterationsplanung und Design**
> Welche Aussage zur Beziehung zwischen Design und Implementierung in agilen Iterationen ist **falsch**?
> - [ ] A) Design und Implementierung sind in agilen Projekten eng verzahnt und sollten nicht strikt getrennt werden.
> - [ ] B) Ein vollständiges Design vor der Implementierung zu erstellen, ist oft ineffizient, da Fehler erst spät erkannt werden.
> - [ ] C) CI/CD-Pipelines ermöglichen es, Designfehler schneller zu identifizieren und zu korrigieren als klassische Wasserfallansätze.
> - [ ] D) Die Folien empfehlen, in jeder Iteration zunächst ein umfassendes Activity-Diagram für *alle* geplanten Use Cases zu erstellen, bevor mit der Implementierung begonnen wird.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A)** Richtig: Die Folien (Slide 323) betonen, dass Design und Implementierung kaum trennbar sind.
> > - **B)** Richtig: Slide 324 warnt davor, dass ein vollständiges Design vor der Implementierung zu spät Fehler aufdeckt.
> > - **C)** Richtig: CI/CD (Slide 324) beschleunigt die Fehlererkennung durch automatisierte Tests.
> > - **D)** **Falsch**: Slide 322 warnt explizit davor, *alle* Use Cases in einer Iteration zu designen („Dies ist nicht unbedingt eine gute Idee!“). Stattdessen soll iterativ vorgegangen werden.

---

> [!question] **Frage 2: Risikomanagement im Spiralmodell**
> Welche der folgenden Aussagen zum Spiralmodell (Slide 325) ist **korrekt**?
> - [ ] A) Das Spiralmodell sieht vor, dass in jeder Iteration *nur* die Implementierung (Phase 3) durchgeführt wird, ohne Risikoanalyse.
> - [ ] B) Die erste Phase des Spiralmodells („Bestimme Ziele, Alternativen, Beschränkungen“) entspricht der klassischen Anforderungsanalyse.
> - [ ] C) Das Spiralmodell verzichtet vollständig auf iterative Prototypen und setzt stattdessen auf lineare Phasen.
> - [ ] D) Phase 4 („Plane die nächste Phase“) ist im Spiralmodell optional und wird nur bei Projektabschluss durchgeführt.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A)** Falsch: Phase 1 (Ziele/Alternativen) und Phase 2 (Risikoanalyse) sind integraler Bestandteil jeder Iteration.
> > - **B)** **Richtig**: Die erste Phase des Spiralmodells (nach Boehm) entspricht der klassischen Anforderungsanalyse und Zieldefinition.
> > - **C)** Falsch: Das Spiralmodell *basiert* auf iterativen Prototypen und Risikoreduktion.
> > - **D)** Falsch: Phase 4 ist zentral, um die nächste Iteration zu planen (z. B. neue Use Cases oder Anpassungen).

---
> [!question] **Frage 3: Systemoperationen und Architektur**
> Welche Aussage zu den „nächsten Schritten“ in der Use-Case-Entwicklung (Slide 322/324) ist **falsch**?
> - [ ] A) Mockups sollten erst angepasst werden, nachdem die Systemoperationen designet wurden, um Konsistenz zu gewährleisten.
> - [ ] B) Die Architektur sollte *nach* der Implementierung aller Systemoperationen angepasst werden, um technische Schulden zu vermeiden.
> - [ ] C) Activity-Diagramme helfen, neue Systemoperationen zu identifizieren, indem sie den Datenfluss visualisieren.
> - [ ] D) CI/CD-Pipelines unterstützen die schnelle Validierung von Implementierungen, indem sie automatisierte Tests ausführen.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A)** Richtig: Mockups (UI-Entwürfe) sollten auf dem Design der Systemoperationen basieren (Slide 322: „Mockups anpassen“ *nach* „Systemoperationen designen“).
> > - **B)** **Falsch**: Slide 324 betont, dass die Architektur *gemäß Design* von Komponente zu Komponente fortschreitet – Anpassungen sollten *vor* der Implementierung erfolgen, nicht danach.
> > - **C)** Richtig: Activity-Diagramme zeigen Prozesse und helfen, fehlende Operationen zu erkennen (Slide 322).
> > - **D)** Richtig: CI/CD (Slide 324) beschleunigt die Validierung durch automatisierte Tests.