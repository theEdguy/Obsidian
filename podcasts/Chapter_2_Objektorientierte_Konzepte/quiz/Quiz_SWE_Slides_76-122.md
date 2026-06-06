---
type: chapter_quiz
chapter: 2
range: "76-122"
generated_at: 2026-06-06 16:32:07
tags:
  - software_engineering
  - quiz
  - chapter_quiz_2
---

# 🧠 Chapter 2 Quiz: Objektorientierte Konzepte

**Slide Range:** 76-122

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien (76–90), formatiert für Obsidian:

---

> [!question] **Frage 1: Vererbung und Substitutionsprinzip**
> Welche der folgenden Aussagen zum **Substitutionsprinzip** (Liskov Substitution Principle) ist **falsch**?
> - [ ] A) Eine Unterklasse muss alle Methoden der Oberklasse implementieren, auch wenn sie nicht sinnvoll sind.
> - [ ] B) Instanzen einer Unterklasse können überall verwendet werden, wo Instanzen der Oberklasse erwartet werden.
> - [ ] C) Die Unterklasse darf die Semantik der geerbten Methoden **nicht verschlechtern** (z. B. schwächere Vorbedingungen).
> - [ ] D) Die Unterklasse darf **neue Ausnahmen** werfen, die in der Oberklasse nicht spezifiziert waren.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: A**
> >
> > *Erklärung*:
> > - **A ist falsch**, weil das Substitutionsprinzip **keine Pflicht zur Implementierung aller Methoden** verlangt – allerdings muss die Unterklasse die Schnittstelle der Oberklasse respektieren (z. B. durch leere Implementierungen oder sinnvolle Alternativen).
> > - **B ist korrekt**: Das ist die Kernidee des Substitutionsprinzips (Objekte der Unterklasse sind "ersetzbar" durch Objekte der Oberklasse).
> > - **C ist korrekt**: Eine Verschlechterung der Semantik (z. B. strengere Nachbedingungen) verletzt das Prinzip.
> > - **D ist korrekt**: Neue Ausnahmen sind problematisch, da sie die Kompatibilität brechen (siehe *Design by Contract*).

---

> [!question] **Frage 2: UML-Meta-Modell und Schichtenarchitektur**
> Welche Aussage zur **Schichtenarchitektur des UML-Meta-Modells** (Folien 85–86) ist **richtig**?
> - [ ] A) Das **M0-Modell** beschreibt die abstrakte Syntax von UML (z. B. Klassen, Assoziationen).
> - [ ] B) Das **M2-Modell** enthält konkrete Objekte wie Datenbankeinträge oder Programmvariablen.
> - [ ] C) Das **M3-Meta-Meta-Modell** definiert die Infrastruktur zur Erstellung von Meta-Modellen (z. B. MOF).
> - [ ] D) Das **M1-Modell** ist eine Instanz des M0-Modells und enthält z. B. die Klasse `Mitglied` mit Attributen wie `name: String`.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A ist falsch**: M0 enthält **reale Objekte** (z. B. `"Mustermann"`), während M2 die **Modellebene** (z. B. UML-Klassendiagramme) beschreibt.
> > - **B ist falsch**: M2 enthält **Modelle** (z. B. UML-Diagramme), während M0 die **konkreten Instanzen** (z. B. Datenbankeinträge) beschreibt.
> > - **C ist korrekt**: M3 (Meta-Meta-Modell) definiert die Sprache zur Erstellung von Meta-Modellen (z. B. MOF oder UML selbst).
> > - **D ist falsch**: M1 enthält **Modelle** (z. B. UML-Klassendiagramme), während M0 die **konkreten Objekte** (z. B. `name = "Thomas Fuchß"`) beschreibt.

---

