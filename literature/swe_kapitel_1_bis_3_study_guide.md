# Software-Engineering: Studienführer für die Kapitel 1 bis 3

Dieser Studienführer fasst die Kernkonzepte der Vorlesung Software-Engineering von Prof. Dr. Thomas Fuchß für die ersten drei Kapitel zusammen. Der Text ist so formuliert, dass er sich hervorragend für die Sprachgenerierung (z. B. NotebookLM Podcast) eignet, indem er theoretische Definitionen mit anschaulichen Erklärungen und Beispielen verbindet.

---

## Kapitel 1: Die Notwendigkeit eines Prozesses

### Was ist Software-Engineering?
Nach der Definition von Broy und Rombach zielt Software-Engineering auf die ingenieurmäßige Entwicklung, Wartung, Anpassung und Weiterentwicklung großer Software-Systeme hin. Das Wort „ingenieurmäßig“ ist hierbei entscheidend: Es bedeutet, dass wir nicht nach Bauchgefühl vorgehen, sondern wissenschaftlich fundierte, systematische Vorgehensweisen, Prinzipien, Methoden und Werkzeuge verwenden.

Große Software-Systeme unterscheiden sich fundamental von kleinen Programmen:
1. Sie haben viele unterschiedliche Benutzer.
2. Sie werden von großen Teams entwickelt, bei denen der einzelne Entwickler oft nur noch Teile des Gesamtsystems versteht.
3. Die Entwicklungskosten sind immens und die Lebenserwartung der Software ist meist deutlich höher als anfangs geschätzt.

Ohne einen klaren Prozess droht das Projekt zu scheitern. Typische Risiken sind mangelndes Problemverständnis (man baut das falsche Produkt), unterschätzte Komplexität (Zeit- und Budgetüberschreitungen) und ineffiziente Nutzung neuer Technologien.

### Das Problem von "Codieren und Verbessern" (Code and Fix)
Der naive Ansatz in der Softwareentwicklung lautet: „Das Problem löst man im Kopf, codiert wird mit links, und Probleme lösen wir, wenn sie auftreten.“ Dieser Ansatz führt fast immer ins Chaos:
* Nach vielen Iterationen ist der Code so unbrauchbar und unstrukturiert, dass jede Änderung extrem teuer wird. Ein sauberes Design vorab ist notwendig.
* Auch der genialste Code nützt nichts, wenn er am Ende ein Problem löst, das der Kunde gar nicht hat. Eine saubere Anforderungsanalyse (Requirement-Analyse) ist unerlässlich.

### Evolution der Prozessmodelle
Um diese Probleme zu beheben, wurden im Laufe der Zeit verschiedene Vorgehensmodelle entwickelt:

1. **Das Wasserfallmodell**:
   Das Projekt wird in starr aufeinanderfolgende Phasen unterteilt (z. B. Analyse, Design, Implementierung, Test, Betrieb). Jede Phase muss vollständig abgeschlossen sein, bevor die nächste beginnt. 
   * *Das Problem*: Es betrachtet die Aufgabe als starr und als Ganzes. Feedback ist nur im Fehlerfall vorgesehen. Oft führt es dazu, dass erst ganz am Ende des Projekts ein fehlerhaftes Produkt bemerkt wird.

2. **Das Prototypenmodell**:
   Hier wird frühzeitig ein anschaulicher Prototyp gebaut. Das reduziert das Risiko von Missverständnissen bei der Anforderungsanalyse mit dem Kunden. Die übrigen Risiken (z. B. schlechtes Design oder mangelhafte Tests des Gesamtsystems) bleiben jedoch bestehen.

3. **Das Spiralmodell (Barry Boehm, 1988)**:
   Das Spiralmodell führt das Risikomanagement als treibende Kraft ein. Jede Schleife der Spirale entspricht einer Phase, die in vier Schritten abläuft: 
   * Ziele und Alternativen bestimmen
   * Risiken evaluieren und beseitigen
   * Das Produkt entwickeln und verifizieren
   * Die nächste Phase planen.
   Schwierige Aufgaben mit hohem Risiko werden zuerst gelöst. Das Spiralmodell ist die theoretische Grundlage fast aller modernen, agilen Prozesse.

4. **Das Versionsmodell**:
   Hierbei wird das Wasserfallmodell iterativ angewendet. Jede Version ist ein lauffähiges Teilsystem, das auf der Vorgängerversion aufbaut. Der Vorteil: Neue Nutzeranforderungen können flexibel integriert werden, und der Auftraggeber sieht frühzeitig ein lauffähiges Kernsystem.

---

## Kapitel 2: Objektorientierung – eine durchgängige Sichtweise

