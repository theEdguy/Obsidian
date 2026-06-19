# KI-Regelwerk für Software-Engineering-Verarbeitung

> Systemregeln und Kontextvorgaben für KI-Assistenten basierend auf Prof. Dr. Thomas Fuchß: Software-Engineering.

**Version**: 1.0.0


---

## ⚙️ Allgemeine Regeln

- **never_do_more_than_requested:** Tue niemals mehr als verlangt. Halte die Antworten präzise, direkt und beschränke dich strikt auf die angeforderte Aufgabe.


---

# Kapitel 1: Die Notwendigkeit eines Prozesses

## 📖 Guidelines

### Das Problem
Die Entwicklung großer Software-Systeme birgt hohe Risiken wie mangelndes Problemverständnis, unterschätzte Komplexität und ineffiziente Ressourcennutzung. Ein naiver 'Codieren und Verbessern'-Ansatz führt schnell zu unbrauchbarem Code, fehlerhaftem Design und hohen Kosten, da Phasen wie Requirements-Analyse und systematisches Design übergangen werden.

### Die Lösung
Ein strukturiertes, ingenieurmäßiges Vorgehen unter Einsatz wissenschaftlich fundierter, empirischer Methoden und standardisierter Entwicklungsprozesse (Prozessmodelle wie Wasserfall, Spiral- oder Versionsmodell) is unabdingbar. Dies ermöglicht die Steuerung von Projekten durch Meilensteine, macht den Fortschritt transparent und minimiert Risiken frühzeitig.

## 🤖 KI-Anweisungen (AI Instructions)

- Vermittle dem Benutzer den Unterschied zwischen qualitativem (Verhalten/Motivation verstehen) und quantitativem (Messen/Analysieren) Vorgehen im Software Engineering.
- Stelle sicher, dass der Benutzer die empirischen Forschungsmethoden (kontrollierte Experimente, Fallstudien, Surveys, Post-Mortem-Analysen) voneinander abgrenzen und ihren jeweiligen Nutzen sowie ihre Grenzen benennen kann.
- Leite den Benutzer an, die Notwendigkeit von Meilensteinen für die Projektsteuerung und das Risikomanagement zu verstehen.
- Stelle sicher, dass der Benutzer die klassischen Prozessmodelle (Wasserfall, Spiralmodell, Versionsmodell) und deren Vor- und Nachteile versteht.


## 💡 Konzepte & Definitionen

### Software-Engineering

**Definition**:
Der Teil der Informatik, der sich mit der systematischen Entwicklung und Wartung softwarebasierter Anwendungen beschäftigt, um große Software-Systeme ingenieurmäßig unter Verwendung bewährter, systematischer Vorgehensweisen, Prinzipien, Methoden und Werkzeuge zu entwickeln.

### Qualitative Forschungsmethoden

**Definition**:
Empirischer Ansatz zur Untersuchung des 'Warum'. Ziel ist es, Verhalten, Meinungen und Motivationen zu verstehen und zu interpretieren (z. B. durch Beobachtungen, offene Fragen in Interviews).

### Quantitative Forschungsmethoden

**Definition**:
Empirischer Ansatz zur Untersuchung des 'Wie viel'. Ziel ist es, Zahlen, Korrelationen und Zusammenhänge zu ermitteln, zu messen und statistisch zu analysieren (z. B. durch geschlossene Fragen in Umfragen, Messungen).

### Kontrolliertes Experiment

**Definition**:
Wissenschaftliche Untersuchung von Ursache-Wirkungs-Beziehungen unter kontrollierten Laborbedingungen. Es werden unabhängige Variablen (Faktoren, die verglichen werden) systematisch manipuliert, um deren Einfluss auf abhängige Variablen (Messwerte) reproduzierbar zu bestimmen. Vorteil: Klare kausale Beziehungen. Kontra: Künstliche Umgebung erschwert Übertragbarkeit.

### Fallstudie (Case Study)

**Definition**:
Explorative Untersuchung realer Prozesse in ihrem natürlichen Umfeld (Beobachtung, Überwachung und Dokumentation). Sie liefert wertvolle Erkenntnisse und Zusammenhänge aus der Praxis, kann jedoch keine eindeutigen Ursache-Wirkungs-Beziehungen beweisen.

### Umfrage (Survey)

**Definition**:
Systematisches Sammeln von Daten aus einer großen Gruppe. Typische Techniken sind Fragebögen (mit geschlossenen Fragen für die quantitative Analyse) und Interviews (mit offenen Fragen für qualitative Einblicke). Kann deskriptiv, explorativ oder explanativ sein.

### Meilenstein

**Definition**:
Klar definierte Abschnitte oder Übergangspunkte in der Entwicklung einer Anwendung. Meilensteine helfen, den Fortschritt zu messen, und bilden die Grundlage für Steuermechanismen (z. B. Gegenmaßnahmen einleiten, Ressourcen anfordern, Projekt einstellen).

### Wasserfallmodell

**Definition**:
Klassisches, phasenbasiertes Prozessmodell (Analyse, Design, Coden, Integration/Test, Betrieb). Jede Phase ist vor dem Übergang vollständig abzuschließen, eine Rückkopplung ist im Regelfall nur im Fehlerfall vorgesehen.

### Spiralmodell

**Definition**:
Risiko-getriebenes Prozessmodell nach Boehm (1988), bei dem kontinuierliches Risikomanagement in jeder Schleife (Ziele bestimmen, Risiken eliminieren, entwickeln/verifizieren, nächste Phase planen) den Entwicklungsverlauf bestimmt. Schwierige Aufgaben mit hohem Risiko kommen zuerst.

### Versionsmodell

**Definition**:
Iteratives Prozessmodell, bei dem das System inkrementell in aufeinander aufbauenden Versionen (Teilsystemen) entwickelt und bewertet wird. Ermöglicht die Integration neuer Nutzeranforderungen und den frühen Einsatz eines Kernsystems.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welche Aussage beschreibt ein zentrales Merkmal einer Fallst...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, empirische_methoden, fallstudie`)


#### Aufgabenstellung:
Welche Aussage beschreibt ein zentrales Merkmal einer Fallstudie (Case Study) im Kontext empirischer Forschung?

A) Sie findet ausschließlich in kontrollierten Laborumgebungen statt, um Störfaktoren zu minimieren.
B) Sie untersucht reale Prozesse in ihrem natürlichen Umfeld und liefert explorative Erkenntnisse aus der Praxis.
C) Sie dient primär der Überprüfung von Kausalzusammenhängen durch systematische Manipulation unabhängiger Variablen.
D) Sie sammelt Daten durch standardisierte Fragebögen mit geschlossenen Fragen, um quantitative Analysen zu ermöglichen.


#### Musterlösung:
Richtige Antwort: B

Erklärung: Fallstudien zeichnen sich durch die Untersuchung realer Prozesse in ihrem natürlichen Umfeld aus. Sie sind explorativ und liefern Erkenntnisse aus der Praxis, zeigen aber keine klaren Ursache-Wirkung-Beziehungen (im Gegensatz zu kontrollierten Experimenten).


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung von Fallstudien (im natürlichen Umfeld, explorativ, keine Kausalität) mit kontrollierten Experimenten (im Labor, Manipulation von Variablen, Kausalität) oder Umfragen (Surveys).


---

### Aufgabe 2: Welche Aussage trifft auf die Durchführung eines kontrollier...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, empirische_methoden, experiment`)


#### Aufgabenstellung:
Welche Aussage trifft auf die Durchführung eines kontrollierten Experiments in der empirischen Softwareforschung zu?

A) Die Umgebung wird bewusst natürlich gehalten, um die Realitätsnähe zu erhöhen.
B) Die Ergebnisse sind nicht reproduzierbar, da sie stark vom Kontext abhängen.
C) Unabhängige Variablen werden systematisch manipuliert, um deren Einfluss auf abhängige Variablen zu messen.
D) Die Methode eignet sich besonders für die Erforschung subjektiver Qualitätsanforderungen, da sie qualitative Daten priorisiert.


#### Musterlösung:
Richtige Antwort: C

Erklärung: Kontrollierte Experimente manipulieren gezielt unabhängige Variablen unter kontrollierten Bedingungen, um deren Einfluss auf abhängige Variablen zu messen und reproduzierbare statistische Daten zu erheben.


#### Typische Stolpersteine / Fehlerquellen:
Die Annahme, Experimente fänden in einer natürlichen Umgebung statt (das trifft auf Fallstudien zu), oder die Annahme, ihre Ergebnisse seien nicht reproduzierbar (Reproduzierbarkeit ist ein Hauptziel).


---

### Aufgabe 3: Was ist ein wesentlicher Nachteil von kontrollierten Experim...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, empirische_methoden, validitaet`)


#### Aufgabenstellung:
Was ist ein wesentlicher Nachteil von kontrollierten Experimenten im Vergleich zu Fallstudien?

A) Fallstudien liefern keine reproduzierbaren Ergebnisse, während Experimente diese garantieren.
B) Experimente sind weniger aufwendig in der Durchführung, da sie keine reale Umgebung benötigen.
C) Die künstliche Umgebung von Experimenten erschwert die Übertragbarkeit der Ergebnisse auf die Praxis.
D) Fallstudien können keine quantitativen Daten sammeln, während Experimente dies ermöglichen.


#### Musterlösung:
Richtige Antwort: C

Erklärung: Die künstliche Umgebung und die streng kontrollierten Bedingungen in Laborexperimenten führen zu einer geringeren externen Validität, was die Übertragbarkeit der Ergebnisse auf reale, komplexe Softwareprojekte erschwert.


#### Typische Stolpersteine / Fehlerquellen:
Vergessen, dass auch Fallstudien quantitative Daten (z. B. Metriken) sammeln können, und Falscheinschätzung des Vorbereitungsaufwands von Laborexperimenten.


---



# Kapitel 2: Entwicklungsprozesse gestern und heute

## 📖 Guidelines

### Das Problem
Prozessmodelle werden oft starr, unvollständig oder dogmatisch gelebt, ohne sie an Technologie, Personen, Unternehmensstrukturen und Projektgrößen anzupassen. Ein fehlerhafter Prozess führt zu verfehlten Fristen, explodierenden Kosten und ineffektiver Qualitätssicherung.

