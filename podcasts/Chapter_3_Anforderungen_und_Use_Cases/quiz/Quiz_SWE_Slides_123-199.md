---
type: chapter_quiz
chapter: 3
range: "123-199"
generated_at: 2026-06-06 16:33:00
tags:
  - software_engineering
  - quiz
  - chapter_quiz_3
---

# 🧠 Chapter 3 Quiz: Anforderungen und Use Cases

**Slide Range:** 123-199

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Welche der folgenden Aussagen zur Phase "Aufgabe verstehen" im Vorprojekt ist **falsch**?**
> - [ ] A) Ein zentraler Bestandteil ist die Erstellung eines ersten Analysemodells, um die Problemdomäne zu erfassen.
> - [ ] B) Die erste Systemarchitektur wird direkt aus dem Analysemodell und den nicht-funktionalen Anforderungen abgeleitet.
> - [ ] C) Ein Prototyp ist **obligatorisch** und muss immer erstellt werden, um Risiken zu minimieren.
> - [ ] D) Use Cases helfen dabei, zentrale Geschäftsvorfälle zu strukturieren und in Beziehung zu setzen.

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A** ist korrekt: Ein Analysemodell ist Teil der Phase "Aufgabe verstehen" (Slide 127).
> > - **B** ist korrekt: Die Systemarchitektur ergibt sich aus dem Analysemodell und nicht-funktionalen Requirements (Slide 129).
> > - **C** ist **falsch**: Ein Prototyp ist **optional** (Slide 130) und nicht zwingend erforderlich.
> > - **D** ist korrekt: Use Cases dienen der Strukturierung von Geschäftsvorfällen (Slide 129).

---

> [!question] **Frage 2: Welche Aussage zur Dauer von Iterationen in SCRUM ist **korrekt**?**
> - [ ] A) Iterationen sollten idealerweise **1 Woche** dauern, um maximale Flexibilität zu gewährleisten.
> - [ ] B) Eine Iteration von **6 Monaten** ist optimal, da sie genug Zeit für komplexe Anforderungen lässt.
> - [ ] C) Iterationen sollten **nicht kürzer als 2 Wochen** und **nicht länger als 2 Monate** sein, um Feedback zu ermöglichen.
> - [ ] D) Die Dauer einer Iteration wird ausschließlich vom Product Owner festgelegt, unabhängig von Teamkapazitäten.

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A** ist falsch: Zu kurze Iterationen (z. B. 1 Woche) erschweren die Umsetzung sinnvoller Funktionalität (Slide 135).
> > - **B** ist falsch: Zu lange Iterationen (z. B. 6 Monate) bergen das Risiko, Komplexität falsch einzuschätzen (Slide 135).
> > - **C** ist **korrekt**: Die Faustregel für Iterationsdauer ist 2 Wochen bis 2 Monate (Slide 135).
> > - **D** ist falsch: Die Dauer wird im Team abgestimmt (Slide 134), nicht vom Product Owner allein.

---

> [!question] **Frage 3: Welche der folgenden Aktivitäten gehört **nicht** zu den Schritten innerhalb einer Iteration?**
> - [ ] A) Analyse des Problemraums (z. B. Requirements erfassen).
> - [ ] B) Erstellung eines vorläufigen Projektplans für das gesamte Projekt.
> - [ ] C) Design des Lösungsraums (z. B. Architekturentscheidungen).
> - [ ] D) Implementierung der getroffenen Designentscheidungen in Code.

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist korrekt: Analyse ist ein zentraler Schritt (Slide 137).
> > - **B** ist **falsch**: Ein **vorläufiger Projektplan für das gesamte Projekt** wird in der Phase I (Evaluierung) erstellt (Slide 125), nicht innerhalb einer Iteration.
> > - **C** ist korrekt: Design ist Teil der Iteration (Slide 137).
> > - **D** ist korrekt: Implementierung ist der dritte Schritt (Slide 137).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien, formatiert für Obsidian:

