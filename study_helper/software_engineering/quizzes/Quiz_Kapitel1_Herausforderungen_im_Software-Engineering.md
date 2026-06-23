---
type: quiz
chapter: 1
subtopic: "Herausforderungen im Software-Engineering"
format: callout
generated_at: 2026-06-06 16:27:10
tags:
  - software_engineering
  - quiz
  - chapter_1
---

# 🧠 Quiz: Herausforderungen im Software-Engineering

**Kapitel:** Kapitel 1: Grundlagen – Entwicklungsprozess & Empirische Methoden
**Details:** (Dekomposition, Abhängigkeiten)

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zu den Herausforderungen im Software-Engineering mit Fokus auf Dekomposition und Abhängigkeiten:

---

> [!question] **Frage 1: Welche Aussage zur Dekomposition in der Software-Entwicklung ist fachlich korrekt?**
> - [ ] A) Dekomposition dient ausschließlich der Parallelisierung von Entwicklungsprozessen, um die Zeit bis zur Markteinführung zu verkürzen.
> - [ ] B) Dekomposition ist ein rein technisches Verfahren, das nur bei der Implementierung von Algorithmen relevant ist.
> - [ ] C) Dekomposition zielt darauf ab, komplexe Systeme in kleinere, handhabbare Module zu zerlegen, um die Wartbarkeit und Wiederverwendbarkeit zu erhöhen.
> - [ ] D) Dekomposition ist ein veraltetes Konzept, das durch moderne KI-gestützte Codegenerierung vollständig ersetzt wird.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> Dekomposition ist ein zentrales Prinzip des Software-Engineerings, das komplexe Systeme in kleinere, unabhängige Module zerlegt. Dies verbessert die Wartbarkeit (durch klare Schnittstellen), die Wiederverwendbarkeit (durch modulare Komponenten) und die Skalierbarkeit (durch parallele Entwicklung). Option A ist zu eng gefasst (Dekomposition hat auch technische Vorteile), Option B ignoriert die architektonische Bedeutung, und Option D widerspricht dem ingenieurmäßigen Ansatz, der auf systematischer Strukturierung basiert.

---

> [!question] **Frage 2: Welche der folgenden Aussagen beschreibt eine **direkte Abhängigkeit** zwischen zwei Software-Modulen korrekt?**
> - [ ] A) Modul A nutzt eine Klasse aus Modul B, ohne deren Implementierung zu kennen (z.B. über Interfaces).
> - [ ] B) Modul A greift direkt auf die private Implementierung eines Dienstes in Modul B zu.
> - [ ] C) Modul A und Modul B teilen sich eine gemeinsame Datenbank, ohne miteinander zu kommunizieren.
> - [ ] D) Modul A erbt von einer Basisklasse in Modul B, überschreibt aber keine Methoden.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> Eine direkte Abhängigkeit liegt vor, wenn ein Modul (A) direkt auf die Implementierungsdetails eines anderen Moduls (B) zugreift – z.B. durch Zugriff auf private Attribute oder Methoden. Dies verletzt das Prinzip der Kapselung und führt zu stark gekoppelten Systemen. Option A beschreibt eine lose Kopplung (abhängig von Interfaces), Option C ist eine indirekte Abhängigkeit (über Datenbank), und Option D ist eine spezifische Form der Abhängigkeit (Vererbung), aber nicht zwingend eine direkte Implementierungsabhängigkeit.

---
> [!question] **Frage 3: Welche der folgenden Maßnahmen reduziert **transitive Abhängigkeiten** in einem Software-System am effektivsten?**
> - [ ] A) Verwendung von Dependency Injection, um Abhängigkeiten zur Laufzeit zu injizieren.
> - [ ] B) Einführung einer zentralen Konfigurationsdatei, die alle Abhängigkeiten verwaltet.
> - [ ] C) Minimierung der Anzahl öffentlicher Methoden in Klassen, um die Schnittstelle zu verkleinern.
> - [ ] D) Einsatz von Design Patterns wie "Facade" oder "Adapter", um komplexe Abhängigkeitsketten zu kapseln.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: D**
>
> *Erklärung*:
> Transitive Abhängigkeiten entstehen, wenn ein Modul A von Modul B abhängt, das wiederum von Modul C abhängt. Design Patterns wie **Facade** (vereinfacht Schnittstellen) oder **Adapter** (wandelt Schnittstellen um) helfen, solche Ketten zu brechen und die Komplexität zu reduzieren. Option A (Dependency Injection) reduziert zwar direkte Abhängigkeiten, bekämpft aber nicht direkt transitive. Option B ist ein organisatorischer Ansatz, und Option C betrifft nur die interne Komplexität einer Klasse, nicht die Abhängigkeiten zwischen Modulen.

---
> [!question] **Frage 4: Welche Aussage zur **Kopplung** zwischen Software-Modulen ist **falsch**?**
> - [ ] A) Hohe Kopplung führt zu Systemen, die schwer zu warten und zu testen sind.
> - [ ] B) Geringe Kopplung erhöht die Wahrscheinlichkeit, dass Änderungen in einem Modul Auswirkungen auf andere Module haben.
> - [ ] C) Kopplung kann durch lose Kopplung (z.B. über Interfaces) reduziert werden.
> - [ ] D) Starke Kopplung entsteht häufig durch direkte Abhängigkeiten zwischen Implementierungsdetails.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> Die Aussage in **B ist falsch**, weil **geringe Kopplung** gerade das Gegenteil bewirkt: Änderungen in einem Modul haben **keine oder nur minimale Auswirkungen** auf andere Module. Hohe Kopplung (Option A) erschwert Wartung und Testing, während lose Kopplung (z.B. über Interfaces) die Unabhängigkeit fördert (Option C). Option D beschreibt einen typischen Fall von starker Kopplung (direkter Zugriff auf Implementierungsdetails).

---
> [!question] **Frage 5: Ein Entwicklungsteam entscheidet sich, ein großes Software-System in Mikroservices zu zerlegen. Welche der folgenden Herausforderungen ist **nicht** direkt mit dieser Dekompositionsstrategie verbunden?**
> - [ ] A) Erhöhter Kommunikationsaufwand zwischen den Teams aufgrund verteilter Verantwortlichkeiten.
> - [ ] B) Komplexität bei der Verwaltung von Datenkonsistenz über Service-Grenzen hinweg.
> - [ ] C) Notwendigkeit, für jeden Mikroservice eine eigene Build-Pipeline zu konfigurieren.
> - [ ] D) Reduzierung der Testkomplexität, da jeder Mikroservice isoliert getestet werden kann.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: D**
>
> *Erklärung*:
> Die **Testkomplexität wird durch Mikroservices nicht reduziert**, sondern oft erhöht, da Integrationstests über Service-Grenzen hinweg erforderlich sind. Die anderen Optionen sind typische Herausforderungen:
> - **A**: Mikroservices erfordern agile Teamstrukturen und erhöhte Kommunikation (z.B. nach Conway’s Law).
> - **B**: Verteilte Datenhaltung führt zu Problemen wie eventual consistency oder verteilten Transaktionen.
> - **C**: Jeder Mikroservice benötigt eigene CI/CD-Pipelines, was den Betriebsaufwand erhöht.
> Option D ist daher die **falsche Aussage**, da Mikroservices die Testkomplexität nicht verringern, sondern neue Herausforderungen schaffen.