### Die Lösung
Der Einsatz flexibler, iterativer und risikoorientierter Prozessmodelle als konfigurierbares Framework. Die Zerlegung in überschaubare Mini-Projekte (Iterationen/Sprints) mit Meilensteinen zur kontinuierlichen Messung und Risikominimierung, unterteilt in Phase I (Evaluierung/Vorprojekt) und Phase II (Umsetzung).

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer die CMMI-Fähigkeitsgrade (Capability Levels L0-L3) und Reifegrade (Maturity Levels L1-L5) sowie deren Bedeutung für den Projekterfolg kennt.
- Erkläre dem Benutzer den Aufbau eines iterativen Entwicklungsprozesses nach Craig Larman (Phase I mit Evaluierung/Vorprojekt, Phase II mit Umsetzung) und dessen Verbindung zu SCRUM.


## 💡 Konzepte & Definitionen

### Prozessmodell

**Definition**:
Ein Prozessmodell definiert die zu erbringenden Aufgaben und deren zeitliche Abfolge. Es bildet einen steuerbaren, transparenten Rahmen für eine effiziente Entwicklung, indem es Risiken verringert und die Vorhersehbarkeit erhöht.

### CMMI (Capability Maturity Model Integration)

**Definition**:
Ein Stufenmodell zur Bewertung der Fähigkeiten eines Unternehmens bei der Projektabwicklung. Es unterscheidet Capability Levels (Fähigkeitsgrade) und Maturity Levels (Reifegrade).

### CMMI Capability Levels

**Definition**:
Fähigkeitsgrade zur Bewertung einzelner Prozesse: L0 (Incomplete: nicht/teilweise durchgeführt), L1 (Performed: individuell befolgt), L2 (Managed: überwacht und gesteuert), L3 (Defined: präzise zugeschnitten und formal fixiert).

### CMMI Maturity Levels

**Definition**:
Reifegrade der gesamten Organisation: L1 (Initial: chaotisch), L2 (Managed: geplant/überwacht unter Stress), L3 (Defined: normiert/generisch), L4 (Quantitatively Managed: messbar/vorhersehbar), L5 (Optimizing: kontinuierliche Verbesserung).

### Iteration / Sprint

**Definition**:
Die Zerlegung eines großen Softwareprojekts in Mini-Projekte. Jede Iteration liefert ein lauffähiges Inkrement, baut auf vorherigen Modellen auf und fokussiert sich auf Use Cases. Risikoreiche Aufgaben werden zuerst gelöst.

### Phase I (Larman)

**Definition**:
Die Evaluierungsphase (Vorprojekt), in der zentrale Anforderungen analysiert, eine prinzipielle Architektur definiert, das Problemverständnis durch erste Vorversionen geschärft und Planungssicherheit gewonnen wird.

### Phase II (Larman)

**Definition**:
Die Erstellungs- und Umsetzungsphase, in der verbliebene Kernfunktionalitäten umgesetzt, die Architektur konsolidiert (Infrastruktur) und anschließend restliche Funktionalitäten ohne Architekturänderungen vervollständigt werden.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welche grundlegende Eigenschaft unterscheidet das Spiralmode...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, vorgehensmodelle, spiralmodell`)


#### Aufgabenstellung:
Welche grundlegende Eigenschaft unterscheidet das Spiralmodell nach Boehm von klassischen sequenziellen Modellen wie dem Wasserfallmodell?

A) Das Spiralmodell verzichtet vollständig auf Dokumentation und setzt stattdessen auf direkte Kommunikation.
B) Das Spiralmodell führt Risikomanagement als zentralen Steuerungsmechanismus ein und durchläuft iterative Schleifen mit klar definierten Phasen.
C) Das Spiralmodell ist ein rein lineares Modell, das jedoch durch Prototypen ergänzt wird.
D) Das Spiralmodell erzwingt eine strikte Trennung zwischen Analyse, Design und Implementierung in jeder Iteration.


#### Musterlösung:
Richtige Antwort: B

Erklärung: Das Spiralmodell nach Boehm (1988) zeichnet sich durch ein kontinuierliches Risikomanagement aus. Jede Schleife stellt eine Phase dar, in der schwierige Aufgaben mit hohem Risiko zuerst angegangen werden. Dies unterscheidet es fundamental vom klassischen Wasserfallmodell.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung des Spiralmodells mit einem rein linearen Prototypen-Ansatz oder der Annahme, es verzichte auf Dokumentation.


---

### Aufgabe 2: Welche Aussage zum Scrum-Framework ist fachlich korrekt?

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, vorgehensmodelle, scrum`)


#### Aufgabenstellung:
Welche Aussage zum Scrum-Framework ist fachlich korrekt?

A) Scrum sieht vor, dass das Entwicklungsteam in jeder Iteration (Sprint) eine vollständige, marktreife Software liefern muss.
B) Scrum ist ein hybrides Modell, das Elemente des Wasserfalls und des Spiralmodells kombiniert.
C) Scrum basiert auf iterativen Sprints, in denen Anforderungen priorisiert und in Inkrementen umgesetzt werden, wobei das Product Backlog kontinuierlich angepasst wird.
D) Scrum erfordert eine feste Rollenverteilung, bei der der Product Owner für die technische Umsetzung verantwortlich ist.


#### Musterlösung:
Richtige Antwort: C

Erklärung: Scrum ist ein agiles Framework basierend auf iterativen Sprints. Das Product Backlog wird kontinuierlich angepasst und verfeinert (Grooming), und am Ende jedes Sprints steht ein potenziell auslieferbares Produktinkrement (nicht zwingend marktreife Software). Der Product Owner ist für die Anforderungen zuständig, nicht die technische Umsetzung.


#### Typische Stolpersteine / Fehlerquellen:
Die Annahme, dass das Inkrement pro Sprint marktreif sein muss, oder dass der Product Owner für die Technik verantwortlich ist.


---



# Kapitel 3: Objektorientierung – eine durchgängige Sichtweise

## 📖 Guidelines

### Das Problem
Klassische Softwareentwicklung trennte Daten und Funktionen strikt. Dies führte bei großen Anwendungen zu mangelnder Wartbarkeit, Konsistenzproblemen und schlechter Abbildung komplexer realer Szenarien (Problemraum) im Code (Lösungsraum).

### Die Lösung
Einsatz von Objektorientierung (OO) als durchgängiges Stilmittel. OO begreift Daten und Funktionen als Einheit (Klassen/Objekte) und bietet methodische Durchgängigkeit von der Analyse (UML-Klassen) bis zur Implementierung (Code-Klassen).

## 🤖 KI-Anweisungen (AI Instructions)

- Erkläre die drei historischen Säulen der Objektorientierung: Natürliche Modellierung (Simula), Sharing (Smalltalk) und Abstrakte Datentypen (Eiffel).
- Stelle sicher, dass der Benutzer den Unterschied zwischen Objektidentität (Derselbe) und Objektgleichheit (Der gleiche) versteht und anwenden kann.


## 💡 Konzepte & Definitionen

### Historische Säulen der OO

**Definition**:
1. Natürliche Modellierung (Simula 67): Objekte modellieren die Realität. 2. Sharing (Smalltalk-80): Objekte teilen sich gemeinsame Eigenschaften (super/self). 3. Abstrakte Datentypen (Eiffel): Objekte kapseln ihren Zustand über definierte Schnittstellen.

### Treaty of Orlando (1989)

**Definition**:
Definiert zwei Mechanismen der Vererbung: 1. Empathy (Nachempfinden): Ein Objekt teilt das Verhalten eines anderen ohne explizite Redefinition (Delegation). 2. Templates: Fähigkeit, neue Objekte basierend auf Vorlagen zu erstellen.

### Methodische Durchgängigkeit

**Definition**:
Die nahtlose Übertragung von Strukturen aus dem Problemraum (Anforderungsanalyse) über das UML-Modell (Designraum) in den Quellcode (Lösungsraum), z. B. die Repräsentation eines 'Mitglieds' auf allen Ebenen.

### Abstraktion (Modellierung)

**Definition**:
Ein Modell ist ein Abbild der Realität, das von irrelevanten Details abstrahiert und nur die für das konkrete Problem relevanten Eigenschaften betrachtet.

### Objektidentität vs. Objektgleichheit

**Definition**:
Objektidentität (== in Java/C++): Zwei Referenzen zeigen auf exakt dasselbe Objekt im Speicher. Objektgleichheit (.equals() in Java): Zwei unterschiedliche Objekte besitzen identische Attributwerte.