---

> [!question] **Frage 1: Unterschied zwischen funktionalen und nicht-funktionalen Anforderungen**
> Welche der folgenden Aussagen beschreibt **korrekt** den Unterschied zwischen funktionalen und nicht-funktionalen Anforderungen?
>
> - [ ] A) Funktionale Anforderungen sind immer subjektiv messbar, während nicht-funktionale Anforderungen objektiv überprüfbar sind.
> - [ ] B) Funktionale Anforderungen definieren *was* das System tun soll, während nicht-funktionale Anforderungen *wie gut* es diese Aufgaben erfüllt.
> - [ ] C) Nicht-funktionale Anforderungen lassen sich immer durch Metriken wie Antwortzeit oder Fehlerrate messen, funktionale Anforderungen nie.
> - [ ] D) Technische Vorgaben (z. B. Programmiersprache) sind immer nicht-funktional, da sie die Implementierung einschränken.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist falsch, weil funktionale Anforderungen objektiv sind (z. B. "Das System muss Mitglieder speichern können"), während nicht-funktionale Anforderungen subjektiv sein können (z. B. "Das System soll benutzerfreundlich sein").
> > - **B** ist korrekt: Funktionale Anforderungen beschreiben die **Funktionalität** (z. B. "E-Mail versenden"), nicht-funktionale Anforderungen die **Qualität** (z. B. "E-Mail muss innerhalb von 2 Sekunden versendet werden").
> > - **C** ist falsch, weil auch funktionale Anforderungen messbar sein können (z. B. "Das System muss 1000 Mitglieder speichern können").
> > - **D** ist falsch, weil technische Vorgaben **funktional** sein können, wenn sie direkt umsetzbar sind (z. B. "Das System muss in Java implementiert werden").

---

> [!question] **Frage 2: Testebenen und ihre Ziele**
> Welche der folgenden Aussagen zur **Hierarchie der Testebenen** (Modultests, Komponentenintegrationstests, Systemtests) ist **falsch**?
>
> - [ ] A) Modultests verifizieren die korrekte Implementierung einzelner Operationen (z. B. eine Methode zur Berechnung von Mitgliedsbeiträgen).
> - [ ] B) Komponentenintegrationstests überprüfen, wie mehrere Module zusammenarbeiten, um eine größere Funktion zu erfüllen (z. B. Mitgliederverwaltung + Beitragserfassung).
> - [ ] C) Systemtests validieren die Anforderungen des Kunden, indem sie das gesamte System in einer produktionsähnlichen Umgebung testen.
> - [ ] D) Modultests sind immer Black-Box-Tests, da sie keine Kenntnis der Implementierung erfordern.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A**, **B** und **C** sind korrekte Beschreibungen der Testebenen (vgl. Slide 138).
> > - **D** ist falsch, weil Modultests **sowohl** White-Box- **als auch** Black-Box-Tests sein können. Bei White-Box-Tests nutzt man Wissen über die Implementierung (z. B. interne Logik einer Methode), während Black-Box-Tests nur die Spezifikation prüfen.

---
> [!question] **Frage 3: Metriken für nicht-funktionale Anforderungen**
> Welche der folgenden **Metriken** ist **nicht** geeignet, um die nicht-funktionale Anforderung **"Skalierbarkeit"** zu messen?
>
> - [ ] A) Die Zeit, die das System benötigt, um bei einer Verdopplung der Nutzerzahl die gleiche Antwortzeit zu halten.
> - [ ] B) Die Anzahl der Fehler pro 1000 Transaktionen.
> - [ ] C) Die maximale Anzahl gleichzeitiger Nutzer, die das System ohne Performance-Einbruch bedienen kann.
> - [ ] D) Die Zeit, die das System benötigt, um zusätzliche Server-Ressourcen zu aktivieren.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A**, **C** und **D** sind gültige Metriken für Skalierbarkeit (vgl. Slide 148):
> >   - **A** misst horizontale Skalierbarkeit (Performance bleibt stabil).
> >   - **C** misst die Kapazitätsgrenze.
> >   - **D** misst die Reaktionszeit auf Skalierungsanforderungen.
> > - **B** misst die **Zuverlässigkeit** (Fehlerrate), nicht die Skalierbarkeit. Skalierbarkeit bezieht sich auf die Fähigkeit, mit wachsender Last umzugehen, nicht auf Fehlerhäufigkeit.

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien, formatiert für Obsidian:

---

> [!question] **Frage 1: Welche Aussage zur Rolle von Use Cases im Software-Engineering ist korrekt?**
> - [ ] A) Use Cases dienen ausschließlich der Dokumentation von funktionalen Anforderungen und haben keine Auswirkungen auf Architektur oder Tests.
> - [ ] B) Use Cases sind nur für die initiale Anforderungsanalyse relevant und werden nach der Implementierung nicht mehr benötigt.
> - [ ] C) Use Cases bilden die Grundlage für Analyse, Architektur, Design, Implementierung, Tests und Evaluation des Systems.
> - [ ] D) Use Cases ersetzen klassische Anforderungsdokumente wie Lasten- und Pflichtenhefte vollständig.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > Use Cases sind zentral für den gesamten Entwicklungsprozess (vgl. Slide 155). Sie unterstützen nicht nur die Analyse, sondern auch Architektur, Design, Implementierung, Tests und Evaluation. Option A ist falsch, da Use Cases auch nicht-funktionale Anforderungen abdecken können. Option B ist falsch, weil Use Cases während des gesamten Entwicklungszyklus relevant bleiben. Option D ist übertrieben, da Use Cases klassische Dokumente ergänzen, aber nicht vollständig ersetzen.

---

> [!question] **Frage 2: Welche der folgenden Aussagen zu Beziehungen zwischen Use Cases ist **falsch**?**
> - [ ] A) Die `<<include>>`-Beziehung wird verwendet, um wiederkehrende Abläufe in mehreren Use Cases zu vermeiden.
> - [ ] B) Die `<<extend>>`-Beziehung modelliert Variationen eines Basis-Use-Cases, die nur unter bestimmten Bedingungen auftreten.
> - [ ] C) Die Generalisierung zwischen Use Cases impliziert, dass der spezialisierte Use Case alle Beziehungen des generischen Use Cases erbt.
> - [ ] D) Eine `<<include>>`-Beziehung zwischen Use Case A und B bedeutet, dass B optional von A aufgerufen wird.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > Die `<<include>>`-Beziehung (Slide 165) ist **verpflichtend**: Use Case A *muss* Use Case B einbinden. Option D ist daher falsch. Die anderen Optionen sind korrekt:
> > - A: Richtig (wiederkehrende Abläufe werden zentralisiert).
> > - B: Richtig (Extension Points definieren Bedingungen für Variationen).
> > - C: Richtig (Generalisierung impliziert Vererbung aller Beziehungen, Slide 166).

---

