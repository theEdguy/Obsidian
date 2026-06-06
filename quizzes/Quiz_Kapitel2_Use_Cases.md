---
type: quiz
chapter: 2
subtopic: "Use Cases"
format: callout
generated_at: 2026-06-06 16:28:09
tags:
  - software_engineering
  - quiz
  - chapter_2
---

# 🧠 Quiz: Use Cases

**Kapitel:** Kapitel 2: Analyse – Anforderungen & Anwendungsfälle (Use Cases)
**Details:** (Erstellen, Beschreiben, Interpretieren)

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zu **Use Cases** (Erstellen, Beschreiben, Interpretieren) im geforderten Format:

---

> [!question] **Frage 1: Welche der folgenden Aussagen beschreibt korrekt die Rolle von Use Cases im Software-Engineering-Prozess nach Prof. Fuchß?**
> - [ ] A) Use Cases dienen ausschließlich der Dokumentation von nicht-funktionalen Anforderungen und haben keine Bedeutung für die Architektur oder Implementierung.
> - [ ] B) Use Cases sind nur für die Testphase relevant, da sie die Grundlage für Testfälle bilden.
> - [ ] C) Use Cases helfen bei der Strukturierung und Organisation des Projekts, indem sie Anforderungen in zentrale Abläufe überführen und die Grundlage für Analyse, Architektur, Design und Tests bilden.
> - [ ] D) Use Cases ersetzen klassische Anforderungsdokumente wie Lasten- und Pflichtenhefte und sind damit die einzige Quelle für Entwickler.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> Nach Prof. Fuchß bilden Use Cases die **Grundlage für alle Phasen des Software-Engineering-Prozesses** (Analyse, Architektur, Design, Implementierung, Tests, Evaluation). Sie strukturieren Anforderungen in zentrale Abläufe und helfen, diese systematisch umzusetzen. Die anderen Optionen sind falsch, weil:
> - A: Use Cases erfassen **sowohl funktionale als auch nicht-funktionale Anforderungen** (siehe Folie 154).
> - B: Use Cases sind **kein reines Testartefakt**, sondern werden bereits in der Analysephase erstellt (siehe Folie 152).
> - D: Use Cases **ergänzen** klassische Dokumente, ersetzen sie aber nicht vollständig (siehe Folie 155).

---

> [!question] **Frage 2: Welche der folgenden Aussagen zur Erstellung von Use Cases ist nach den Vorlesungsinhalten korrekt?**
> - [ ] A) Use Cases sollten immer detailliert alle möglichen Ausnahmefälle beschreiben, um spätere Fehler zu vermeiden.
> - [ ] B) Bei der Erstellung von Use Cases wird zunächst eine grobe Struktur (High-Level-Use-Cases) erstellt, die später verfeinert wird. Anschließend werden die Use Cases nach Wichtigkeit priorisiert.
> - [ ] C) Use Cases müssen immer als UML-Diagramme dargestellt werden, da textuelle Beschreibungen nicht ausreichen.
> - [ ] D) Die Erstellung von Use Cases erfolgt erst nach der Implementierung, um die tatsächlichen Abläufe zu dokumentieren.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> Die Vorlesung betont, dass die **Analyse mit High-Level-Use-Cases beginnt**, die später verfeinert und nach Wichtigkeit (z. B. "sehr wichtig", "wichtig") bewertet werden (siehe Folie 152). Die anderen Optionen sind falsch, weil:
> - A: Use Cases beschreiben **zentrale Abläufe**, nicht alle Ausnahmefälle (siehe Folie 153: "Wenige Sätze beschreiben übersichtlich die zentralen Abläufe").
> - C: Use Cases können **textuell oder als UML-Diagramme** dargestellt werden (siehe Folie 161: "Use-Case-Diagramme helfen bei der Strukturierung").
> - D: Use Cases werden **vor der Implementierung** erstellt, um Anforderungen zu strukturieren (siehe Folie 155: "Use Cases bilden die Grundlage für die Analyse, Architektur, Design, Implementierung...").

---

