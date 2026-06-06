---
type: quiz
chapter: 3
subtopic: "Von der Analyse zur Systemarchitektur"
format: callout
generated_at: 2026-06-06 16:28:20
tags:
  - software_engineering
  - quiz
  - chapter_3
---

# 🧠 Quiz: Von der Analyse zur Systemarchitektur

**Kapitel:** Kapitel 3: Design – Softwarearchitektur & Entwurfsmuster
**Details:** 

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zum Thema **"Von der Analyse zur Systemarchitektur"** im geforderten Format:

---

> [!question] **Frage 1: Welche der folgenden Aussagen beschreibt am präzisen die Bedeutung der Systemgrenzen in der Softwareentwicklung?**
> - [ ] A) Systemgrenzen definieren ausschließlich die technische Schnittstelle zwischen Hardware und Software.
> - [ ] B) Systemgrenzen legen fest, welche externen Dienste (z. B. Cloud-Services) in das System integriert werden dürfen.
> - [ ] C) Systemgrenzen bestimmen, welche Komponenten, Funktionen und Daten zum System gehören und welche externen Systeme oder Akteure (z. B. Benutzer, andere Systeme) außerhalb stehen.
> - [ ] D) Systemgrenzen sind nur relevant für die Dokumentation und haben keine Auswirkungen auf die Implementierung.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> Systemgrenzen sind ein **fundamentales Konzept** in der Systemanalyse und -architektur. Sie definieren, was **Teil des Systems** ist (z. B. Komponenten, Daten, Funktionen) und was **extern** bleibt (z. B. Benutzer, andere Systeme oder Dienste). Dies ist entscheidend für die **Planungssicherheit**, die **Modularisierung** und die **Vermeidung von Abhängigkeiten**. Option A ist zu technisch eingegrenzt, Option B bezieht sich nur auf einen Teilaspekt, und Option D ignoriert die praktische Relevanz für die Entwicklung.

---

> [!question] **Frage 2: Welches der folgenden Ziele ist **kein** primäres Entwurfsprinzip für offene verteilte Systeme?**
> - [ ] A) **Interoperabilität**: Fähigkeit zur Zusammenarbeit mit anderen Systemen über wohldefinierte Schnittstellen.
> - [ ] B) **Portabilität**: Möglichkeit, Anwendungen ohne Änderungen auf verschiedenen Plattformen auszuführen.
> - [ ] C) **Zentralisierung**: Konzentration aller Daten und Logik in einem einzigen, monolithischen System.
> - [ ] D) **Erweiterbarkeit**: Einfache Hinzufügung neuer Funktionen oder Komponenten ohne Systemumbau.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> Offene verteilte Systeme (z. B. Microservices, Cloud-Systeme) verfolgen **Dezentralisierung** und **Modularität**, nicht Zentralisierung. Zentralisierung widerspricht den Prinzipien der **Skalierbarkeit**, **Fehlertoleranz** und **Flexibilität**. Die anderen Optionen (A, B, D) sind zentrale Entwurfsziele offener Systeme, wie in der Vorlesung betont.

---
> [!question] **Frage 3: In der Phase der Infrastrukturplanung (Phase II der Systementwicklung) wird die Systemarchitektur konsolidiert. Welche der folgenden Maßnahmen gehört **nicht** zu den typischen Aktivitäten dieser Phase?**
> - [ ] A) Umsetzung der **Kernfunktionalität** in den ersten Iterationen.
> - [ ] B) Definition der **Schichtenarchitektur** (z. B. Präsentation, Business-Logik, Datenhaltung).
> - [ ] C) **Refactoring** der bereits implementierten Komponenten zur Verbesserung der Wartbarkeit.
> - [ ] D) **Erstellung eines detaillierten Lastenhefts** für alle zukünftigen Anforderungen.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: D**
>
> *Erklärung*:
> Ein **Lastenheft** wird typischerweise in der **Analysephase** (Phase I) erstellt, um Anforderungen zu dokumentieren. Die Infrastrukturplanung (Phase II) konzentriert sich auf die **Umsetzung der Kernfunktionalität**, die **Architekturkonsolidierung** (z. B. Schichtenmodell) und **technische Optimierungen** (z. B. Refactoring). Option D gehört daher nicht in diese Phase.

---
> [!question] **Frage 4: Welche Eigenschaft ist **kein** Kernmerkmal **ubiquitärer Systeme** (Pervasive/Ubiquitous Computing)?**
> - [ ] A) **Kontextsensitivität**: Das System passt sein Verhalten dynamisch an den Nutzerkontext an (z. B. Ort, Zeit, Präferenzen).
> - [ ] B) **Autonomie**: Geräte arbeiten weitgehend ohne menschliche Intervention und selbstverwaltet.
> - [ ] C) **Monolithische Architektur**: Alle Komponenten sind in einem einzigen, nicht verteilten System zusammengefasst.
> - [ ] D) **Intelligenz**: Das System beherrscht komplexe, dynamische Interaktionen und Aktivitäten.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> Ubiquitäre Systeme sind **verteilte Systeme** mit den Kernmerkmalen **Kontextsensitivität**, **Autonomie**, **Intelligenz** und **Transparenz** (z. B. IoT-Geräte). Eine **monolithische Architektur** (Option C) steht im Widerspruch zu diesen Prinzipien, da sie Skalierbarkeit und Flexibilität einschränkt. Ubiquitäre Systeme erfordern **Modularität** und **Dezentralisierung**.

---
> [!question] **Frage 5: Welche der folgenden Aussagen zur **Konsolidierung der Systemarchitektur** in der Erstellungsphase ist **falsch**?**
> - [ ] A) Die Konsolidierung dient dazu, **Architekturentscheidungen** (z. B. Schichtenmodell, Komponentenaufteilung) zu überprüfen und zu stabilisieren.
> - [ ] B) Sie umfasst **Refactoring-Maßnahmen**, um technische Schulden abzubauen und die Wartbarkeit zu verbessern.
> - [ ] C) Die Konsolidierung ersetzt die **funktionale Analyse**, da sie bereits alle Anforderungen abdeckt.
> - [ ] D) Sie geht einher mit der **Umsetzung der Kernfunktionalität** in frühen Iterationen.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> Die Konsolidierung der Systemarchitektur (Phase II) **ergänzt** die funktionale Analyse, ersetzt sie aber **nicht**. Die Analysephase (Phase I) dient der **Erfassung der Anforderungen**, während die Konsolidierung sich auf die **technische Umsetzung** und **Architekturoptimierung** konzentriert. Option C ist daher falsch. Die anderen Optionen (A, B, D) beschreiben korrekte Aspekte der Konsolidierung.

---
Das Quiz deckt **analytische Fähigkeiten**, **Anwendung von Konzepten** und **Abgrenzung von Begriffen** ab – genau wie im Hochschulkontext gefordert. Die Fragen sind auf **Master-Niveau** (M.Sc. Informatik) ausgelegt und erfordern vertieftes Verständnis.