> [!question] **Frage 3: Ein Use Case „Mitglied löschen“ soll um die Funktion erweitert werden, dass betroffene Mitglieder per E-Mail benachrichtigt werden. Welche der folgenden Modellierungsansätze ist **am besten geeignet**?**
> - [ ] A) Modellierung als separater Use Case „Mitglied per E-Mail benachrichtigen“ mit einer `<<include>>`-Beziehung zu „Mitglied löschen“.
> - [ ] B) Modellierung als Erweiterung (`<<extend>>`) des Use Cases „Mitglied löschen“ mit einem Extension Point bei der Löschbestätigung.
> - [ ] C) Modellierung als Generalisierung, bei der „Mitglied löschen mit Benachrichtigung“ eine Spezialisierung von „Mitglied löschen“ darstellt.
> - [ ] D) Modellierung als eigenständiger Use Case ohne Beziehung zu „Mitglied löschen“, da die Benachrichtigung optional ist.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Die Benachrichtigung ist eine **Variation**, die nur unter bestimmten Bedingungen (z. B. nach erfolgreicher Löschung) auftritt. Dies entspricht der `<<extend>>`-Beziehung (Slide 165, 167), bei der die Erweiterung an einem klar definierten Extension Point (hier: Löschbestätigung) hängt. Option A ist falsch, da `<<include>>` für wiederkehrende, **verpflichtende** Abläufe verwendet wird. Option C ist übertrieben, da die Benachrichtigung kein eigenständiger Use Case mit eigener Architektur ist. Option D ist falsch, weil die Benachrichtigung direkt mit dem Löschvorgang verknüpft ist.

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Modellierung von zeitlichen Abfolgen in Use-Case-Diagrammen**
> Welche der folgenden Aussagen zu Use-Case-Diagrammen und zeitlichen Abfolgen ist **korrekt**?
>
> - [ ] A) Die Beziehungen `<<extend>>` und `<<include>>` können genutzt werden, um die zeitliche Abfolge von Use Cases explizit darzustellen.
> - [ ] B) Zeitliche Abfolgen zwischen Use Cases müssen zwingend im Use-Case-Diagramm modelliert werden, da sie sonst nicht berücksichtigt werden.
> - [ ] C) Use-Case-Diagramme sind nicht dafür geeignet, zeitliche Abfolgen von Use Cases darzustellen. Diese müssen in separaten Diagrammen (z. B. Aktivitätsdiagrammen) modelliert werden.
> - [ ] D) Die Assoziation zwischen Akteuren und Use Cases impliziert automatisch eine zeitliche Abfolge, die im Diagramm nicht weiter spezifiziert werden muss.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A)** Falsch: `<<extend>>` und `<<include>>` beziehen sich nicht auf zeitliche Abfolgen, sondern auf optionale Erweiterungen oder obligatorische Inklusionen von Use Cases (vgl. Folie 168).
> > - **B)** Falsch: Zeitliche Abfolgen sind kein primäres Anliegen von Use-Case-Diagrammen. Sie werden in anderen UML-Diagrammen wie Aktivitätsdiagrammen modelliert (vgl. Folie 175).
> > - **C)** Richtig: Use-Case-Diagramme zeigen *welche* Use Cases existieren und wie sie miteinander in Beziehung stehen, aber nicht *wann* oder *in welcher Reihenfolge* sie ausgeführt werden (vgl. Folie 168).
> > - **D)** Falsch: Assoziationen zwischen Akteuren und Use Cases definieren nur die Teilnahme, nicht die zeitliche Abfolge.

---

> [!question] **Frage 2: Aktivitätsdiagramme und ihre Elemente**
> Welche der folgenden Aussagen zu Aktivitätsdiagrammen (Activity Diagrams) ist **falsch**?
>
> - [ ] A) Aktivitätsdiagramme können genutzt werden, um Geschäftsprozesse oder Workflows abzubilden, die mehrere Use Cases umfassen.
> - [ ] B) Ein `Join`-Knoten im Aktivitätsdiagramm synchronisiert mehrere eingehende Kontrollflüsse zu einem ausgehenden Fluss, während ein `Split`-Knoten einen Fluss in mehrere parallele Zweige aufteilt.
> - [ ] C) Objektknoten in Aktivitätsdiagrammen dienen ausschließlich der Darstellung von Datenflüssen und können keine Zustände von Objekten modellieren.
> - [ ] D) Swimlanes in Aktivitätsdiagrammen können Verantwortlichkeitsbereiche (z. B. Akteure oder Systeme) darstellen und sind besonders in Business-Modellen nützlich.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A)** Richtig: Aktivitätsdiagramme eignen sich für die Modellierung von Workflows und können mehrere Use Cases übergreifend darstellen (vgl. Folie 175).
> > - **B)** Richtig: `Join` und `Split` sind zentrale Elemente zur Synchronisation und Parallelisierung von Flüssen (vgl. Folie 178).
> > - **C)** **Falsch**: Objektknoten können nicht nur Datenflüsse darstellen, sondern auch Zustände von Objekten modellieren (z. B. `{weight = 1}` oder `[Zustand]`; vgl. Folie 180).
> > - **D)** Richtig: Swimlanes sind ein mächtiges Feature zur Darstellung von Verantwortlichkeiten (vgl. Folie 182).