> [!question] **Frage 3: Vererbung vs. Komposition – Das Quadrat-Rechteck-Problem**
> Welche Aussage zur **Vererbungshierarchie zwischen `Quadrat` und `Rechteck`** (Folien 79–82) ist **falsch**?
> - [ ] A) Eine naive Vererbung von `Quadrat` als Unterklasse von `Rechteck` führt zu **Invariantenverletzungen**, wenn Methoden wie `stretch(i, j)` aufgerufen werden.
> - [ ] B) Die **Lösung ohne Vererbung** (z. B. durch eine `istQuadrat()`-Methode in `Rechteck`) vermeidet das Problem, weil sie die **is-a-Beziehung** aufhebt.
> - [ ] C) Das Problem entsteht, weil `Quadrat` eine **stärkere Invariante** (`a = b`) hat als `Rechteck` (`a` und `b` unabhängig`).
> - [ ] D) Die **falsche Vererbungsrichtung** (z. B. `Rechteck` als Unterklasse von `Quadrat`) würde das Problem lösen, weil `Rechteck` dann die Invariante von `Quadrat` erzwingen könnte.

> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A ist korrekt**: Das Problem ist ein klassisches Beispiel für das **Liskov Substitution Principle** – ein `Quadrat` kann nicht als `Rechteck` behandelt werden, ohne Invarianten zu brechen.
> > - **B ist korrekt**: Die Komposition (z. B. `Rechteck` mit einer `Form`-Klasse) löst das Problem, weil die **is-a-Beziehung** nicht erzwungen wird.
> > - **C ist korrekt**: Die Invariante von `Quadrat` (`a = b`) ist stärker als die von `Rechteck` (`a` und `b` unabhängig`), was zu Konflikten führt.
> > - **D ist falsch**: Die umgekehrte Vererbung (`Rechteck` als Unterklasse von `Quadrat`) würde das Problem **verschlimmern**, weil `Rechteck` dann die Invariante von `Quadrat` erzwingen müsste – was unmöglich ist (ein Rechteck kann `a ≠ b` haben).

---
Diese Fragen decken zentrale Konzepte ab:
1. **Substitutionsprinzip** (Frage 1),
2. **UML-Meta-Modell** (Frage 2),
3. **Vererbung vs. Komposition** (Frage 3).

Die Distraktoren sind so gewählt, dass sie typische Missverständnisse adressieren (z. B. Schichtenarchitektur, Invariante bei Vererbung).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Abstrakte Klassen vs. Interfaces**
> Welche der folgenden Aussagen trifft **nicht** auf abstrakte Klassen oder Interfaces zu?
> - [ ] A) Eine abstrakte Klasse kann sowohl konkrete als auch abstrakte Methoden enthalten, während ein Interface nur abstrakte Methoden (bis Java 8) oder Default-Implementierungen (ab Java 8) definieren kann.
> - [ ] B) Eine Klasse kann nur eine abstrakte Klasse erben, aber mehrere Interfaces implementieren.
> - [ ] C) Interfaces dürfen Attribute und Assoziationen zu anderen Klassen enthalten, während abstrakte Klassen dies explizit verbieten.
> - [ ] D) Eine abstrakte Klasse ohne Unterklassen ist sinnlos, da sie nicht instanziiert werden kann und keine konkrete Funktionalität bietet.

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A** ist korrekt: Abstrakte Klassen können sowohl abstrakte als auch konkrete Methoden enthalten, während Interfaces (bis Java 8) nur abstrakte Methoden definieren konnten. Ab Java 8 sind Default-Implementierungen in Interfaces möglich.
> > - **B** ist korrekt: In Java (und vielen anderen Sprachen) unterstützt die Vererbung nur eine Oberklasse (`extends`), aber mehrere Interfaces (`implements`).
> > - **C** ist **falsch**: Interfaces **dürfen keine Attribute oder Assoziationen zu anderen Klassen enthalten** (siehe Slide 92). Abstrakte Klassen können dies sehr wohl.
> > - **D** ist korrekt: Eine abstrakte Klasse ohne Unterklassen ist sinnlos, da sie nicht instanziiert werden kann und keine konkrete Funktionalität bietet (siehe Slide 91).

---