**Beispiel / Code**:
```cpp
String x = new String("test");
String y = new String("test");
System.out.println(x == y);      // false (nicht identisch)
System.out.println(x.equals(y)); // true (gleich)
```

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Gegeben sind in Java zwei Instanzen:

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, objektorientierung, identitaet`)


#### Aufgabenstellung:
Gegeben sind in Java zwei Instanzen:
`String x = new String("text");` und `String y = new String("text");`.
Welches Ergebnis liefern die Ausdrücke `(x == y)` und `x.equals(y)`?

A) Beide liefern `true`.
B) Beide liefern `false`.
C) `(x == y)` liefert `true`, `x.equals(y)` liefert `false`.
D) `(x == y)` liefert `false`, `x.equals(y)` liefert `true`.


#### Musterlösung:
Richtige Antwort: D

Erklärung: Der Operator `==` prüft die Objektidentität (zeigen x und y auf denselben Speicherbereich?). Da beide mit `new` erzeugt wurden, sind sie unterschiedliche Objekte (false). Die Methode `equals()` prüft die inhaltliche Gleichheit (ist der Text derselbe?), was hier zutrifft (true).


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung von Identität (derselbe) und Gleichheit (der gleiche). Besondere Optimierungen wie String-Pooling in Java können bei Literalen (ohne 'new') verwirren.


---



# Kapitel 4: Objektorientierung – Vererbung

## 📖 Guidelines

### Das Problem
Redundante Daten- und Verhaltensstrukturen führen zu aufgeblähtem und schwer wartbarem Code. Ohne einheitliche Schnittstellen und Typbeziehungen können Klassen nicht flexibel miteinander kombiniert oder ausgetauscht werden.

### Die Lösung
Einsatz von Vererbung zur Strukturierung von Generalisierungen und Spezialisierungen. Unterklassen erben Eigenschaften und Beziehungen ihrer Oberklassen, können diese überschreiben und erweitern, und sind über das Substitutionsprinzip typkompatibel.

## 🤖 KI-Anweisungen (AI Instructions)

- Erkläre das Liskovsche Substitutionsprinzip anhand des klassischen Beispiels Quadrat vs. Rechteck.
- Stelle sicher, dass der Benutzer die 4 Schichten der MOF-Architektur (M0 bis M3) benennen und einordnen kann.
- Erkläre die Generalisierungsbedingungen in UML: overlapping vs. disjoint und complete vs. incomplete.
- Vermittle die UML-Syntax für Attribute, Operationen, abstrakte Klassen und Interfaces.


## 💡 Konzepte & Definitionen

### Substitutionsprinzip (Liskov)

**Definition**:
Instanzen von Unterklassen müssen sich so verhalten, dass sie überall dort eingesetzt werden können, wo Instanzen der Oberklasse erwartet werden, ohne die Korrektheit des Programms zu gefährden.

### Quadrat-Rechteck-Problem

**Definition**:
Ein klassischer Verstoß gegen das Substitutionsprinzip: Erbt Quadrat von Rechteck, verletzt Quadrat die Rechteck-Eigenschaft (Breite und Höhe unabhängig veränderbar, z. B. stretch(w, h)), da beim Quadrat w = h gelten muss.


**Beispiel / Code**:
```cpp
Rechteck r = new Quadrat(3);
r.setBreite(4);
r.setHoehe(5);
// Wenn r ein Quadrat ist, gilt nun Breite=5, Hoehe=5. Erwartet wurde aber Flaeche 20!
```

### MOF-Schichten (Meta Object Facility)

**Definition**:
M3 (Meta-Meta-Modell): Definiert die Sprache für Meta-Modelle (z. B. MOF). M2 (Meta-Modell): Definiert die Modellierungssprache (z. B. UML: Class, Association). M1 (Modell): Ein konkretes Diagramm (z. B. Klasse Mitglied). M0 (Reale Objekte/Laufzeit): Konkrete Programminstanzen im Speicher oder Datenbankdatensätze.

### UML Attribut-Syntax

**Definition**:
Syntax: visibility / name : type [multiplicity] = initial-value {property}. Z. B. - alter: Date. Das Zeichen '/' markiert ein abgeleitetes (berechenbares) Attribut. Multiplizität legt fest, wie viele Werte existieren.

### Generalisierungsbedingungen in UML

**Definition**:
overlapping: Instanzen können in mehreren Unterklassen gleichzeitig sein. disjoint: Keine Schnittmengen. complete: Keine weiteren Unterklassen außerhalb möglich. incomplete: Weitere Unterklassen sind zulässig und sinnvoll.

### Abstrakte Klasse vs. Interface

**Definition**:
Abstrakte Klasse: Kann Struktur (Attribute) und Implementierungen vererben; keine direkten Instanzen. Interface: Vererbt ausschließlich Operationen (Schnittstellen), besitzt im Regelfall keine Attribute oder Assoziationen.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Warum ist die Vererbung `Quadrat erbt von Rechteck` im Sinne...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, objektorientierung, liskov, vererbung`)


#### Aufgabenstellung:
Warum ist die Vererbung `Quadrat erbt von Rechteck` im Sinne des Liskovschen Substitutionsprinzips problematisch?

A) Weil ein Quadrat geometrisch kein Rechteck ist.
B) Weil Operationen des Rechtecks wie `stretch(width, height)` oder unabhängige Setter die Invariante des Quadrats (Breite = Höhe) verletzen.
C) Weil Java keine Mehrfachvererbung unterstützt.
D) Weil das Quadrat weniger Attribute als das Rechteck benötigt.


#### Musterlösung:
Richtige Antwort: B

Erklärung: Das Substitutionsprinzip verlangt, dass ein Quadrat überall dort verwendet werden kann, wo ein Rechteck erwartet wird. Wenn ein Client auf einem Rechteck-Objekt die Breite und Höhe unabhängig voneinander ändert (z.B. setBreite(4), setHoehe(5)), bricht diese Logik bei einem Quadrat zusammen, da sich dessen Invariante (w == h) nicht aufrechterhalten lässt, ohne das Verhalten der Oberklasse zu verfälschen.


#### Typische Stolpersteine / Fehlerquellen:
Umgangssprachliches Denken ('Ein Quadrat ist doch ein Rechteck') kollidiert hier mit der Verhaltenskompatibilität im Softwaredesign.


---

### Aufgabe 2: Ordne die UML-Modellierungsebene einer konkreten Klasse (z.B...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, metamodellierung, mof`)


#### Aufgabenstellung:
Ordne die UML-Modellierungsebene einer konkreten Klasse (z.B. 'class Mitglied') und einer konkreten Instanz zur Laufzeit (z.B. 'new Mitglied("Meier")') den korrekten Schichten der MOF-Architektur (Meta Object Facility) zu.

A) Klasse = M3, Instanz = M2
B) Klasse = M2, Instanz = M1
C) Klasse = M1, Instanz = M0
D) Klasse = M2, Instanz = M0


#### Musterlösung:
Richtige Antwort: C

Erklärung: In der MOF-Architektur ist M1 die Modell-Ebene (wo wir Klassen wie 'Mitglied' modellieren). M0 ist die Laufzeit-Ebene mit den realen Objekten im Speicher ('Meier'). M2 enthält das Meta-Modell (die UML-Definition von 'Class' und 'Attribute'), und M3 ist das Meta-Meta-Modell.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung der Klassendefinition (M1) mit dem UML-Metamodell (M2).


---



# Kapitel 5: Objektorientierung – Komposition, Aggregation und Assoziation

## 📖 Guidelines

### Das Problem
Softwareobjekte müssen miteinander interagieren, um komplexe Aufgaben zu lösen. Ohne strukturierte Modellierung von Beziehungen (Assoziationen, Aggregationen, Kompositionen) entstehen unübersichtliche Abhängigkeiten und Speicherlecks durch unklare Objektlebenszyklen.

### Die Lösung
Nutzung differenzierter UML-Beziehungen. Die Assoziation als allgemeine Verbindung, die Aggregation als schwache Teile-Ganzes-Beziehung (Teile existieren unabhängig) und die Komposition als starke Teile-Ganzes-Beziehung (existenzabhängige Teile, erzeugt/zerstört durch das Ganze).

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer Komposition und Aggregation präzise voneinander abgrenzen kann, insbesondere bezüglich der Existenzabhängigkeit und Erzeugungs-/Zerstörungsverantwortung.
- Erkläre die Notation und Semantik von Multiplizitäten, Rollenbezeichnern, Navigierbarkeit, Assoziationsklassen und Qualifiers in UML-Diagrammen.
- Vermittle das Konzept von Abhängigkeiten (Dependencies/<<use>>) und deren Abgrenzung zu permanenten Assoziationen.


## 💡 Konzepte & Definitionen

### Assoziation (UML)

**Definition**:
Die allgemeinste Beziehung zwischen Klassen, dargestellt als Linie. Beschreibt, dass Instanzen miteinander kommunizieren können. Kann Multiplizitäten, Rollenbezeichnungen und Richtungen (Navigierbarkeit) besitzen.

### Assoziationsklasse

**Definition**:
Eine Klasse, die einer Assoziation zugeordnet ist. Sie wird verwendet, wenn Eigenschaften oder Beziehungen nicht eindeutig einer der beteiligten Klassen zugewiesen werden können (z.B. 'Ranking' oder 'seit'-Datum bei einer Vereinsmitgliedschaft).

### Qualifier

**Definition**:
Ein UML-Element, das an einem Assoziationsende platziert wird. Er partitioniert die menge der assoziierten Objekte und ermöglicht den gezielten Zugriff (vergleichbar mit einem Schlüssel in einer Map/Dictionary).

### Komposition (UML)

**Definition**:
Starke Teile-Ganzes-Beziehung (gefüllte Raute). Teile sind existenzabhängig vom Ganzen und können nicht zu mehreren Ganzen gehören. Das Ganze verantwortet die Erzeugung und Zerstörung der Teile. Multiplizität auf Seite des Ganzen ist stets 1.

### Aggregation (UML)

**Definition**:
Schwache Teile-Ganzes-Beziehung (leere Raute). Teile sind existenzunabhängig und können ohne das Ganze existieren oder an mehreren Aggregaten beteiligt sein. Das Aggregat agiert oft als Stellvertreter.

### Abhängigkeit (Dependency / <<use>>)

**Definition**:
Eine temporäre Beziehung (gestrichelter Pfeil). Zeigt an, dass eine Klasse eine andere temporär nutzt (z. B. als Methodenparameter oder lokales Objekt), ohne eine dauerhafte Assoziation (Instanzvariable) zu halten.