---
> [!question] **Frage 3: Szenarien und Use-Case-Modellierung**
> Welche der folgenden Aussagen zu Szenarien in der Use-Case-Modellierung ist **korrekt**?
>
> - [ ] A) Ein Szenario beschreibt immer nur den *erfolgreichen* Pfad eines Use Cases und ignoriert Ausnahmen oder Fehlerfälle.
> - [ ] B) Je komplexer ein Use Case ist, desto weniger Szenarien werden benötigt, um ihn vollständig zu beschreiben.
> - [ ] C) Szenarien können mit verschiedenen UML-Diagrammen (z. B. Aktivitätsdiagrammen, Zustandsdiagrammen) oder rein textuell beschrieben werden.
> - [ ] D) Szenarien sind identisch mit den Beziehungen `<<extend>>` und `<<include>>` in Use-Case-Diagrammen und ersetzen diese.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A)** Falsch: Szenarien können sowohl den Hauptpfad als auch alternative Pfade oder Fehlerfälle beschreiben (vgl. Folie 173).
> > - **B)** Falsch: Komplexe Use Cases erfordern *mehr* Szenarien, um alle möglichen Interaktionen und Pfade abzudecken (vgl. Folie 173).
> > - **C)** Richtig: Szenarien sind flexible Beschreibungen von Interaktionen und können in verschiedenen Formen (Text, Diagramme) dargestellt werden (vgl. Folie 173).
> > - **D)** Falsch: Szenarien ergänzen Use-Case-Diagramme, ersetzen aber nicht die Beziehungen `<<extend>>` und `<<include>>`. Diese Beziehungen strukturieren die Use Cases selbst (vgl. Folie 168).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Analyse der Problemdomäne**
> Welche der folgenden Aussagen beschreibt **korrekt** den Unterschied zwischen der Analyse der Problemdomäne und der Lösungsspezifikation in der Software-Engineering-Analyse?
>
> - [ ] A) Die Analyse der Problemdomäne konzentriert sich auf die technische Implementierung der Software, während die Lösungsspezifikation die Anforderungen der Stakeholder erfasst.
> - [ ] B) Die Analyse der Problemdomäne identifiziert Objekte und Beziehungen in der realen Welt, während die Lösungsspezifikation die technische Architektur der Software definiert.
> - [ ] C) Die Analyse der Problemdomäne priorisiert Use Cases nach technischen Machbarkeitskriterien, während die Lösungsspezifikation die Benutzeranforderungen ignoriert.
> - [ ] D) Die Analyse der Problemdomäne und die Lösungsspezifikation sind identisch, da beide die Software-Architektur beschreiben.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist falsch, weil die Analyse der Problemdomäne **nicht** die technische Implementierung, sondern die **Problemdomäne** (reale Welt) untersucht.
> > - **B** ist korrekt: Die Analyse der Problemdomäne sucht nach **Objekten und Beziehungen in der realen Welt** (z. B. "Mitglied", "Abteilung"), während die Lösungsspezifikation die **technische Umsetzung** (z. B. Klassen, Datenbanktabellen) definiert.
> > - **C** ist falsch, weil die Analyse der Problemdomäne **nicht** technische Machbarkeit priorisiert, sondern die **Anforderungen der Stakeholder** erfasst.
> > - **D** ist falsch, da die beiden Schritte **unterschiedliche Ziele** verfolgen: Analyse der Problemdomäne vs. technische Lösungsspezifikation.

