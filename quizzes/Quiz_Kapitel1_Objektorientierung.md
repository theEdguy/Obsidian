---
type: quiz
chapter: 1
subtopic: "Objektorientierung"
format: callout
generated_at: 2026-06-06 16:27:46
tags:
  - software_engineering
  - quiz
  - chapter_1
---

# 🧠 Quiz: Objektorientierung

**Kapitel:** Kapitel 1: Grundlagen – Entwicklungsprozess & Empirische Methoden
**Details:** (Vererbung, Komposition, Aggregation, Assoziation)

---

Hier ist das anspruchsvolle Multiple-Choice-Quiz zum Thema **Objektorientierung** (Vererbung, Komposition, Aggregation, Assoziation) im geforderten Format:

---

> [!question] **Frage 1: Welche der folgenden Aussagen beschreibt korrekt den Unterschied zwischen Vererbung und Komposition?**
> - [ ] A) Vererbung ermöglicht zur Laufzeit dynamische Bindung, während Komposition nur zur Compile-Zeit möglich ist.
> - [ ] B) Vererbung bedeutet eine "ist-ein"-Beziehung mit fester Implementierung, Komposition eine "hat-ein"-Beziehung mit flexibler Schnittstellennutzung.
> - [ ] C) Komposition ist immer stärker gekoppelt als Vererbung, da sie die Implementierung direkt übernimmt.
> - [ ] D) Vererbung und Komposition sind äquivalent, da beide eine "ist-ein"-Beziehung modellieren.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - **Vererbung** modelliert eine **"ist-ein"**-Beziehung (z. B. `Auto ist ein Fahrzeug`) und legt sich zur **Compile-Zeit** auf eine Implementierung fest (starre Kopplung).
> - **Komposition** modelliert eine **"hat-ein"**-Beziehung (z. B. `Motor hat ein Auto`) und nutzt eine **Schnittstelle zur Laufzeit** (flexiblere Kopplung).
> - Option A ist falsch, da Vererbung **keine** dynamische Bindung zur Laufzeit ermöglicht (Polymorphie ist ein separates Konzept).
> - Option C ist falsch, weil Komposition **geringere Kopplung** als Vererbung aufweist (abhängig von der Schnittstelle, nicht der Implementierung).
> - Option D ist falsch, da die Beziehungen grundverschieden sind.

---

> [!question] **Frage 2: Welche der folgenden Aussagen zur Aggregation ist korrekt?**
> - [ ] A) Aggregation impliziert eine exklusive Besitzbeziehung, bei der das "Teil"-Objekt nicht ohne das "Ganzes"-Objekt existieren kann.
> - [ ] B) Aggregation ist eine schwächere Form der Assoziation, bei der das "Teil"-Objekt unabhängig vom "Ganzes"-Objekt existieren kann.
> - [ ] C) Aggregation ist identisch mit Komposition, da beide eine "ist-ein"-Beziehung darstellen.
> - [ ] D) Aggregation erfordert immer eine bidirektionale Navigation zwischen den beteiligten Objekten.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - **Aggregation** ist eine **schwache "hat-ein"**-Beziehung, bei der das "Teil" **unabhängig** vom "Ganzes" existieren kann (z. B. `Student` aggregiert `Buch` – das Buch kann auch ohne den Studenten existieren).
> - **Komposition** hingegen ist eine **starke "hat-ein"**-Beziehung, bei der das "Teil" **nicht ohne das "Ganzes" existieren kann** (z. B. `Motor` existiert nur mit dem `Auto`).
> - Option A beschreibt **Komposition**, nicht Aggregation.
> - Option C ist falsch, da Aggregation und Komposition unterschiedliche Semantiken haben.
> - Option D ist falsch, da Aggregation **nicht zwingend bidirektional** ist (z. B. kann eine `Universität` Studenten aggregieren, aber Studenten müssen nicht zwingend die Universität kennen).

---