**Beispiel / Code**:
```cpp
public int leistungsprognose(Date datum) {
    // Temporäre Nutzung von Date; Dependency <<use>> auf Date
}
```

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welche Aussage beschreibt den Unterschied zwischen einer Agg...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, objektorientierung, beziehungen, komposition`)


#### Aufgabenstellung:
Welche Aussage beschreibt den Unterschied zwischen einer Aggregation und einer Komposition in UML korrekt?

A) Bei der Aggregation können Teile nicht ohne das Ganze existieren, bei der Komposition schon.
B) Die Komposition ist eine exklusive Besitzbeziehung mit Existenzabhängigkeit (Teil stirbt mit dem Ganzen); bei der Aggregation können Teile unabhängig existieren.
C) Aggregations-Teile werden immer zur Compilezeit erzeugt, Kompositions-Teile zur Laufzeit.
D) Komposition wird durch eine leere Raute dargestellt, Aggregation durch eine gefüllte Raute.


#### Musterlösung:
Richtige Antwort: B

Erklärung: Bei der Komposition (gefüllte Raute) liegt eine starke Existenzabhängigkeit vor. Das Ganze steuert den Lebenszyklus der Teile. Bei der Aggregation (leere Raute) handelt es sich um eine lose Kopplung; die Teile existieren unabhängig weiter, wenn das Aggregat zerstört wird (z. B. ein Buch im Bücherregal).


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung der Rauten (gefüllt = Komposition/stark, leer = Aggregation/schwach) und Missinterpretation der Lebenszyklus-Verantwortlichkeiten.


---



# Kapitel 6: Requirements

## 📖 Guidelines

### Das Problem
Das Entwickeln von Software ohne klares Problemverständnis führt zum Scheitern von Projekten, da falsche Funktionalitäten implementiert, Risiken ignoriert und Aufwände unterschätzt werden. Subjektive nicht-funktionale Anforderungen lassen sich ohne konkrete Kriterien nicht bewerten.

### Die Lösung
Ein systematisches Anforderungsmanagement in Phase I (Evaluierung). Erfassung funktionaler Anforderungen (Systemfunktionen) und nicht-funktionaler Anforderungen (Qualitätseigenschaften), die über Metriken objektivierbar gemacht werden. Strukturierung der Anforderungen in Use Cases.

## 🤖 KI-Anweisungen (AI Instructions)

- Grenze funktionale Anforderungen, nicht-funktionale Anforderungen und technische Randbedingungen (Constraints) sauber voneinander ab.
- Stelle sicher, dass der Benutzer die Bedeutung von Metriken zur Bewertung nicht-funktionaler Anforderungen versteht.
- Erkläre die Arbeitsschritte im Detailprozess 'Aufgabe verstehen' nach Larman (Plan, Report, Requirements, Use Cases, Analysemodell, Systemarchitektur, Wiki).


## 💡 Konzepte & Definitionen

### Funktionale Anforderungen

**Definition**:
Beschreiben konkrete Systemfunktionen, Dienste oder Berechnungen, die das System ausführen können muss (z. B. 'System berechnet Mitgliedsbeitrag automatisch').

### Nicht-funktionale Anforderungen (NFA)

**Definition**:
Definieren qualitative Eigenschaften, Einschränkungen oder Kriterien des Systems (z. B. Performance, Zuverlässigkeit, Benutzbarkeit, Sicherheit).

### Technische Randbedingungen (Constraints)

**Definition**:
Vorgaben, die den Lösungsraum einschränken (z. B. einzusetzende Programmiersprachen, Betriebssystemkompatibilität, Datenbanken oder Protokolle wie OAuth 2.0).

### Metrik

**Definition**:
Messbare und objektive Kriterien (z. B. Antwortzeit in Sekunden, Ausfallrate in Prozent), um NFAs bewertbar und überprüfbar zu machen und deren Subjektivität aufzuheben.

### Aufgabe verstehen (Larman)

**Definition**:
7-Schritte-Vorprojekt: 1. Vorläufiger Plan, 2. Erster Report (Motivation/Ziel), 3. Zentrale Requirements (Lastenheft), 4. Use Cases, 5. Erstes Analysemodell, 6. Erste Systemarchitektur, 7. Plan verfeinern (Meilensteine/Iterationen). Begleitet von einem Wiki.

### Iterations-Erfolgsfaktoren

**Definition**:
Risiken, die den Erfolg einer Iteration gefährden: Einführung neuer Technologien, Personalprobleme/Mangel an Experten, hoher Koordinationsaufwand im Team und Unterschätzen der Architektur-Komplexität.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welche der folgenden Anforderungen stellt eine nicht-funktio...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, requirements, nfa`)


#### Aufgabenstellung:
Welche der folgenden Anforderungen stellt eine nicht-funktionale Anforderung dar?

A) Das System muss Benutzer authentifizieren können.
B) Die Authentifizierung muss mit OAuth 2.0 erfolgen.
C) Die Authentifizierung darf maximal 5 Sekunden dauern.
D) Die Authentifizierung muss in der Datenbank gespeichert werden.


#### Musterlösung:
Richtige Antwort: C

Erklärung: NFAs beschreiben Qualitätseigenschaften. Eine Antwortzeit von 'maximal 5 Sekunden' is ein messbares Qualitätskriterium. A ist eine funktionale Anforderung (was das System tut), B und D sind technische Randbedingungen (Constraints für Protokoll und Speicherung).


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung von NFAs (Qualitätseigenschaften) mit technischen Randbedingungen (Constraints/Umsetzungsvorgaben).


---

### Aufgabe 2: Warum sind Metriken bei nicht-funktionalen Anforderungen (NF...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, requirements, metriken`)


#### Aufgabenstellung:
Warum sind Metriken bei nicht-funktionalen Anforderungen (NFA) wichtig?

A) Weil sie die subjektive Natur nicht-funktionaler Anforderungen messbar und bewertbar machen.
B) Weil sie die Entwicklungskosten reduzieren.
C) Weil sie die funktionalen Anforderungen ersetzen.
D) Weil sie die Architektur des Systems automatisch generieren.


#### Musterlösung:
Richtige Antwort: A

Erklärung: Nicht-funktionale Anforderungen wie 'Benutzerfreundlichkeit' oder 'hohe Performance' sind subjektiv und vage. Erst durch Metriken (z. B. 'Kontrastverhältnis von 4,5:1' oder '99,9% Verfügbarkeit') werden sie objektiv testbar und vertraglich überprüfbar.


#### Typische Stolpersteine / Fehlerquellen:
Die falsche Vorstellung, Metriken würden Kosten senken oder automatisch Code generieren.


---



# Kapitel 7: Use Cases erstellen und beschreiben

## 📖 Guidelines

### Das Problem
Requirements liegen oft nur als unstrukturierte, vage Wunschlisten vor. Ohne systematische Aufbereitung entstehen Missverständnisse über den Systemumfang, und es fehlen klare Abgrenzungen zur Umgebung (Wer macht was?).

### Die Lösung
Einsatz von Use Cases (Anwendungsfällen) zur Beschreibung zusammenhängender Interaktionseinheiten aus Sicht der Akteure. Die Modellierung erfolgt über Use-Case-Diagramme mit Akteuren, Systemgrenzen und gerichteten Beziehungen (<<include>>, <<extend>>, Generalisierung).

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer einen Use Case korrekt von einer einzelnen Aktion abgrenzen kann (ein Use Case ist eine fachlich sinnvolle Einheit, kein einzelner Schritt wie 'Mail senden').
- Erkläre die Beziehungen zwischen Use Cases in UML: <<include>> (Abläufe wiederverwenden), <<extend>> (optionale Erweiterung am Extension Point) und Generalisierung (Spezialfall).


## 💡 Konzepte & Definitionen

### Use Case (Anwendungsfall)

**Definition**:
Eine zusammenhängende Einheit von Aktionen aus Benutzersicht, die einen fachlich sinnvollen Ablauf im Anwendungsumfeld beschreibt. Er bildet die Basis für Analyse, Design, Implementierung und Tests.

### Akteur (UML)

**Definition**:
Eine externe Entität (Mensch, Rolle oder Fremdsystem), die außerhalb des betrachteten Systems liegt, aber an der Durchführung eines Use Cases beteiligt ist oder von dessen Ergebnissen betroffen ist.

### Systemgrenze (UML)

**Definition**:
Die visuelle Abgrenzung im Use-Case-Diagramm, die festlegt, welche Funktionalitäten Teil des zu entwickelnden Systems sind (innerhalb der Systemgrenze) und welche extern liegen (Akteure).

### <<include>> (Beziehung)

**Definition**:
Einordnung eines Use Cases in einen anderen. Der eingebundene Use Case wird zwingend als Ganzes im Ablauf des aufrufenden Use Cases ausgeführt. Dient der Vermeidung von Redundanz.

### <<extend>> (Beziehung)

**Definition**:
Eine optionale Erweiterung eines Basis-Use-Cases. Der erweiternde Use Case wird nur dann ausgeführt, wenn eine definierte Bedingung an einem bestimmten Extension Point erfüllt ist.

### Generalisierung (Use Case)

**Definition**:
Eine Beziehung, bei der ein spezialisierter Use Case das Verhalten und die Beziehungen eines allgemeineren Use Cases erbt und ggf. erweitert oder überschreibt.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welche der folgenden Aussagen beschreibt korrekt die Rolle v...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, use_cases, prozess`)


#### Aufgabenstellung:
Welche der folgenden Aussagen beschreibt korrekt die Rolle von Use Cases im Software-Engineering-Prozess?

A) Use Cases dienen ausschließlich der Dokumentation von nicht-funktionalen Anforderungen und haben keine Bedeutung für die Architektur.
B) Use Cases sind nur für die Testphase relevant, da sie die Grundlage für Testfälle bilden.
C) Use Cases helfen bei der Strukturierung und Organisation des Projekts, indem sie Anforderungen in zentrale Abläufe überführen und die Grundlage für Analyse, Architektur, Design und Tests bilden.
D) Use Cases ersetzen klassische Anforderungsdokumente wie Lasten- und Pflichtenhefte vollständig.


#### Musterlösung:
Richtige Antwort: C

Erklärung: Use Cases bilden die methodische Grundlage für den gesamten Entwicklungsprozess. Sie bündeln Anforderungen in didaktisch und technisch nachvollziehbare Einheiten, die sowohl für das Design (UML) als auch für die Implementierung und Testfallerstellung verwendet werden.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung von Use Cases mit reinen Testartefakten oder der Annahme, sie würden alle sonstigen Anforderungsdokumente ersetzen.


---

### Aufgabe 2: Ein Use Case 'Buch bestellen' soll um den Use Case 'Zahlung ...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, use_cases, beziehungen`)


#### Aufgabenstellung:
Ein Use Case 'Buch bestellen' soll um den Use Case 'Zahlung prüfen' erweitert werden. Welche Beziehung ist zu verwenden, wenn die Prüfung immer durchgeführt werden muss?

A) Generalisierung
B) <<extend>>
C) <<include>>
D) Assoziation ohne Stereotyp


#### Musterlösung:
Richtige Antwort: C

Erklärung: Wenn ein Anwendungsfall zwingend ein anderes Verhalten erfordert, wird dies über eine <<include>>-Beziehung modelliert. Ein <<extend>> wird verwendet, wenn das Verhalten optional bzw. bedingt ist.


#### Typische Stolpersteine / Fehlerquellen:
Falsche Richtung bei extend (extend zeigt vom optionalen Zweig zum Basis-Use-Case) und Verwechslung von Pflicht (include) und Option (extend).


---



# Kapitel 8: Use Cases verstehen

## 📖 Guidelines

### Das Problem
Use Cases geben nur den groben Interaktionsrahmen vor. Ohne detaillierte Untersuchung der verschiedenen Ablaufszenarien bleibt unklar, wie das System in konkreten Situationen reagiert und wie die Klassen zur Laufzeit interagieren.