---

> [!question] **Frage 2: Identifikation von Objekten vs. Attributen**
> Im Use Case "Mitglieder verwalten" wird der Status eines Mitglieds als `status: Status = aktiv` modelliert. Welche der folgenden Aussagen ist **falsch**?
>
> - [ ] A) Der Status sollte als **eigenständiges Konzept (Objekt)** modelliert werden, wenn er komplexe Logik enthält (z. B. Validierungsregeln).
> - [ ] B) Der Status ist ein **Attribut**, wenn er nur einfache Werte wie "aktiv" oder "passiv" annimmt und keine weiteren Eigenschaften hat.
> - [ ] C) Faustregel: Dinge, die man "anfassen" kann (z. B. "Mitglied"), sind immer Objekte, während abstrakte Konzepte wie "Status" Attribute sein müssen.
> - [ ] D) Falls unsicher, sollte man sich für ein **Objekt** entscheiden, um Flexibilität zu gewährleisten.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A** ist richtig: Komplexe Logik (z. B. Statusübergänge) spricht für ein **eigenständiges Objekt**.
> > - **B** ist richtig: Einfache Werte wie `status: Status = aktiv` können als **Attribut** modelliert werden.
> > - **C** ist **falsch**: Die Faustregel besagt, dass man Dinge, die man "anfassen" kann, als **Objekte** modelliert – aber **abstrakte Konzepte wie "Status"** können **sowohl Objekte als auch Attribute** sein, abhängig von ihrer Komplexität. Die Aussage ist zu absolut formuliert.
> > - **D** ist richtig: Die Vorlesung empfiehlt, bei Unsicherheit lieber ein **Objekt** zu wählen ("Mehr Konzepte sind besser als zu wenige").

---
> [!question] **Frage 3: System-Sequenz-Diagramme und Schnittstellen**
> Welche der folgenden Aussagen über **System-Sequenz-Diagramme (SSD)** und die Identifikation von Schnittstellen ist **falsch**?
>
> - [ ] A) System-Sequenz-Diagramme zeigen die **Interaktion zwischen Akteuren und dem System** sowie zwischen Systemkomponenten.
> - [ ] B) Schnittstellen im SSD verbergen sich hinter **Übergängen im Kontrollfluss**, z. B. zwischen Akteur und System oder zwischen Systemkomponenten.
> - [ ] C) Systemoperationen wie `abteilungVerlassen(abteilung: Abteilung)` werden im SSD **nicht** explizit modelliert, da sie nur in Use-Case-Beschreibungen dokumentiert werden.
> - [ ] D) Fragmente wie `loop` oder `opt` können verwendet werden, um **iterative oder optionale Abläufe** im SSD darzustellen.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A** ist richtig: SSDs visualisieren **Akteur-System-Interaktionen** und System-internen Nachrichtenaustausch.
> > - **B** ist richtig: Schnittstellen werden durch **Nachrichtenflüsse** im SSD sichtbar (z. B. Akteur → System oder System → System).
> > - **C** ist **falsch**: Systemoperationen wie `abteilungVerlassen()` werden **explizit im SSD modelliert** (z. B. als Nachricht an das System). Sie sind zentral für die Schnittstellendefinition.
> > - **D** ist richtig: Fragmente wie `loop` (Iteration) oder `opt` (optional) sind **Standardbestandteile von SSDs** (siehe Slide 193).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien, formatiert für Obsidian mit verschachtelten Callouts:

---