> [!question] **Frage 2: Besondere Beziehungen in der Vererbung**
> Welche der folgenden Aussagen zu den Beziehungen `{overlapping}`, `{disjoint}`, `{complete}` und `{incomplete}` ist **falsch**?
> - [ ] A) Bei `{overlapping}` können Instanzen gleichzeitig mehreren Unterklassen angehören (z. B. ein `HerrenLigaTeam` könnte sowohl `HerrenTeam` als auch `LigaTeam` sein).
> - [ ] B) Bei `{disjoint}` ist eine Mehrfachvererbung sinnlos, da keine Instanz mehreren Unterklassen angehören kann (z. B. ein `Mitglied` kann nicht gleichzeitig `Junior` und `Senior` sein).
> - [ ] C) Bei `{complete}` gibt es keine Instanzen der Oberklasse außerhalb der angegebenen Unterklassen (z. B. ein `Vereinsmanager` muss entweder `Vorstand` oder `Abteilungsleiter` sein).
> - [ ] D) Bei `{incomplete}` sind alle möglichen Unterklassen bereits definiert, und es gibt keine weiteren Spezialisierungen (z. B. ein `Mitglied` kann nur `Junior` oder `Dame` sein).

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A** ist korrekt: `{overlapping}` erlaubt Mehrfachvererbung (siehe Slide 95).
> > - **B** ist korrekt: `{disjoint}` verbietet Mehrfachvererbung (siehe Slide 96).
> > - **C** ist korrekt: `{complete}` bedeutet, dass alle Instanzen der Oberklasse in den Unterklassen enthalten sind (siehe Slide 97).
> > - **D** ist **falsch**: `{incomplete}` bedeutet, dass es **noch weitere Unterklassen geben kann** (siehe Slide 98). Die Aussage in D beschreibt fälschlicherweise `{complete}`.

---

> [!question] **Frage 3: Templates und Bindungen**
> Welche der folgenden Aussagen zu Templates (Generics) ist **falsch**?
> - [ ] A) Ein Template definiert eine Familie von Klassen, die durch Substitution der formalen Parameter (Binding) entstehen.
> - [ ] B) Beziehungen (Assoziationen) in Templates sind immer gerichtet – von der Template-Klasse zur gebundenen Klasse, nicht umgekehrt.
> - [ ] C) Eine durch Binding entstandene Klasse kann eine Unterklasse einer Superklasse sein, wenn das Template selbst eine Unterklasse ist.
> - [ ] D) Templates können nur mit primitiven Datentypen (z. B. `int`, `String`) gebunden werden, nicht mit benutzerdefinierten Klassen (z. B. `Mitglied`).

> > [!success]- 🔑 Antwort anzeigen / Show Answer
> > **Richtige Antwort: D**
> >
> > *Erklärung*:
> > - **A** ist korrekt: Templates definieren eine Familie von Klassen (siehe Slide 99).
> > - **B** ist korrekt: Assoziationen in Templates sind immer gerichtet (siehe Slide 99).
> > - **C** ist korrekt: Wenn das Template eine Unterklasse ist, dann ist auch die gebundene Klasse eine Unterklasse der entsprechenden Superklasse (siehe Slide 99).
> > - **D** ist **falsch**: Templates können mit **beliebigen Klassen** gebunden werden, nicht nur mit primitiven Datentypen (siehe Slide 100, Beispiel `Set<Mitglied>`).

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Binäre Assoziationen und ihre Eigenschaften**
> Welche der folgenden Aussagen beschreibt **korrekt** eine binäre Assoziation zwischen zwei Klassen?
>
> - [ ] A) Eine binäre Assoziation kann nur zwischen genau zwei Objekten derselben Klasse bestehen.
> - [ ] B) Eine binäre Assoziation beschreibt eine Beziehung zwischen den Objekten **genau zweier** Klassen und kann durch Rollenbezeichner, Stelligkeit und Eigenschaften näher spezifiziert werden.
> - [ ] C) Binäre Assoziationen sind immer navigierbar, d. h., beide beteiligten Klassen kennen ihre Beziehungen gegenseitig.
> - [ ] D) Binäre Assoziationen erlauben keine Einschränkungen wie `{ordered}` oder `{xor}`, da diese nur für mehrstellige Assoziationen gelten.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist falsch, da binäre Assoziationen zwischen Objekten **zweier verschiedener Klassen** bestehen, nicht derselben.
> > - **B** ist korrekt: Binäre Assoziationen verbinden zwei Klassen und können durch Rollenbezeichner (z. B. "unterstützt"), Stelligkeit (z. B. `1..*`) und Eigenschaften wie `{ordered}` beschrieben werden (vgl. Slide 106).
> > - **C** ist falsch, da Navigierbarkeit nicht zwingend gegeben ist (vgl. Slide 107: Nur das Mitglied kennt die Disziplinen, nicht umgekehrt).
> > - **D** ist falsch, da Constraints wie `{ordered}` oder `{xor}` auch bei binären Assoziationen vorkommen (z. B. Slide 106: `{ordered}` oder Slide 110: `{xor}`).