### Die Lösung
Verfeinerung von Use Cases über Szenarien (Szenariobeschreibungen). Komplexe Abläufe und logische Zusammenhänge werden mithilfe von Aktivitätsdiagrammen (Aktionen, Transitionen, Verzweigungen, Split/Join, Objektknoten, Parameter/Pins, Swimlanes) visualisiert, um Klassen und Operationen präzise zu spezifizieren.

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer den Unterschied zwischen High-Level-Use-Cases (grober Überblick) und erweiterten Use-Cases (detaillierte Szenarien) versteht.
- Erkläre das Konzept von Szenarien als konkreten Ausprägungen (Instanzen) eines Use Cases.
- Vermittle den Nutzen von Aktivitätsdiagrammen (Activity Diagrams) in UML zur Modellierung von Workflows, Algorithmen und Datenflüssen.


## 💡 Konzepte & Definitionen

### Szenario

**Definition**:
Eine konkrete Instanz oder Ausprägung eines Use Cases, die eine bestimmte Interaktionssequenz zwischen Akteuren und dem System beschreibt. Komplexe Use Cases benötigen meist mehrere Szenarien (z. B. Erfolgsfall vs. Fehlerfall).

### Aktivitätsdiagramm (UML)

**Definition**:
Ein UML-Verhaltensdiagramm zur Darstellung von Abläufen und Workflows als zusammenhängende Aktionen. Ein Übergang (Transition) erfolgt automatisch nach Abschluss einer Aktion (im Gegensatz zu zustandsgesteuerten Transitionen).

### High-Level Use Case

**Definition**:
Ein Anwendungsfall, der in wenigen Sätzen den zentralen Ablauf beschreibt. Dient in der frühen Phase zum schnellen Aufbau eines gemeinsamen Problemverständnisses.

### Erweiterter Use Case

**Definition**:
Detaillierte textuelle Beschreibung eines Anwendungsfalls unter Berücksichtigung von Akteuren, Vorbedingungen, Nachbedingungen, Hauptszenario (Erfolgsablauf) und Alternativszenarien (Ausnahmen).

### Objektknoten (UML)

**Definition**:
Elemente in Aktivitätsdiagrammen zur Modellierung des Datenflusses. Sie fungieren als Container für Objekte eines Typs und können Zustände definieren (z. B. [Zustand]).

### Swimlanes (Aktivitätsdiagramm)

**Definition**:
Organisatorische oder architektonische Verantwortungsbereiche (Spalten/Zeilen) in Aktivitätsdiagrammen, denen Aktionen eindeutig zugeordnet werden (z. B. Akteure, Subsysteme).

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Was unterscheidet ein Aktivitätsdiagramm (Activity Diagram) ...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, uml, aktivitaetsdiagramm`)


#### Aufgabenstellung:
Was unterscheidet ein Aktivitätsdiagramm (Activity Diagram) primär von einem Zustandsdiagramm (State Machine) in UML?

A) Aktivitätsdiagramme stellen keine Verzweigungen dar.
B) Aktivitätsdiagramme sind Strukturdiagramme, Zustandsdiagramme sind Verhaltensdiagramme.
C) In Aktivitätsdiagrammen werden Transitionen durch den Abschluss einer Aktion (Activity) ausgelöst, während in Zustandsdiagrammen explizite Ereignisse (Events) Zustandsübergänge triggern.
D) Zustandsdiagramme dürfen keine Schleifen enthalten.


#### Musterlösung:
Richtige Antwort: C

Erklärung: Ein Aktivitätsdiagramm zeigt den Kontrollfluss von Aktion zu Aktion; Übergänge finden statt, sobald eine Aktion abgeschlossen ist. Ein Zustandsdiagramm zeigt Zustände eines Objekts und wechselt diese typischerweise als Reaktion auf asynchrone, externe Ereignisse.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung des Begriffs 'Zustand' (State) mit einer 'Aktivität' (Activity). Beide Diagramme stellen dynamisches Verhalten dar.


---



# Kapitel 9: Use Cases interpretieren

## 📖 Guidelines

### Das Problem
Use Cases und Anforderungen beschreiben fachliche Abläufe, bieten aber keine direkte Systemstruktur. Ohne systematische Interpretation bleibt der Übergang zum Klassendesign und zu konkreten Systemschnittstellen unklar.

### Die Lösung
Identifikation von Konzepten/Klassen der Problemdomäne (z. B. via Checkliste von Kategorien oder Noun-Extraction aus Beschreibungen). Entwicklung von System-Sequenz-Diagrammen (SSD) zur Ermittlung von Systemereignissen und Operationen, inklusive detaillierter Beschreibungen (Name, Vor-/Nachbedingungen, Ausnahmen).

## 🤖 KI-Anweisungen (AI Instructions)

- Leite den Benutzer an, Klassen der Problemdomäne über Substantiv-Analyse (Noun Extraction) und Checklisten (Dinge, Rollen, Prozesse, Ereignisse) zu identifizieren.
- Erkläre die Faustregel: Dinge, die man anfassen kann und keine reinen Werte (Texte, Zahlen) sind, sind Konzepte/Klassen, keine Attribute.
- Vermittle den Aufbau von System-Sequenz-Diagrammen (SSD) mit Lifelines, Activation Bars und UML-Fragmenten (loop, alt, opt).


## 💡 Konzepte & Definitionen

### Noun Extraction (Substantivanalyse)

**Definition**:
Eine Technik zum Auffinden von Domänenkonzepten, bei der alle Substantive in Use-Case-Beschreibungen gesammelt und als potenzielle Klassenkandidaten bewertet werden.

### Konzept-Kategorien-Checkliste

**Definition**:
Eine Liste typischer Kategorien zur Identifikation von Objekten (z. B. physische Dinge, Rollen, Organisationen, Prozesse, Ereignisse), um die Noun-Extraction abzusichern.

### System-Sequenz-Diagramm (SSD)

**Definition**:
Ein UML-Interaktionsdiagramm, das für ein Szenario eines Use Cases die Interaktionen zwischen externen Akteuren und dem System als Blackbox darstellt, um Systemoperationen zu identifizieren.

### UML-Fragmente (alt, opt, loop)

**Definition**:
Strukturelemente in Sequenzdiagrammen zur Modellierung von Kontrollflüssen: 'alt' für Alternativen (if-else), 'opt' für optionale Abläufe (if) und 'loop' für Iterationen.

### Systemoperation (Schnittstelle)

**Definition**:
Eine vom System bereitgestellte Schnittstellenfunktion, die durch ein externes Systemereignis (Trigger) eines Akteurs ausgelöst wird.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: In welcher Phase des Software-Entwicklungsprozesses wird ein...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, analyse, ssd`)


#### Aufgabenstellung:
In welcher Phase des Software-Entwicklungsprozesses wird ein System-Sequenzdiagramm (SSD) typischerweise erstellt und welchen Hauptzweck erfüllt es?

A) In der Analysephase, um die Schnittstellen eines Use Cases zu identifizieren.
B) In der Designphase, um die Implementierungsdetails einer Klasse zu spezifizieren.
C) In der Analysephase, um die statische Struktur des Systems zu modellieren.
D) In der Testphase, um die Korrektheit der Klassenimplementierung zu verifizieren.


#### Musterlösung:
Richtige Antwort: A

Erklärung: SSDs zeigen das System als Blackbox und stellen die Interaktionen mit externen Akteuren dar. Sie dienen in der Analysephase dazu, die notwendigen Systemoperationen (Schnittstellen) zu bestimmen, bevor internes Klassendesign stattfindet.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung von SSDs (Blackbox, System-Schnittstellen) mit normalen Sequenzdiagrammen (Whitebox, interne Objekt-Interaktionen) oder Klassendiagrammen.


---



# Kapitel 10: Von der Analyse zur Systemarchitektur

## 📖 Guidelines

### Das Problem
Ein ungeordnetes System ohne Schichteneinteilung leidet unter hoher Kopplung und mangelnder Wartbarkeit. Wenn Präsentationsschicht, Logikschicht und Persistenzschicht stark miteinander verwoben sind, führt dies zu Performanceproblemen, Sicherheitslücken und starr gekoppelten Komponenten.

### Die Lösung
Einführung eines Drei-Schichtenmodells (Präsentation, Logik/Business, Persistenz/Datenzugriff) mit einer klaren Richtung der Abhängigkeiten (höhere Schichten nutzen tiefere, niemals umgekehrt). Modellierung der physischen Komponenten über Komponentendiagramme (mit Ports und Assembly/Delegation Connectors) und Deployment-Diagramme.

## 🤖 KI-Anweisungen (AI Instructions)

- Erkläre die Architekturprinzipien des Drei-Schichtenmodells und die strikte Trennung von Benutzeroberfläche und Businesslogik (UI triggers, logic executes).
- Stelle sicher, dass der Benutzer die Konzepte Interoperabilität, Portabilität und Erweiterbarkeit verteilter Systeme kennt.
- Vermittle den Aufbau von UML-Komponentendiagrammen (Components, Ports, Assembly/Delegation Connectors) und UML-Deployment-Diagrammen (Devices, Deployed Artifacts).


## 💡 Konzepte & Definitionen

### Drei-Schichtenmodell

**Definition**:
Die Aufteilung einer Anwendung in Präsentationsschicht (Zugriff über Fenster/Webseiten), Logikschicht (Businesslogik) und Persistenzschicht (Datenbankanbindung, Drittsysteme).

### Interoperabilität

**Definition**:
Die Fähigkeit von Systemen, über vordefinierte Schnittstellen effizient zusammenzuarbeiten.

### Portabilität

**Definition**:
Die Möglichkeit, eine Anwendung auf unterschiedlichen Plattformen auszuführen, ohne den Quellcode ändern zu müssen.

### Komponentendiagramm (UML)

**Definition**:
Zeigt modulare Einheiten (Komponenten) und deren Verbindungen. Komponenten sind unabhängig von konkreten Clients und stellen/benötigen Schnittstellen.

### Port (UML)

**Definition**:
Ein dedizierter Interaktionspunkt einer Komponente mit der Umgebung, definiert durch angebotene und benötigte Interfaces.

### Assembly Connector

**Definition**:
Verbindet die bereitgestellte Schnittstelle (Lollipop-Notation) einer Komponente mit der benötigten Schnittstelle (Socket-Notation) einer anderen Komponente.

### Delegation Connector

**Definition**:
Verbindet die externe Schnittstelle (Port) einer Komponente mit den internen Sub-Komponenten, die diese realisieren.

### Deployment-Diagramm (UML)