> [!question] **Frage 1: Welche der folgenden Aussagen beschreibt korrekt den Übergang zwischen Analyse und Design im Software Engineering?**
> - [ ] A) Im Design werden ausschließlich neue Use Cases identifiziert, die in der Analyse noch nicht betrachtet wurden.
> - [ ] B) Die Architektur wird im Design nur in der ersten Iteration festgelegt und bleibt in allen weiteren Iterationen unverändert.
> - [ ] C) Mockups und Bedienkonzepte werden erst nach der vollständigen Systemarchitektur erstellt, um die technische Machbarkeit zu gewährleisten.
> - [ ] D) Nur die bereits analysierten und verstandenen Use Cases werden im Design berücksichtigt und dienen als Grundlage für die Architektur.

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > Die Folie 199 betont, dass **nur die bereits analysierten Use Cases** im Design berücksichtigt werden (*"Nur die Use Cases kommen in Betracht, die bereits analysiert wurden!"*). Die anderen Optionen sind falsch, weil:
> > - A: Neue Use Cases werden nicht im Design identifiziert, sondern in der Analyse.
> > - B: Die Architektur wird in Iterationen erweitert und angepasst (*"kommende Iterationen: Architektur erweitern, anpassen"*).
> > - C: Mockups und Bedienkonzepte werden **vor** der Architektur erstellt (*"abhängig davon: Bedienkonzept und Mockups erstellen"*).

---

> [!question] **Frage 2: Welche der folgenden Fragen ist zentral für die Identifikation der zu realisierenden Komponenten und Schnittstellen im Design?**
> - [ ] A) Welche Programmiersprache bietet die beste Performance für die Implementierung?
> - [ ] B) Welche zusammenhängenden funktionalen Einheiten (Komponenten) müssen realisiert werden und welche Schnittstellen benötigen sie?
> - [ ] C) Wie viele Entwickler:innen werden für die Umsetzung des Projekts benötigt?
> - [ ] D) Welche Testfälle müssen für die Abnahme durch den Kunden definiert werden?

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Die Folie 198 listet explizit die zentralen Fragen für die Komponenten- und Schnittstellenidentifikation auf:
> > - *"Welche Komponenten und Schnittstellen müssen realisiert werden?"*
> > - *"Was sind die zusammenhängenden funktionalen Einheiten?"*
> > - *"Welche Schnittstellen gibt es?"*
> > Die anderen Optionen sind irrelevant für die Designphase:
> > - A: Die Programmiersprache ist eine Implementierungsentscheidung, keine Designfrage.
> > - C: Teamgröße ist ein Management-Thema, nicht Teil der technischen Designentscheidungen.
> > - D: Testfälle werden erst in späteren Phasen (z. B. Qualitätssicherung) relevant.

---

> [!question] **Frage 3: Welches Konzept wird in der Designphase **nicht** direkt aus der Analyse übernommen, sondern erst im Design konkretisiert?**
> - [ ] A) Die funktionalen Anforderungen (Use Cases).
> - [ ] B) Die Systemarchitektur (Komponenten, Konnektoren).
> - [ ] C) Die Schnittstellenspezifikationen (Operationen und deren Aufgaben).
> - [ ] D) Die Konzepte und deren Abhängigkeiten zueinander.

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Die Folien zeigen einen klaren Übergang:
> > - **Analyse**: Use Cases werden identifiziert und verstanden (Folie 199: *"Zu realisierende Use Cases festlegen"*).
> > - **Design**: Die **Systemarchitektur** (Komponenten, Konnektoren) wird **erst im Design** entworfen (*"Die Architektur entwerfen (Komponenten, Konnektoren, Module, …)"*).
> > Die anderen Optionen sind falsch, weil:
> > - A, C, D: Diese Konzepte werden bereits in der Analyse erarbeitet (Folie 198: *"Welche Operationen werden an den Schnittstellen gebraucht?"*, *"Was ist deren Aufgabe?"*, *"Welche Konzepte sind relevant?"*).
> > - Die Architektur ist das **neue** Konzept, das im Design hinzukommt.