---

> [!question] **Frage 2: Komposition vs. Aggregation**
> Welche der folgenden Aussagen trifft **nicht** auf eine **Komposition** zu, aber **kann** auf eine **Aggregation** zutreffen?
>
> - [ ] A) Die Teile sind existenzabhängig vom Ganzen.
> - [ ] B) Die Stelligkeit auf Seiten des Aggregats ist stets `1`.
> - [ ] C) Ein Teil kann von mehreren Aggregaten gleichzeitig abhängen.
> - [ ] D) Die Zerstörung des Ganzen führt zur Zerstörung der Teile.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: C**
> >
> > *Erklärung*:
> > - **A** und **D** beschreiben Eigenschaften der **Komposition** (vgl. Slide 115–116: Teile existieren nur mit dem Ganzen; Zerstörung des Ganzen zerstört die Teile).
> > - **B** ist eine Eigenschaft **beider** Beziehungen (Komposition und Aggregation, vgl. Slide 116 und 118).
> > - **C** ist **falsch für Kompositionen**, aber **möglich für Aggregationen**:
> >   - Bei **Kompositionen** kann ein Teil **nicht** von mehreren Aggregaten abhängen (Slide 116: "Kein Teil kann von mehr als einem Objekt existenzabhängig sein").
> >   - Bei **Aggregationen** ist dies jedoch möglich (Slide 117–118: Teile sind nicht existenzabhängig und können mehreren Aggregaten zugeordnet sein).

---
> [!question] **Frage 3: Assoziationsklassen und ihre Verwendung**
> Wann ist die Verwendung einer **Assoziationsklasse** (wie in Slide 108) besonders sinnvoll?
>
> - [ ] A) Wenn eine Beziehung zwischen zwei Klassen **keine zusätzlichen Attribute** benötigt.
> - [ ] B) Wenn eine Beziehung **mehrere Rollenbezeichner** erfordert, die nicht einer der beteiligten Klassen zugeordnet werden können.
> - [ ] C) Wenn die Beziehung zwischen zwei Klassen **existenzabhängig** ist (z. B. wie eine Komposition).
> - [ ] D) Wenn die Beziehung **nur zwischen zwei Objekten** besteht und keine weiteren Einschränkungen benötigt.
>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > - **A** ist falsch: Assoziationsklassen werden **gerade dann** verwendet, wenn eine Beziehung **zusätzliche Attribute** benötigt (z. B. `seit` und `Ranking` in Slide 108).
> > - **B** ist korrekt: Assoziationsklassen ermöglichen es, **Eigenschaften zu modellieren, die weder der einen noch der anderen Klasse sinnvoll zugeordnet werden können** (z. B. wenn eine Beziehung selbst Attribute hat, wie "seit wann" ein Mitglied einen Sport ausübt).
> > - **C** ist falsch: Existenzabhängigkeit ist ein Merkmal von **Kompositionen/Aggregationen**, nicht von Assoziationsklassen.
> > - **D** ist falsch: Assoziationsklassen werden auch bei **mehrstelligen Beziehungen** oder komplexen Constraints verwendet (vgl. Slide 109–111), nicht nur bei einfachen binären Beziehungen.

---

Hier sind drei anspruchsvolle Multiple-Choice-Fragen basierend auf den Vorlesungsfolien:

---