**Definition**:
Visualisiert die physische Verteilung von Softwareartefakten auf Laufzeitknoten (Hardware, VMs, Server) und deren Kommunikationswege.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welche der folgenden Aussagen beschreibt am präzisesten die ...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, architektur, systemgrenze`)


#### Aufgabenstellung:
Welche der folgenden Aussagen beschreibt am präzisesten die Bedeutung von Systemgrenzen in der Softwarearchitektur?

A) Systemgrenzen definieren ausschließlich die technische Schnittstelle zwischen Hardware und Software.
B) Systemgrenzen bestimmen, welche Komponenten, Funktionen und Daten zum System gehören und welche externen Systeme oder Akteure außerhalb stehen.
C) Systemgrenzen legen fest, welche externen Cloud-Services in das System integriert werden dürfen.
D) Systemgrenzen dienen primär der Dokumentation und haben keinen direkten Einfluss auf die Implementierung.


#### Musterlösung:
Richtige Antwort: B

Erklärung: Systemgrenzen legen fest, was Teil des Systems (Daten, Logik, Komponenten) ist und was außerhalb als externer Akteur (Mensch oder Fremdsystem) agiert. Dies ist kritisch für die Eingrenzung des Projekts und die Schnittstellengestaltung.


#### Typische Stolpersteine / Fehlerquellen:
Einengung der Grenzen auf reine Hardware-Schnittstellen (A) oder Missachtung des Einflusses auf die Systemgestaltung (D).


---

### Aufgabe 2: Welches der folgenden Ziele stellt KEIN primäres Entwurfspri...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, architektur, verteilte_systeme`)


#### Aufgabenstellung:
Welches der folgenden Ziele stellt KEIN primäres Entwurfsprinzip für offene verteilte Systeme dar?

A) Interoperabilität
B) Portabilität
C) Zentralisierung aller Daten und Logik in einem Monolithen
D) Erweiterbarkeit über offene Schnittstellen


#### Musterlösung:
Richtige Antwort: C

Erklärung: Verteilte Systeme streben nach Dezentralisierung und Modularität, um Skalierbarkeit und Fehlertoleranz zu gewährleisten. Monolithische Zentralisierung steht diesem Prinzip diametral entgegen.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung von Dezentralisierung mit Unordnung oder Missinterpretation von Interoperabilität.


---



# Kapitel 11: MVC-Architektur und das Observer-Muster

## 📖 Guidelines

### Das Problem
Wenn GUI-Elemente direkt auf der Geschäftslogik operieren oder Geschäftslogik-Klassen direkt GUI-Widgets manipulieren, bricht das Schichtenmodell zusammen. Die GUI wird unteilbar mit der Logik verschmolzen, was automatisiertes Testen und die Unterstützung mehrerer Benutzeroberflächen unmöglich macht.

### Die Lösung
Einsatz des Model-View-Controller (MVC) Musters zur Entkopplung von Daten/Wissen (Model), Präsentation (View) und Steuerung (Controller). Die lose Kopplung und asynchrone Benachrichtigung bei Änderungen wird über das Observer-Muster (Subject/Observer) realisiert.

## 🤖 KI-Anweisungen (AI Instructions)

- Kläre die Rollenverteilung in MVC: Der Controller enthält keine Businesslogik, das Model enthält Daten und Logik.
- Erkläre die Initialisierungsreihenfolge in MVC: 1. Model erzeugen, 2. Views erzeugen (registrieren sich beim Model als Observer und erzeugen ihren Controller), 3. Event-Schleife starten.
- Vermittle die Funktionsweise des Observer-Musters (attach, detach, notify, update) zur Entkopplung von Model und View (Push-from-below).


## 💡 Konzepte & Definitionen

### Model (MVC)

**Definition**:
Das Modell verwaltet die Anwendungsdaten und das domänenspezifische Wissen (Geschäftsregeln). Es ist kein Monolith, sondern besteht aus Domänenobjekten und Services.

### View (MVC)

**Definition**:
Visualisiert die Daten des Modells für den Benutzer und reagiert als Observer auf Änderungen des Modells.

### Controller (MVC)

**Definition**:
Empfängt Benutzereingaben von der View, interpretiert sie und stößt die entsprechenden Systemoperationen auf dem Modell an. Besitzt keine eigene Geschäftslogik.

### Observer-Pattern (Beobachter-Muster)

**Definition**:
Ein Verhaltensmuster, bei dem ein Subjekt (Subject) eine Liste von Beobachtern (Observer) verwaltet und diese bei Zustandsänderungen über eine einheitliche Schnittstelle (update) benachrichtigt.

### Push-from-below

**Definition**:
Ein Benachrichtigungsprinzip, bei dem die tiefere Schicht (Model) die höhere Schicht (View) über Änderungen benachrichtigt, ohne sie direkt zu kennen (durch Nutzung von Schnittstellen wie Observer).

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welche Komponente im MVC-Pattern übernimmt typischerweise di...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, mvc, observer`)


#### Aufgabenstellung:
Welche Komponente im MVC-Pattern übernimmt typischerweise die Rolle des Subjekts im Observer-Muster?

A) Die View
B) Der Controller
C) Das Model
D) Die Zustandsmaschine


#### Musterlösung:
Richtige Antwort: C

Erklärung: Das Model verwaltet die Daten und den Zustand der Anwendung. Es fungiert als Subjekt und bietet Schnittstellen wie attach(Observer), um Views und Controller über Zustandsänderungen zu informieren, damit sich diese synchronisieren.


#### Typische Stolpersteine / Fehlerquellen:
Falsche Zuweisung des Subjekts an den Controller (der Eingaben steuert, aber keine Daten verwaltet) oder an die View.


---

### Aufgabe 2: Welche Methode gehört typischerweise NICHT zu den Schnittste...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, observer, entwurfsmuster`)


#### Aufgabenstellung:
Welche Methode gehört typischerweise NICHT zu den Schnittstellenoperationen des Subjekts im Observer-Muster?

A) attach(Observer)
B) detach(Observer)
C) notify()
D) handleEvent()


#### Musterlösung:
Richtige Antwort: D

Erklärung: attach, detach und notify sind die typischen Operationen des Subjekts zur Verwaltung und Benachrichtigung von Beobachtern. handleEvent() ist eine Methode des Controllers zur Verarbeitung von Benutzeraktionen.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung des Controller-Verhaltens (Eingabe) mit dem Subjekt-Verhalten (Zustandsänderung).


---



# Kapitel 12: Protokoll-Automaten

## 📖 Guidelines

### Das Problem
Systeme geraten leicht in inkonsistente Zustände, wenn Systemoperationen in einer unzulässigen Reihenfolge aufgerufen werden (z. B. Daten bearbeiten ohne erfolgreichen Login). Wenn die Einhaltung dieser Reihenfolgen dezentral und implizit in der Logik verteilt ist, wird der Code unübersichtlich und fehleranfällig.

### Die Lösung
Explizite Definition und Überwachung der zulässigen Operationen über einen Protokoll-Automaten (Zustandsmaschine). Die Verwaltung des Systemzustands wird in einer zentralen Klasse (z. B. `StateMachineImpl` als Subject) gekapselt, während Systemoperationen über Vor- und Nachbedingungen abgesichert werden.

## 🤖 KI-Anweisungen (AI Instructions)

- Erkläre den Unterschied zwischen Protokoll-Automaten (erlaubte Sequenzen von Systemoperationen) und klassischen Zustandsdiagrammen (alle Zustände).
- Zeige auf, wie Zustände als Enums (z. B. in Interfaces) modelliert und über Facades überwacht werden (Vor- und Nachbedingungen abprüfen).
- Vermittle den Aufbau komplexer Zustände (Compound States, History-Zustände, Parallelität, Synchronisierung) und die vordefinierten internen Übergänge (entry, exit, do, completion).


## 💡 Konzepte & Definitionen

### Protokoll-Automat

**Definition**:
Eine spezielle Form von Zustandsmaschine, die festlegt, in welchen Zuständen welche Systemoperationen (Trigger) aufgerufen werden dürfen.

### Vorbedingung (Precondition)

**Definition**:
Die Menge der Zustände, in denen ein Aufruf einer Operation zulässig ist.

### Nachbedingung (Postcondition)

**Definition**:
Der Zielzustand (oder die Menge möglicher Zustände), der nach Abschluss der Operation eingenommen wird.

### Interner Übergang (UML)

**Definition**:
Ein Übergang innerhalb eines Zustands, der den Zustand nicht verlässt (kein exit/entry-Event auslöst). Vordefiniert: entry, exit, do (für langlebige Aktivitäten).

### History-Zustand (History State)

**Definition**:
Ein Pseudozustand in UML, der sich beim Verlassen eines zusammengesetzten Zustands den zuletzt aktiven Unterzustand merkt, um bei Rückkehr dorthin zu springen.

### Parallelität (Zustandsdiagramm)

**Definition**:
Die Aufteilung eines Zustands in orthogonale Regionen, die unabhängig voneinander Zustände wechseln.

### Synchronisierung (Zustandsdiagramm)

**Definition**:
Die Zusammenführung paralleler Pfade, wobei ein Folgezustand erst erreicht wird, wenn alle orthogonalen Regionen ihren Endzustand erreicht haben.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welche Aussage beschreibt korrekt die Rolle von Vor- und Nac...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, state_machine, protokoll_automat`)


#### Aufgabenstellung:
Welche Aussage beschreibt korrekt die Rolle von Vor- und Nachbedingungen in einem Protokoll-Automaten?

A) Vorbedingungen definieren die Zustände nach einer Operation, Nachbedingungen die Zustände davor.
B) Vorbedingungen spezifizieren die Menge der Zustände, in denen ein Aufruf einer Systemoperation zulässig ist, Nachbedingungen den Zustand nach Abschluss der Operation.
C) Beide Bedingungen sind optional und dienen nur der Entwickler-Dokumentation.
D) Vor- und Nachbedingungen legen ausschließlich die GUI-Aktivität fest.


#### Musterlösung:
Richtige Antwort: B

Erklärung: Vorbedingungen legen fest, wann ein API-Aufruf oder eine Systemoperation valide ist. Nachbedingungen sichern zu, in welchen Zustand das System nach der Ausführung übergeht.


#### Typische Stolpersteine / Fehlerquellen:
Vertauschen von Vor- und Nachbedingung oder Geringschätzung ihrer formalen Bedeutung für die Zustandskonsistenz.


---

### Aufgabe 2: Was gilt als 'Trigger' in einem Protokoll-Automaten?

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, state_machine, trigger`)