> [!question] **Frage 3: Welche der folgenden Aussagen zu Akteuren und Use Cases in UML-Diagrammen ist nach Prof. Fuchß korrekt?**
> - [ ] A) Akteure können nur menschliche Benutzer sein, keine externen Systeme oder Hardwarekomponenten.
> - [ ] B) Die Beziehungen zwischen Akteuren und Use Cases (Assoziationen) werden in UML-Diagrammen nicht dargestellt, um die Übersichtlichkeit zu erhöhen.
> - [ ] C) Ein Use Case kann mehrere Akteure haben, aber ein Akteur kann nur mit einem Use Case assoziiert sein.
> - [ ] D) Akteure repräsentieren Entitäten, die mit dem System interagieren, und ihre Beziehungen zu Use Cases zeigen, welche Vorgänge sie auslösen.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: D**
>
> *Erklärung*:
> Akteure sind **Entitäten (Menschen, Systeme, Hardware)**, die mit dem System interagieren, und ihre Beziehungen zu Use Cases zeigen, welche **Vorgänge sie auslösen** (siehe Folie 161: "Die Akteure, die mit dem System interagieren. Use-Case-Diagramme helfen bei der Strukturierung..."). Die anderen Optionen sind falsch, weil:
> - A: Akteure können **externe Systeme oder Hardware** sein (siehe Folie 161).
> - B: Assoziationen zwischen Akteuren und Use Cases **müssen dargestellt werden** (siehe Folie 166: "Verzicht auf Assoziationen ist nicht zulässig").
> - C: Ein Akteur kann mit **mehreren Use Cases** assoziiert sein (und umgekehrt).

---
> [!question] **Frage 4: Ein Use Case "Buch bestellen" soll um den Use Case "Zahlung prüfen" erweitert werden. Welche der folgenden Aussagen zur Beziehung zwischen diesen Use Cases ist nach den Vorlesungsinhalten korrekt?**
> - [ ] A) Die Beziehung sollte als Vererbung (Generalization) modelliert werden, da "Zahlung prüfen" eine spezielle Form von "Buch bestellen" ist.
> - [ ] B) Die Beziehung sollte als `<<include>>` modelliert werden, wenn "Zahlung prüfen" immer Teil von "Buch bestellen" ist.
> - [ ] C) Die Beziehung sollte als `<<extend>>` modelliert werden, wenn "Zahlung prüfen" optional ist und nur unter bestimmten Bedingungen aufgerufen wird.
> - [ ] D) Die Beziehung sollte als Assoziation ohne Stereotyp dargestellt werden, da `<<include>>` und `<<extend>>` in UML nicht zulässig sind.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - `<<include>>` wird verwendet, wenn ein Use Case **immer** einen anderen Use Case aufruft (z. B. "Buch bestellen" **inkludiert** "Zahlung prüfen").
> - `<<extend>>` wird verwendet, wenn ein Use Case **optional** erweitert wird (z. B. "Zahlung prüfen" wird nur unter bestimmten Bedingungen aufgerufen).
> Die anderen Optionen sind falsch, weil:
> - A: `<<include>>` und `<<extend>>` sind **keine Vererbungsbeziehungen** (siehe Folie 166: "Weder extend noch include stellen Vererbungsrelationen dar").
> - C: Die Beziehung ist **falsch herum** – wenn "Zahlung prüfen" optional ist, sollte "Buch bestellen" den Use Case `<<extend>>` "Zahlung prüfen".
> - D: Assoziationen ohne Stereotyp sind **nicht ausreichend**, da die Art der Beziehung (include/extend) explizit modelliert werden muss.

---
> [!question] **Frage 5: Welche der folgenden Aussagen zur Interpretation von Use Cases in der Designphase ist nach den Vorlesungsinhalten korrekt?**
> - [ ] A) In der Designphase werden Use Cases aus der Analysephase verworfen, da sie zu abstrakt sind.
> - [ ] B) Use Cases der Analysephase werden in der Designphase zu **konkreten System-Use-Cases** verfeinert, wobei technische Aspekte und Subsysteme berücksichtigt werden.
> - [ ] C) Die Designphase konzentriert sich ausschließlich auf die Implementierung der Use Cases, ohne deren Abläufe weiter zu analysieren.
> - [ ] D) Use Cases spielen in der Designphase keine Rolle mehr, da sie nur für die Anforderungsanalyse relevant sind.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> In der Designphase werden die Use Cases der Analysephase **iterativ verfeinert** und zu **konkreten System-Use-Cases** weiterentwickelt. Dabei werden technische Aspekte, Subsysteme und Input-Output-Terminologie berücksichtigt (siehe Folie 244: "Aus den Use Cases der Analyse werden im Design konkrete System-Use-Cases. Input-Output-Terminologie verwenden. Subsysteme (Architektur) beachten."). Die anderen Optionen sind falsch, weil:
> - A: Use Cases werden **nicht verworfen**, sondern verfeinert (siehe Folie 244).
> - C: Die Designphase **baut auf den Use Cases auf** und analysiert deren Abläufe weiter (siehe Folie 244).
> - D: Use Cases bleiben **während des gesamten Prozesses** relevant (siehe Folie 155).