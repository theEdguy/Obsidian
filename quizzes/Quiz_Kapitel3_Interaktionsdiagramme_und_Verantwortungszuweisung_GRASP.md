---
type: quiz
chapter: 3
subtopic: "Interaktionsdiagramme & Verantwortungszuweisung (GRASP)"
format: callout
generated_at: 2026-06-06 16:28:55
tags:
  - software_engineering
  - quiz
  - chapter_3
---

# 🧠 Quiz: Interaktionsdiagramme & Verantwortungszuweisung (GRASP)

**Kapitel:** Kapitel 3: Design – Softwarearchitektur & Entwurfsmuster
**Details:** 

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zu **Interaktionsdiagrammen & Verantwortungszuweisung (GRASP)** im geforderten Format:

---

> [!question] **Frage 1: Welches der folgenden Elemente ist KEIN primäres Ziel eines Sequenzdiagramms nach GRASP?**
> - [ ] A) Darstellung des zeitlichen Ablaufs von Interaktionen zwischen Objekten
> - [ ] B) Visualisierung der Lebenszeit von Objekten während eines Use Cases
> - [ ] C) Identifikation der Verantwortlichkeiten für Operationen und Wissen
> - [ ] D) Abbildung der statischen Struktur eines Systems (z. B. Klassenbeziehungen)

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: D**
>
> *Erklärung*:
> - **A** und **B** sind korrekte Ziele von Sequenzdiagrammen (vgl. Folien 286–300: "zeitlicher Verlauf der Interaktion" und "Objektlebenszeit").
> - **C** bezieht sich auf die **Verantwortungszuweisung** (GRASP-Prinzipien, Folie 295), die durch Interaktionsdiagramme unterstützt wird.
> - **D** beschreibt ein **Klassendiagramm** (statische Struktur), nicht ein Sequenzdiagramm. Dies ist kein primäres Ziel von Interaktionsdiagrammen.

---

> [!question] **Frage 2: Welches GRASP-Prinzip wird angewendet, wenn ein Objekt eine Methode eines anderen Objekts aufruft, um eine komplexe Berechnung durchzuführen?**
> - [ ] A) **Information Expert**
> - [ ] B) **Controller**
> - [ ] C) **Low Coupling**
> - [ ] D) **High Cohesion**

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: A**
>
> *Erklärung*:
> - **Information Expert** (Folien 295–300) besagt, dass die Verantwortung für eine Operation dem Objekt zugewiesen wird, das die **notwendigen Informationen** besitzt. Hier ruft das aufrufende Objekt das berechnende Objekt auf, weil dieses die Expertise für die Berechnung hat.
> - **Controller** (B) bezieht sich auf die Zuweisung der ersten Verantwortung für eine Systemoperation (z. B. an einen Use-Case-Controller).
> - **Low Coupling** (C) und **High Cohesion** (D) sind allgemeine Design-Prinzipien, aber nicht direkt auf die Delegation von Berechnungen anwendbar.

---
> [!question] **Frage 3: Welche Aussage zu Kommunikationsdiagrammen (Communication Diagrams) im Vergleich zu Sequenzdiagrammen ist FALSCH?**
> - [ ] A) Kommunikationsdiagramme betonen die räumliche Anordnung der Objekte, während Sequenzdiagramme den zeitlichen Ablauf zeigen.
> - [ ] B) Kommunikationsdiagramme basieren auf Objektdiagrammen und zeigen Verbindungen zwischen Objekten explizit.
> - [ ] C) Sequenzdiagramme eignen sich besser zur Darstellung von parallelen Nachrichtenflüssen.
> - [ ] D) Kommunikationsdiagramme sind immer detaillierter als Sequenzdiagramme, da sie alle Attribute von Objekten anzeigen.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: D**
>
> *Erklärung*:
> - **A** und **B** sind korrekt (vgl. Folien 286–300: Kommunikationsdiagramme zeigen "räumlich verteilte Sicht" und basieren auf Objektdiagrammen).
> - **C** ist richtig, da Sequenzdiagramme durch die vertikale Zeitachse parallele Nachrichten besser darstellen können.
> - **D** ist falsch: Kommunikationsdiagramme zeigen **keine Attribute** von Objekten (das wäre Aufgabe eines Klassendiagramms). Sie fokussieren auf Nachrichten und Verbindungen.

---
> [!question] **Frage 4: Ein System-Sequenzdiagramm (SSD) wird typischerweise in welcher Phase des Software-Entwicklungsprozesses erstellt und welchen Zweck erfüllt es?**
> - [ ] A) In der **Analysephase**, um die **statische Struktur** des Systems zu modellieren.
> - [ ] B) In der **Designphase**, um die **Implementierungsdetails** einer Klasse zu spezifizieren.
> - [ ] C) In der **Analysephase**, um die **Schnittstellen** eines Use Cases zu identifizieren.
> - [ ] D) In der **Testphase**, um die **Korrektheit der Implementierung** zu verifizieren.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> - **SSDs** werden in der **Analysephase** erstellt (vgl. Folien 181–195: "System-Sequenz-Diagramme erstellen" als Teil der Analyse).
> - Ihr **Zweck** ist die Identifikation der **erforderlichen Schnittstellen** für einen Use Case (z. B. welche externen Systeme oder Objekte beteiligt sind).
> - **A** ist falsch, da SSDs keine statische Struktur modellieren (das ist Aufgabe von Klassendiagrammen).
> - **B** und **D** beziehen sich auf Design/Implementierung bzw. Test, nicht auf die Analyse.

---
> [!question] **Frage 5: Welche der folgenden Verantwortungszuweisungen nach GRASP verletzt das Prinzip des "Low Coupling"?**
> - [ ] A) Ein `Order`-Objekt delegiert die Berechnung des Gesamtpreises an ein `PriceCalculator`-Objekt.
> - [ ] B) Ein `Customer`-Objekt speichert direkt eine Liste aller `Order`-Objekte, die es besitzt.
> - [ ] C) Ein `PaymentService`-Objekt wird von einem `Order`-Objekt aufgerufen, um eine Zahlung zu verarbeiten.
> - [ ] D) Ein `Inventory`-Objekt verwaltet eine Liste aller verfügbaren `Item`-Objekte und bietet eine Methode `checkAvailability()` an.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - **Low Coupling** (Folien 295–300) besagt, dass Objekte möglichst wenige Abhängigkeiten zu anderen Objekten haben sollten.
> - **B** verletzt dieses Prinzip, da das `Customer`-Objekt direkt eine Liste von `Order`-Objekten speichert (starke Kopplung). Besser wäre eine Delegation an ein separates `OrderRepository`-Objekt.
> - **A**, **C** und **D** sind korrekte Verantwortungszuweisungen:
>   - **A**: Delegation an einen spezialisierten Service (niedriges Coupling).
>   - **C**: Klare Trennung der Verantwortlichkeiten (PaymentService ist ein separates Objekt).
>   - **D**: Das `Inventory`-Objekt hat eine klare, begrenzte Verantwortung (niedriges Coupling zu anderen Objekten).

---