#### Aufgabenstellung:
Was gilt als 'Trigger' in einem Protokoll-Automaten?

A) Die Änderung eines Attributwerts in der Datenbank
B) Der Aufruf einer Systemoperation (z. B. login()), die im Protokoll definiert ist
C) Ein beliebiges asynchrones UI-Redraw-Event
D) Die Instanziierung einer Service-Klasse


#### Musterlösung:
Richtige Antwort: B

Erklärung: Im Protokoll-Automaten ist ein Trigger der Aufruf einer Systemoperation, der den Übergang von einem Protokollzustand in den nächsten auslösen kann.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung von allgemeinen Ereignissen (Events) mit den spezifischen Systemoperationsaufrufen (Triggern) des Protokolls.


---



# Kapitel 13: Interaktionsdiagramme und GRASP-Verantwortlichkeiten

## 📖 Guidelines

### Das Problem
Bei der Umsetzung von Systemoperationen ist unklar, wie die Verantwortung auf die Klassen verteilt werden soll. Schlechte Zuordnung führt zu hoher Kopplung (Classes kennen zu viele andere Classes), geringer Kohäsion (eine Riesen-Klasse macht alles) und schlechter Wartbarkeit.

### Die Lösung
Anwendung der GRASP-Prinzipien (General Responsibility Assignment Software Patterns) zur strukturierten Verantwortungszuweisung. Die dynamischen Abläufe werden mittels UML-Interaktionsdiagrammen (Sequenz- und Kommunikationsdiagrammen) modelliert, um den Nachrichtenfluss und die Objektlebenszeiten präzise zu planen.

## 🤖 KI-Anweisungen (AI Instructions)

- Erkläre die fünf grundlegenden GRASP-Muster: Information Expert, Creator, Low Coupling, High Cohesion und Controller/Management.
- Stelle sicher, dass der Benutzer den Unterschied zwischen Sequenzdiagrammen (zeitlicher Fokus, Lifelines, Gates, Fragmente) und Kommunikationsdiagrammen (räumlicher Fokus, Objektdiagramm-Basis) versteht.


## 💡 Konzepte & Definitionen

### GRASP

**Definition**:
General Responsibility Assignment Software Patterns. Ein Satz von Entwurfsprinzipien zur strukturierten Verteilung von Verantwortlichkeiten (Wissen und Tun) auf Klassen.

### Information Expert

**Definition**:
Das GRASP-Prinzip, das besagt, dass eine Verantwortung der Klasse zugewiesen wird, die über alle zur Erfüllung notwendigen Informationen verfügt.

### Creator (Erzeuger)

**Definition**:
Bestimmt, welche Klasse für die Instanziierung eines Objekts zuständig ist (z. B. wenn sie das Objekt besitzt, aggregiert oder die Initialisierungsdaten kennt).

### Low Coupling (Lose Kopplung)

**Definition**:
Ein Entwurfsziel, bei dem Abhängigkeiten zwischen Klassen minimiert werden, um Änderungen zu vereinfachen und Wiederverwendbarkeit zu erhöhen.

### High Cohesion (Hohe Kohäsion)

**Definition**:
Ein Entwurfsziel, bei dem die Verantwortlichkeiten einer Klasse eng fokussiert und thematisch einheitlich sind, um 'Gott-Objekte' zu vermeiden.

### Controller (GRASP)

**Definition**:
Das erste Objekt jenseits der UI-Schicht, das Systemoperationen empfängt und koordiniert (z. B. ein Use-Case-Controller).

### Sequenzdiagramm (UML)

**Definition**:
Ein Interaktionsdiagramm, das den zeitlichen Ablauf von Nachrichten zwischen Objekten entlang vertikaler Lebenslinien (Lifelines) und Aktivierungsbalken zeigt.

### Kommunikationsdiagramm (UML)

**Definition**:
Ein Interaktionsdiagramm, das den Schwerpunkt auf die Netzbeziehungen und die räumliche Anordnung der beteiligten Objekte legt.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welches der folgenden Elemente stellt KEIN primäres Ziel ein...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, uml, sequenzdiagramm`)


#### Aufgabenstellung:
Welches der folgenden Elemente stellt KEIN primäres Ziel eines UML-Sequenzdiagramms dar?

A) Darstellung des zeitlichen Ablaufs von Interaktionen zwischen Objekten
B) Visualisierung der Lebenszeit von Objekten während eines Use Cases
C) Abbildung der statischen Struktur des Systems (z. B. Assoziationen, Vererbung)
D) Identifikation der Verantwortlichkeiten für Operationen


#### Musterlösung:
Richtige Antwort: C

Erklärung: Sequenzdiagramme sind Verhaltensdiagramme, die den Nachrichtenaustausch im Zeitverlauf darstellen. Die statische Struktur (Assoziationen, Attribute, Klassenstruktur) wird im Klassendiagramm modelliert.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung von dynamischem Verhalten (Sequenzdiagramm) mit statischer Struktur (Klassendiagramm).


---

### Aufgabe 2: Welches GRASP-Prinzip wird angewendet, wenn ein Objekt eine ...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, grasp, information_expert`)


#### Aufgabenstellung:
Welches GRASP-Prinzip wird angewendet, wenn ein Objekt eine Berechnung an ein anderes Objekt übergibt, da dieses über alle dafür benötigten Attribute verfügt?

A) Creator
B) Information Expert
C) Controller
D) High Cohesion


#### Musterlösung:
Richtige Antwort: B

Erklärung: Der Information Expert besagt, dass die Verantwortung für ein Verhalten bei dem Objekt liegen sollte, das das dafür nötige Wissen (Informationen) besitzt.


#### Typische Stolpersteine / Fehlerquellen:
Falsche Zuweisung an Creator (der Objekte baut) oder Controller (der Systemevents routet).


---



# Kapitel 14: Patterns – Erzeugungsmuster

## 📖 Guidelines

### Das Problem
Wenn Client-Code konkrete Produktklassen über 'new' instanziiert, wird er starr an diese gebunden. Dies verhindert den einfachen Austausch von Implementierungen (z. B. plattformspezifische UI-Komponenten) und verletzt das Open/Closed-Prinzip.

### Die Lösung
Verstecken des Erzeugungsprozesses durch Erzeugungsmuster. Clients programmieren gegen Schnittstellen, und die Objekterzeugung wird an Fabrikmethoden (Unterklassen entscheiden) oder abstrakte Fabriken (erzeugen konsistente Produktfamilien) ausgelagert.

## 🤖 KI-Anweisungen (AI Instructions)

- Erkläre die Fabrikmethode (Factory Method): Schnittstelle zur Objekterzeugung, Delegierung an Unterklassen.
- Erkläre die Abstrakte Fabrik (Abstract Factory): Schnittstelle zur Erzeugung von Familien verwandter/abhängiger Objekte ohne Angabe konkreter Klassen.
- Stelle sicher, dass der Benutzer den Unterschied und die typischen Nachteile kennt (z. B. Abstrakte Fabrik erschwert das Hinzufügen neuer Produkttypen).


## 💡 Konzepte & Definitionen

### Fabrikmethode (Factory Method)

**Definition**:
Definiert eine Schnittstelle zur Erzeugung eines Objekts, lässt aber Unterklassen entscheiden, welche Klasse instanziiert wird. Delegiert die Erzeugung an Unterklassen.

### Abstrakte Fabrik (Abstract Factory)

**Definition**:
Bietet eine Schnittstelle zur Erzeugung von Familien zusammenhängender oder voneinander abhängiger Objekte, ohne deren konkrete Klassen zu benennen. Garantiert das korrekte Zusammenspiel der Produkte (Produktfamilien).

### Produktfamilie

**Definition**:
Eine Menge von Produktklassen (z. B. GermanAL, GermanTL, GermanBL), die aufeinander abgestimmt sind und gemeinsam verwendet werden müssen, um Inkonsistenzen zu vermeiden.

### Programmieren auf Schnittstellen

**Definition**:
Entwurfsprinzip, bei dem Clients nur die abstrakten Schnittstellen (Interfaces) kennen, wodurch konkrete Implementierungen zur Laufzeit austauschbar bleiben.

### Objektkomposition vs. Vererbung

**Definition**:
Die Bevorzugung von Komposition/Aggregation (Schnittstellennutzung zur Laufzeit) gegenüber Vererbung (Kopplung an Implementierung zur Compilezeit). Erhöht Flexibilität.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welches der folgenden Szenarien beschreibt einen typischen A...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, entwurfsmuster, abstract_factory`)


#### Aufgabenstellung:
Welches der folgenden Szenarien beschreibt einen typischen Anwendungsfall für die Abstrakte Fabrik (Abstract Factory)?

A) Ein Texteditor soll zur Laufzeit zwischen verschiedenen Betriebssystem-Stilen (Windows/macOS/Linux) wechseln können.
B) Ein Datenbank-Client soll automatisch zwischen MySQL und PostgreSQL umschalten, wenn eine Verbindung fehlschlägt.
C) Ein Spiel soll zufällig Gegner-Charaktere mit unterschiedlichen Fähigkeiten generieren.
D) Ein Compiler soll während der Kompilierung temporäre Dateien für die Zwischenspeicherung nutzen.


#### Musterlösung:
Richtige Antwort: A

Erklärung: Die Abstrakte Fabrik wird eingesetzt, wenn Familien verwandter Objekte (hier: plattformspezifische UI-Komponenten wie Button, TextField für ein bestimmtes OS) konsistent erzeugt werden müssen und der Client unabhängig von konkreten Implementierungen arbeiten soll.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung mit der einfachen Fabrikmethode (die einzelne Objekte erzeugt, nicht Familien) oder dem Strategie-Muster.


---

### Aufgabe 2: Welcher der folgenden Nachteile ist typisch für die Abstrakt...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, entwurfsmuster, abstract_factory`)


#### Aufgabenstellung:
Welcher der folgenden Nachteile ist typisch für die Abstrakte Fabrik, aber nicht für die einfache Fabrikmethode?