> [!question] **Frage 1: Welche Aussage beschreibt korrekt die Rolle von Dependencies in UML-Klassendiagrammen?**
> - [ ] A) Dependencies werden verwendet, um dauerhafte Assoziationen zwischen Klassen darzustellen, die über die gesamte Lebensdauer der Objekte bestehen.
> - [ ] B) Dependencies kennzeichnen dynamische Beziehungen, bei denen Objekte nur temporär übergeben oder genutzt werden, ohne eine feste Assoziation zu etablieren.
> - [ ] C) Dependencies ersetzen Vererbungsbeziehungen (`<<inherits>>`), um die Wiederverwendung von Code zu ermöglichen.
> - [ ] D) Dependencies sind ausschließlich für die Modellierung von Schnittstellen (`<<interface>>`) reserviert und haben keine andere Funktion.

>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Dependencies in UML dienen dazu, **temporäre oder dynamische Abhängigkeiten** zwischen Klassen oder Komponenten zu modellieren – etwa wenn eine Klasse eine Methode einer anderen aufruft oder ein Objekt als Parameter übergibt, ohne dass eine dauerhafte Assoziation besteht. Option A beschreibt klassische Assoziationen, Option C ist falsch, da Dependencies keine Vererbung ersetzen, und Option D ist zu eng gefasst, da Dependencies auch bei regulären Klassen vorkommen (wie im Beispiel der `leistungsprognose`-Methode auf Folie 121).

---

> [!question] **Frage 2: Welche der folgenden Aussagen zur Methode `leistungsprognose(Date datum)` in der Klasse `Mitglied` (Folie 121) ist korrekt?**
> - [ ] A) Die Methode implementiert eine direkte Assoziation zwischen `Mitglied` und `Wettkampf`, da sie auf `team[i].wettkampf[k].maxPunkte()` zugreift.
> - [ ] B) Die Methode zeigt eine Dependency zwischen `Mitglied` und `Wettkampf` an, da sie dynamisch auf Instanzen von `Wettkampf` zugreift, ohne eine feste Assoziation zu etablieren.
> - [ ] C) Die Methode verletzt das Prinzip der Kapselung, weil sie direkt auf interne Attribute von `Team` und `Wettkampf` zugreift.
> - [ ] D) Die Methode ist ein Beispiel für eine Aggregation, da sie eine "hat"-Beziehung zwischen `Mitglied` und `Team` modelliert.

>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Die Methode `leistungsprognose` greift auf Objekte von `Team` und `Wettkampf` zu, die ihr **nicht direkt zugeordnet** sind (sondern über eine Collection oder Parameter). Dies stellt eine **Dependency** dar, da die Beziehung nur für die Dauer des Methodenaufrufs besteht. Option A ist falsch, weil keine direkte Assoziation vorliegt, Option C ist irrelevant (die Kapselung wird hier nicht verletzt, sondern die Abhängigkeit modelliert), und Option D ist falsch, da Aggregationen spezifische "Teil-von"-Beziehungen sind, die hier nicht zutreffen.

---
> [!question] **Frage 3: Welche der folgenden Aussagen zu Interfaces und Dependencies (Folie 122) ist zutreffend?**
> - [ ] A) Ein Interface wie `Team` kann nur von Klassen implementiert werden, die eine Dependency zu `EventManagement` haben.
> - [ ] B) Die Dependency `<<use>>` zwischen `EventManagement` und `Team` zeigt an, dass `EventManagement` die Schnittstelle `Team` nutzt, um auf dessen Methoden zuzugreifen.
> - [ ] C) Interfaces ersetzen Dependencies vollständig, da sie alle dynamischen Abhängigkeiten abstrahieren.
> - [ ] D) Die Klasse `DDDTeam` implementiert `EventManagement` direkt, was eine Dependency `<<use>>` überflüssig macht.

>
> > [!success]- 🔑 Antwort anzeigen
> > **Richtige Antwort: B**
> >
> > *Erklärung*:
> > Die Notation `<<use>>` zwischen `EventManagement` und `Team` (Interface) bedeutet, dass `EventManagement` die Schnittstelle `Team` **nutzt** – also von ihr abhängt. Dies ist ein klassisches Beispiel für eine Dependency, bei der ein Client (hier `EventManagement`) ein Interface (hier `Team`) verwendet. Option A ist zu spezifisch, Option C ist falsch, da Interfaces Dependencies nicht ersetzen, sondern selbst eine Form von Abhängigkeit darstellen, und Option D ist falsch, weil `DDDTeam` das Interface `Team` implementiert, nicht `EventManagement`.