### Die Säulen der Objektorientierung (OO)
Die Objektorientierung basiert auf fünf zentralen Säulen:
1. **Natürliche Modellierung**: Objekte im Code spiegeln reale oder abstrakte Dinge der echten Welt (Personen, Konten, Prozesse) wider.
2. **Sharing**: Objekte können gemeinsame Eigenschaften und Verhaltensweisen teilen.
3. **Abstrakte Datentypen (Kapselung)**: Der interne Zustand eines Objekts ist verborgen. Der Zugriff erfolgt ausschließlich über eine wohldefinierte Schnittstelle.
4. **Nachempfinden (Vererbung)**: Klassen können von anderen Klassen erben.
5. **Templates (Generics)**: Schablonen zur Erstellung flexibler Datenstrukturen.

### Operationen vs. Methoden
In der objektorientierten Modellierung unterscheidet man strikt zwischen der Beschreibung und der Ausführung:
* Eine **Operation** ist eine Begrifflichkeit aus der Modellierungsebene. Sie beschreibt abstrakt, *was* getan werden soll (eine Dienstleistung ohne konkreten Code).
* Eine **Methode** ist die konkrete Implementierung im Quellcode. Sie bestimmt, *wie* die Operation ausgeführt wird.

### Grundprinzipien des OO-Entwurfs
Der objektorientierte Entwurf zeichnet sich durch drei Eigenschaften aus:
* **Ganzheitlichkeit**: Daten und Funktionen werden gemeinsam in Klassen beschrieben.
* **Intuitivität**: Das Problem wird durch das Modellieren und Simulieren von Objekten gelöst.
* **Methodische Durchgängigkeit**: Die Analyseergebnisse aus dem Problemraum lassen sich direkt in den Lösungsraum (die Implementierung) übertragen.

---

## Kapitel 3: Vererbung und UML-Semantik

### Das Vererbungsprinzip und Substitutionsprinzip
Vererbung bedeutet, dass Klassen hierarchisch angeordnet werden können. Unterklassen sind Spezialisierungen ihrer Oberklasse. 
* **Vererbungsprinzip**: Die Unterklasse übernimmt alle Attribute, Operationen und Beziehungen der Oberklasse. Sie kann diese erweitern oder überschreiben, aber **niemals eliminieren**.
* **Substitutionsprinzip (Liskovsches Substitutionsprinzip)**: Objekte einer Unterklasse müssen sich überall dort einsetzen lassen, wo Objekte der Oberklasse erwartet werden, ohne dass das System fehlerhaft reagiert.

### Das klassische Rechteck-Quadrat-Dilemma
Ein berühmtes Problem verdeutlicht die Tücken falscher Vererbung:
* *Idee 1: Quadrat erbt von Rechteck*. 
  Ein Rechteck hat die Attribute Breite `a` und Höhe `b`. Ein Quadrat hat die Bedingung, dass `a` und `b` immer gleich sein müssen (`{a = b}`). Wenn wir nun auf einem Quadrat-Objekt die geerbte Operation `stretch(width, height)` mit unterschiedlichen Werten aufrufen, verletzen wir die Invariante des Quadrats. Das Substitutionsprinzip ist verletzt!
* *Idee 2: Rechteck erbt von Quadrat*.
  Ein Quadrat besitzt nur eine Seitenlänge `a`. Ein Rechteck kann aber unterschiedliche Seitenlängen haben. Wenn wir ein Rechteck-Objekt einer Variablen vom Typ Quadrat zuweisen, bricht das Substitutionsprinzip ebenfalls zusammen, da ein allgemeines Rechteck kein Quadrat ist.
* *Die Lösung*: In der Praxis verzichtet man hier oft auf Vererbung. Stattdessen nutzt man eine einzige Klasse `Rechteck` mit einer Hilfsmethode `istQuadrat(): boolean`.

### UML-Generalisierungs-Semantiken
In der Unified Modeling Language (UML) kann die Vererbung durch vier semantische Paare genauer charakterisiert werden:

1. **disjoint (disjunkt)**:
   Eine Instanz der Oberklasse kann höchstens Mitglied einer der Unterklassen sein. Es gibt keine Schnittmenge. (Beispiel: Ein Fahrzeug ist entweder ein PKW oder ein LKW, aber nicht beides gleichzeitig).
2. **overlapping (überlappend)**:
   Es gibt Instanzen, die sich in der Schnittmenge befinden. Eine Instanz kann gleichzeitig mehreren Unterklassen angehören.
3. **complete (vollständig)**:
   Die Menge der Unterklassen deckt alle möglichen Spezialisierungen ab. Es gibt keine weiteren, nicht modellierten Unterklassen.
4. **incomplete (unvollständig)**:
   Es gibt weitere Unterklassen, die im Modell (noch) nicht aufgeführt sind.