A) Erhöhte Komplexität durch zusätzliche Abstraktionsschichten.
B) Starke Kopplung zwischen Client und konkreten Produkten.
C) Unfähigkeit, neue Produkttypen zur Laufzeit hinzuzufügen.
D) Die Notwendigkeit, bei der Einführung neuer Produkttypen die Schnittstelle der abstrakten Fabrik und alle konkreten Fabrikunterklassen zu ändern.


#### Musterlösung:
Richtige Antwort: D

Erklärung: Da die Abstrakte Fabrik Schnittstellen für die Erzeugung einer festen Produktfamilie bereitstellt, muss bei Einführung eines neuen Produkts (z. B. VideoLabel) das Interface LabelFactory sowie jede konkrete Fabrikklasse (GermanLabelFactory, USLabelFactory) angepasst werden (Verletzung des Open/Closed-Prinzips).


#### Typische Stolpersteine / Fehlerquellen:
Vergessen, dass die Produktpalette bei einer Abstrakten Fabrik fest vorgegeben ist, während neue Familien leicht durch neue Fabriken ergänzt werden können.


---



# Kapitel 15: Patterns – Strukturmuster

## 📖 Guidelines

### Das Problem
Nachträglich integrierte Bibliotheken oder Altsysteme haben oft inkompatible Schnittstellen zur Client-Anwendung. Zudem führt die direkte Vererbung von Abstraktionen an plattform- oder darstellungsabhängige Implementierungen zu starren, tiefen Klassenhierarchien.

### Die Lösung
Einführung einer Indirektion durch Strukturmuster. Der Adapter übersetzt inkompatible Schnittstellen post-facto. Die Brücke (Bridge) trennt Abstraktion und Implementierung bereits im Entwurf (up-front), sodass beide unabhängig voneinander variieren können.

## 🤖 KI-Anweisungen (AI Instructions)

- Erkläre das Adapter-Muster (Adapter) in den Varianten Klassen-Adapter (Vererbung) und Objekt-Adapter (Komposition) sowie Zweiweg-Adapter.
- Erkläre das Brücke-Muster (Bridge) zur Entkopplung von Abstraktion und Implementierung.
- Stelle sicher, dass der Benutzer den Unterschied versteht: Adapter passt inkompatible Schnittstellen nachträglich an; Bridge entkoppelt diese von vornherein, um unabhängige Erweiterungen zu ermöglichen.


## 💡 Konzepte & Definitionen

### Adapter-Muster

**Definition**:
Passt die Schnittstelle einer Klasse an eine andere an, die von den Clients erwartet wird. Ermöglicht die Zusammenarbeit unabhängig entworfener Klassen mit inkompatiblen Schnittstellen.

### Klassen-Adapter

**Definition**:
Realisiert den Adapter über Vererbung (Mehrfachvererbung in C++, in Java über Vererbung der Adaptee-Klasse und Implementierung des Target-Interfaces). Kann Teile des Adaptees überschreiben.

### Objekt-Adapter

**Definition**:
Realisiert den Adapter über Objektkomposition. Er hält eine Referenz auf den Adaptee und delegiert Aufrufe. Funktioniert auch mit Unterklassen des Adaptees.


**Beispiel / Code**:
```python
public class Adapter implements Target {
    private Adaptee adaptee;
    public Adapter(Adaptee a) { this.adaptee = a; }
    public void targetOp() { this.adaptee.existingOp(); }
}
```

### Zweiweg-Adapter

**Definition**:
Implementiert sowohl die Ziel-Schnittstelle als auch die Schnittstelle des Adaptees, um Transparenz für Clients auf beiden Seiten zu bieten.

### Brücke-Muster (Bridge)

**Definition**:
Entkoppelt eine Abstraktion von ihrer Implementierung, sodass beide unabhängig voneinander variieren können. Verhindert permanente Bindungen zwischen beiden.

### Abstraktion vs. Implementierung (Bridge)

**Definition**:
Die Abstraktion definiert die Schnittstelle für den Client, während die Implementierungsoberklasse (Implementor) primitive Operationen bereitstellt, die von der Abstraktion genutzt werden.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Welcher der folgenden Punkte beschreibt einen wesentlichen k...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, entwurfsmuster, bridge, adapter`)


#### Aufgabenstellung:
Welcher der folgenden Punkte beschreibt einen wesentlichen konzeptionellen Unterschied zwischen dem Bridge-Muster und dem Adapter-Muster?

A) Der Adapter wird zur Laufzeit eingesetzt, die Bridge nur zur Compilezeit.
B) Der Adapter dient dem nachträglichen Auflösen von Schnittstelleninkompatibilitäten unabhängig entworfener Klassen (post-facto), während die Bridge von vornherein (up-front) entworfen wird, um Abstraktion und Implementierung unabhängig variieren zu lassen.
C) Die Bridge ändert die Schnittstelle einer Klasse, während der Adapter nur die Implementierung anpasst.
D) Das Adapter-Muster erfordert immer Mehrfachvererbung, während die Bridge dies verbietet.


#### Musterlösung:
Richtige Antwort: B

Erklärung: Dies ist der entscheidende Unterschied. Der Adapter ist ein Wrapper für inkompatiblen Code (oft Legacy-Code oder Drittbibliotheken). Die Bridge hingegen ist ein Entwurfsstrukturmuster, das up-front geplant wird, um Abstraktion und Implementierung getrennt weiterzuentwickeln.


#### Typische Stolpersteine / Fehlerquellen:
Beide Muster leiten Anfragen an ein anderes Objekt weiter und führen eine Indirektion ein, was oft zu Verwechslungen führt.


---

### Aufgabe 2: Ein Entwickler möchte eine neue Verschlüsselungs-API in ein ...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, entwurfsmuster, adapter`)


#### Aufgabenstellung:
Ein Entwickler möchte eine neue Verschlüsselungs-API in ein bestehendes System integrieren. Die neue API hat jedoch eine andere Schnittstelle als die vom System geforderte Schnittstelle 'Cipher'. Welches Muster sollte er verwenden?

A) Bridge, um Abstraktion und Implementierung zu trennen.
B) Adapter, da er die inkompatible Schnittstelle der API an das geforderte 'Cipher'-Interface anpasst.
C) Singleton, um nur eine API-Instanz zu erlauben.
D) Decorator, um das Verhalten der API zu erweitern.


#### Musterlösung:
Richtige Antwort: B

Erklärung: Das Adapter-Muster ist ideal, um bestehende Komponenten mit inkompatiblen Schnittstellen nutzbar zu machen. Der Adapter implementiert das System-Interface 'Cipher' und leitet die Aufrufe an die neue API weiter.


#### Typische Stolpersteine / Fehlerquellen:
Sich von der Bridge ablenken lassen, die für das bewusste Aufteilen eigener Klassen gedacht ist, nicht für das Verpacken fremder APIs.


---



# Kapitel 16: GUI-Anbindung und Persistenz

## 📖 Guidelines

### Das Problem
Benutzeroberflächen und Datenhaltungssysteme hängen stark vom Zustand der Anwendungslogik ab. Eine unkoordinierte GUI-Aktualisierung führt zu Inkonsistenzen, während unsynchronisierte, parallele Datenbankzugriffe Deadlocks und Datenverlust verursachen.

### Die Lösung
Steuerung der Benutzeroberfläche über eine zustandsabhängige ViewFactory (mkView(state)). Datenhaltung über einen Object-Relational Mapper (ORM/JPA), der Tabellen auf Klassen abbildet. Die Thread-Sicherheit bei DB-Zugriffen wird durch Beschränkung auf einen dedizierten Thread gewährleistet.

## 🤖 KI-Anweisungen (AI Instructions)

- Erkläre die Organisation der GUI anhand des Zustandsmodells (Default-Views pro Zustand, State-gesteuerte View-Erstellung).
- Vermittle die Grundlagen des Object-Relational Mapping (ORM/JPA) zur Kapselung der Persistenzschicht.
- Verdeutliche das Concurrency-Prinzip in Persistenz-Frameworks: Vermeidung paralleler Thread-Zugriffe auf die DB-Session, um Sperrkonflikte (Locks) zu vermeiden.


## 💡 Konzepte & Definitionen

### ViewFactory

**Definition**:
Ein Entwurfsmuster zur dynamischen Erzeugung und Zuordnung von GUI-Views basierend auf dem aktuellen Systemzustand des Protokoll-Automaten (z. B. mkView(state)).

### Object-Relational Mapping (ORM)

**Definition**:
Technik zur Abbildung einer relationalen Datenbank (Tabellen, Fremdschlüssel) auf ein objektorientiertes Klassensystem (Klassen, Assoziationen). Beispiele: JPA, Hibernate.

### Session-Kontext (Persistence Context)

**Definition**:
Der vom OR-Mapper verwaltete Kontext, der geladene Objekte im Speicher trackt und Änderungen automatisch mit der Datenbank synchronisiert.

### Thread-Sicherheit in OR-Mappern

**Definition**:
Die Anforderung, auf eine Datenbank-Session nicht aus unterschiedlichen Threads parallel zuzugreifen, um Locks, unvorhersehbare Transaktionszustände und Race Conditions zu verhindern.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Warum sollte beim Einsatz von OR-Mappern wie Hibernate der D...

- **Klausurrelevant**: Ja (Tags: `klausur_vorbereitung, persistenz, concurrency, orm`)


#### Aufgabenstellung:
Warum sollte beim Einsatz von OR-Mappern wie Hibernate der Datenbankzugriff nicht aus mehreren parallelen Threads auf derselben Session durchgeführt werden?

A) Weil relationale Datenbanken generell keine parallelen Anfragen unterstützen.
B) Um Probleme mit Datenbank-Locks und inkonsistenten Zuständen (Race Conditions) innerhalb des Session-Kontextes zu vermeiden.
C) Weil OR-Mapper keine Multi-Thread-Anwendungen erlauben.
D) Um den Arbeitsspeicher des Client-Rechners zu schonen.


#### Musterlösung:
Richtige Antwort: B

Erklärung: OR-Mapper verwalten geladene Objekte in einem Session-Kontext (First-Level Cache). Greifen mehrere Threads gleichzeitig auf diese Session zu, kommt es zu Race Conditions und Synchronisationskonflikten (Locks). Datenbankzugriffe müssen daher thread-safe koordiniert werden.


#### Typische Stolpersteine / Fehlerquellen:
Die falsche Annahme, dass relationale Datenbanken an sich keine Nebenläufigkeit unterstützen (das tun sie auf Server-Ebene, aber nicht die clientseitige ORM-Session).


---