> [!question] **Frage 3: In welchem Szenario wäre die Verwendung von Vererbung statt Komposition problematisch?**
> - [ ] A) Ein `Dreieck` erbt von `Form` und implementiert eine Methode `berechneFlaeche()`.
> - [ ] B) Ein `Auto` erbt von `Fahrzeug`, obwohl es spezifische Eigenschaften wie `Elektroantrieb` hat, die nicht für alle Fahrzeuge gelten.
> - [ ] C) Ein `Stack` wird als Komposition aus `ArrayList` implementiert.
> - [ ] D) Ein `Kunde` aggregiert eine `Adresse`, die auch von anderen Klassen genutzt wird.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - **Vererbung** sollte nur verwendet werden, wenn eine **echte "ist-ein"**-Beziehung vorliegt (z. B. `Dreieck ist eine Form`).
> - **Problemfall**: Ein `Auto` ist zwar ein `Fahrzeug`, aber die spezifische Eigenschaft `Elektroantrieb` passt nicht zu allen Fahrzeugen. Dies führt zu **starren Hierarchien** und **Code-Duplikation** (z. B. müsste man für `Verbrenner` eine separate Klasse erstellen).
> - **Lösung**: Hier wäre **Komposition** besser (z. B. `Auto hat einen Antrieb` als separates Objekt).
> - Option A ist korrekt, da `Dreieck` eine spezielle `Form` ist.
> - Option C ist korrekt, da `Stack` typischerweise als Komposition implementiert wird.
> - Option D ist korrekt, da Aggregation hier sinnvoll ist.

---
> [!question] **Frage 4: Welche der folgenden Aussagen zur Assoziation ist falsch?**
> - [ ] A) Assoziation ist die allgemeinste Form der Beziehung zwischen Klassen und kann mit Multiplizitäten (z. B. 0..*) annotiert werden.
> - [ ] B) Assoziation impliziert immer eine bidirektionale Navigation zwischen den Objekten.
> - [ ] C) Assoziation kann sowohl eine "hat-ein"- als auch eine "ist-ein"-Beziehung modellieren.
> - [ ] D) Assoziation wird in UML durch eine einfache Linie zwischen Klassen dargestellt.

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: C**
>
> *Erklärung*:
> - **Assoziation** ist die **allgemeinste Beziehung** und kann **keine "ist-ein"**-Beziehung modellieren (das ist die Domäne der **Vererbung**).
> - **Richtige Aussagen**:
>   - A: Assoziation kann Multiplizitäten haben (z. B. `Verein hat 0..* Mitglieder`).
>   - B: Assoziation **kann** bidirektional sein, muss aber nicht (z. B. `Kunde bestellt Produkt` – der Kunde kennt das Produkt, aber nicht umgekehrt).
>   - D: In UML wird Assoziation durch eine **Linie** dargestellt (mit optionalen Pfeilen für die Navigationsrichtung).
> - **Falsche Aussage C**: "ist-ein" ist **Vererbung**, nicht Assoziation.

---
> [!question] **Frage 5: Welches Entwurfsmuster nutzt Komposition, um die Erzeugung von Objekten zu delegieren?**
> - [ ] A) Singleton
> - [ ] B) Fabrikmethode (Factory Method)
> - [ ] C) Beobachter (Observer)
> - [ ] D) Strategie (Strategy)

> [!success]- 🔑 Antwort anzeigen / Show Answer
> **Richtige Antwort: B**
>
> *Erklärung*:
> - **Fabrikmethode (Factory Method)** ist ein **Erzeugungsmuster**, das **Komposition** nutzt, um die Objekterzeugung an Unterklassen zu delegieren.
>   - Beispiel: Eine `DokumentFabrik` erstellt verschiedene `Dokument`-Objekte, ohne die konkrete Klasse zu kennen.
>   - Die Erzeugung wird **zur Laufzeit** entschieden (flexibel).
> - **Warum nicht die anderen Optionen?**
>   - A) **Singleton** nutzt **keine Komposition**, sondern eine statische Methode (`getInstance()`).
>   - C) **Beobachter** nutzt Assoziation (Objekte registrieren sich gegenseitig).
>   - D) **Strategie** nutzt Komposition, um Algorithmen auszutauschen, aber **nicht für die Objekterzeugung**.
> - **Hinweis**: Die Vorlesung erwähnt die Fabrikmethode explizit als Beispiel für **Delegation zur Laufzeit** (Folie 331–345).

---