# KI-Regelwerk für Verteilte-Systeme-2-Verarbeitung

> Systemregeln und Kontextvorgaben für KI-Assistenten basierend auf Prof. Dr. Christian Zirpins: Verteilte Systeme 2.

**Version**: 1.0.0


---

## ⚙️ Allgemeine Regeln

- **never_do_more_than_requested:** Tue niemals mehr als verlangt. Halte die Antworten präzise, direkt und beschränke dich strikt auf die angeforderte Aufgabe.


---

# Kapitel 1: Einführung

## 📖 Guidelines

### Das Problem
Verteilte Systeme bestehen aus autonomen, heterogenen Rechenelementen (Knoten) ohne gemeinsame physikalische Uhr. Dies führt zu fundamentalen Herausforderungen bei der Koordination, da keine globale Reihenfolge von Ereignissen existiert, partielle Ausfälle unvermeidbar sind und die Skalierung bezüglich der Anzahl der Nutzer (größenmäßig), der maximalen Distanz (geografisch) und der Anzahl administrativer Domänen (administrativ) oft durch Latenzen oder organisatorische Grenzen blockiert wird.

### Die Lösung
Durch Middleware als verteilte Systemschicht wird Verteilungstransparenz (Zugriff, Ort, Relokation, Migration, Replikation, Nebenläufigkeit, Ausfall) angestrebt. Skalierungsprobleme werden durch Techniken wie Latenzverbergen (Asynchronität), Verlagerung von Berechnungen zum Client (z. B. Formularprüfung), Partitionierung (z. B. DNS) und Replikation/Caching gelöst, wobei bei der Replikation ein Trade-off zwischen globaler Konsistenz und Performance besteht. Sensornetze werden mittels zyklischer Inaktivität (Arbeitszyklen) energieeffizient betrieben, wobei die Koordination über einen clusterbasierten Synchronisationsalgorithmus (Join-Nachrichten, Cluster-IDs) erfolgt.

## 🤖 KI-Anweisungen (AI Instructions)

- Leite den Benutzer an, die Dimensionen der Skalierung (größenmäßig, geografisch, administrativ) sowie die entsprechenden Skalierungstechniken (Verbergen von Latenzen, Partitionierung, Replikation) korrekt zu identifizieren und auf Fallbeispiele anzuwenden.
- Erzwinge die Verwendung der exakten Formel für den Arbeitszyklus (Duty Cycle) \tau = T_active / (T_active + T_suspended) bei allen Berechnungen zum Energieverbrauch in Sensornetzwerken.
- Stelle sicher, dass der Benutzer den clusterbasierten Synchronisationsalgorithmus für Sensornetze mit Arbeitszyklen verstanden hat, insbesondere die Regeln zum Senden und Empfangen von JOIN-Nachrichten basierend auf dem Vergleich von Cluster-IDs (C_A < C_B bzw. C_A > C_B).
- Weise darauf hin, dass absolute Verteilungstransparenz ein theoretisches Ideal ist und in der Praxis aufgrund unüberwindbarer physikalischer Grenzen (z. B. Netzwerklatenz, Ununterscheidbarkeit von langsamen und ausgefallenen Knoten) oft bewusst durchbrochen werden muss (z. B. bei standortbezogenen Diensten).


## 💡 Konzepte & Definitionen

### Verteiltes System

**Definition**:
Eine Sammlung autonomer Rechenelemente (Knoten), die ihren Nutzern wie ein einzelnes kohärentes System erscheint. Knoten agieren unabhängig, besitzen keinen gemeinsamen Speicher und keine globale Uhr.

### Overlay-Netzwerk

**Definition**:
Ein logisches Netzwerk, das oberhalb eines bestehenden physikalischen Netzwerks aufgebaut ist. Knoten kommunizieren direkt nur mit ihren Nachbarn. Man unterscheidet strukturierte Overlays (definierte Nachbarschaftsbeziehungen, z. B. Ringe wie Chord) und unstrukturierte Overlays (zufällig gewählte Nachbarn, z. B. durch Random Walks).

### Middleware

**Definition**:
Eine Softwareplattform zur einfacheren Realisierung verteilter Systeme, die sich als zusätzliche Schicht oberhalb der lokalen Betriebssysteme und unterhalb der Anwendungen befindet. Sie stellt standardisierte Schnittstellen und Dienste zur Verfügung, um die Verteilungstransparenz zu erhöhen.

### Verteilungstransparenz

**Definition**:
Das Verbergen der physischen Verteilung von Ressourcen vor dem Benutzer oder der Anwendung. Die wichtigsten Typen sind: Zugriffstransparenz (Datenrepräsentation/Aufrufe), Ortstransparenz (Speicherort), Relokationstransparenz (Bewegung während der Nutzung), Migrationstransparenz (Ortswechsel), Replikationstransparenz (Mehrfachkopien), Nebenläufigkeitstransparenz (gemeinsame Nutzung) und Ausfalltransparenz (Fehler/Wiederherstellung).

### Skalierungsdimensionen

**Definition**:
Kriterien zur Bewertung der Skalierbarkeit eines Systems. Größenmäßige Skalierbarkeit (Nutzer-/Prozessanzahl), geografische Skalierbarkeit (maximale Distanz zwischen Knoten) und administrative Skalierbarkeit (Anzahl unabhängiger administrativer Domänen).

### Skalierungstechniken

**Definition**:
Methoden zur Überwindung von Skalierungsgrenzen. Dazu gehören: Verbergen von Kommunikationslatenzen (asynchrone Kommunikation), Verlagerung von Berechnungen auf den Client (z. B. Formularprüfung im Browser), Partitionierung/Aufteilung von Daten und Berechnungen (z. B. DNS-Hierarchie) und Replikation/Caching zur Steigerung der Datenverfügbarkeit.

### Arbeitszyklus (Duty Cycle)

**Definition**:
Das Verhältnis der aktiven Phase eines Knotens zur Gesamtzeit eines Zyklus, genutzt zur Energieeinsparung in Sensornetzwerken. Formel: \tau = T_active / (T_active + T_suspended).

### Cluster-basierte Synchronisierung (Sensornetze)

**Definition**:
Algorithmus zur Synchronisation von Arbeitszyklen disjunkter Sensoren zur Vermeidung dauerhafter Trennung. Jeder Knoten wählt eine zufällige Cluster-ID C. Knoten senden während der inaktiven Phase JOIN-Nachrichten. Empfängt A ein JOIN von B: Wenn C_A < C_B, leitet A die Nachricht an sein Cluster weiter und tritt C_B bei (Zeitanpassung an B). Wenn C_A > C_B, sendet A während B's aktiver Phase eine JOIN-Nachricht an B.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Analysieren Sie die folgenden drei Anwendungsfälle bezüglich...

- **Klausurrelevant**: Ja (Tags: `uebung, analyse, skalierung`)


#### Aufgabenstellung:
Analysieren Sie die folgenden drei Anwendungsfälle bezüglich der Dimension der Skalierung (größenmäßig, geografisch, administrativ) und der eingesetzten Skalierungstechnik (verbergen, partitionieren, replizieren):

1. Kreditkartentransaktionen: Da bei großer Nachfrage Wartezeiten auftreten können, erfolgt die Zahlungsbestätigung nicht unmittelbar auf der Oberfläche, sondern verzögert per E-Mail.
2. Software-as-a-Service: Ein deutscher SaaS-Anbieter mietet VMs in den USA an und erstellt exakte Kopien seines Anwendungsservers und der Datenbank, um Latenzen für US-Nutzer zu verbessern.
3. Web-Marktplatz: Jeder Händler erhält einen exklusiven Server mit eigener Produktdatenbank zur Unterstützung individueller Sicherheitsregeln der beteiligten Unternehmen.


#### Musterlösung:
1. Kreditkartentransaktionen:
   - Dimension: größenmäßig (Ziel: Bewältigung hoher Nutzerlast/Nachfrage)
   - Technik: verbergen (Latenzverbergen durch asynchrone E-Mail-Zustellung)
2. Software-as-a-Service:
   - Dimension: geografisch (Ziel: Überwindung physischer Distanzen / Latenzen für US-Nutzer)
   - Technik: replizieren (Kopieren von Anwendungsserver und Datenbank)
3. Web-Marktplatz:
   - Dimension: administrativ (Ziel: Integration unabhängiger Unternehmen und deren Sicherheitsregeln)
   - Technik: partitionieren (Aufteilung auf händlerspezifische Server und Produktdatenbanken)


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung zwischen Replikation (Kopieren desselben Inhalts) und Partitionierung (Aufteilen unterschiedlicher Inhalte). Falsche Zuordnung der administrativen Skalierung bei reinen Infrastruktur-SaaS-Projekten (hier geht es um Richtlinien/Sicherheitsgrenzen verschiedener Unternehmen, also administrativ).


---

### Aufgabe 2: Wir betrachten ein Szenario mit drei Sensoren S_A, S_B, S_C....

- **Klausurrelevant**: Ja (Tags: `klausur_wise_2023_2024, sensornetze, berechnung`)


#### Aufgabenstellung:
Wir betrachten ein Szenario mit drei Sensoren S_A, S_B, S_C. Deren Arbeitszyklus ist identisch mit T_active = 10 s und T_suspended = 30 s konfiguriert.

(a) Geben Sie die Formel des Arbeitszyklus \tau an und berechnen Sie den Wert.
(b) Angenommen, der clusterbasierte Synchronisationsalgorithmus startet ab Sekunde 40. Die Initiative geht von S_C (C_C = 9) aus, der eine JOIN-Nachricht an S_B (C_B = 7) sendet. In welchem Zeitintervall muss S_C die JOIN-Nachricht gesendet haben, damit S_B sie empfängt?
(c) Wie reagiert S_B auf die Nachricht von S_C? Beschreiben Sie die Regel und die zwei resultierenden Aktivitäten. S_A hat ebenfalls die Cluster-ID 7 (C_A = 7).
(d) Welche Cluster-ID hat das durch den Algorithmus vereinigte Cluster am Ende?
(e) Auf welchen Startzeitpunkt der aktiven Phase einigen sich die Sensoren, wenn S_C als Referenz dient und seine aktiven Phasen bei Sekunde 30-40, 70-80, 110-120 usw. liegen?


#### Musterlösung:
(a) Formel: \tau = T_active / (T_active + T_suspended). Berechnung: \tau = 10 s / (10 s + 30 s) = 0.25 (bzw. 25%).
(b) S_C muss die JOIN-Nachricht während der aktiven Phase von S_B gesendet haben. Da S_B zwischen Sekunde 40 und 50 aktiv ist, ist das Zeitintervall [40 s, 50 s].
(c) Da C_C = 9 > C_B = 7 (Regel: Empfangene ID ist größer als eigene ID), tritt S_B dem Cluster von S_C bei. Die zwei Aktivitäten sind:
   1. Aktivität 1: S_B leitet die JOIN-Nachricht an S_A weiter, um sein bisheriges Cluster über die Änderung zu informieren.
   2. Aktivität 2: S_B passt seine Uhr bzw. seinen Arbeitszyklus an S_C an (Zeitanpassung).
(d) Das vereinigte Cluster hat die ID 9.
(e) Die Sensoren einigen sich auf den Arbeitszyklus von S_C. Die aktiven Phasen starten daher bei Sekunde 70, 110, 150 usw.


#### Typische Stolpersteine / Fehlerquellen:
Vergessen, die Einheiten anzugeben. Bei (b) muss darauf geachtet werden, dass die Nachricht den Empfänger in dessen aktiver Phase (T_active) erreicht. Bei (c) müssen Regel und beide Aktivitäten (Weiterleiten an Nachbarn, Zeitanpassung) explizit genannt werden.




---

# Kapitel 2: Architekturen

## 📖 Guidelines

### Das Problem
Der Entwurf verteilter Systeme erfordert das Mapping logischer Softwarekomponenten auf physische Knoten, wobei Kommunikationsaufwand, Kopplung (temporal/referenziell), Systemleistung und Skalierbarkeit ausbalanciert werden müssen. Starre Legacy-Schnittstellen, quadratische Wrapper-Komplexität O(N^2) bei der Integration vieler Systeme sowie hoher Lookup-Overhead in dezentralen Netzen erschweren die Architektur.

### Die Lösung
Durch den Einsatz standardisierter Architekturstile (geschichtet, REST, SOA, ereignisbasiert, Linda-Tupelraum) können Kopplungen gezielt gelöst werden. Wrapper und Broker reduzieren Integrationskomplexitäten von O(N^2) auf O(N), Interzeptoren passen Middleware-Verhalten flexibel an, und strukturierte P2P-Systeme (wie Chord-DHTs mittels Finger-Tabellen) ermöglichen eine logarithmisch skalierende Suche nach Schlüsseln.

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer die Dimensionen temporaler und referenzieller Kopplung (direkt, Mailbox, ereignisbasiert, geteilter Datenraum) korrekt unterscheiden und tabellarisch einordnen kann.
- Leite den Benutzer an, die Komplexität von Wrappern bei N Systemen im 1-zu-1-Modell (O(N^2)) im Vergleich zum Broker-Modell (O(N)) mathematisch herzuleiten.
- Erzwinge das korrekte Berechnungsverfahren für Chord-Finger-Tabellen unter Verwendung der Formel successor((n + 2^(i-1)) mod 2^m) und das entsprechende Routing im Ring.
- Weise auf den Unterschied zwischen zustandslosen (z. B. REST) und zustandsbehafteten Servern und den Trade-off zwischen Fehlertoleranz und Session-Handling hin.


## 💡 Konzepte & Definitionen

### Architekturstil

**Definition**:
Generelle Gestaltungsprinzipien für Systemstrukturen, die durch Komponenten (modulare Einheiten), Konnektoren (Kommunikations-/Koordinationsmechanismen), ausgetauschte Daten und deren Konfiguration bestimmt werden.

### Kopplung (Koordination)

**Definition**:
Klassifizierung der Interaktion in zwei Dimensionen: 1. Referenzielle Kopplung (müssen Kommunikationspartner sich namentlich kennen? Gekoppelt = direkt adressiert vs. Entkoppelt = anonym über Vermittler). 2. Temporale Kopplung (müssen Sender und Empfänger gleichzeitig aktiv sein? Gekoppelt = blockierend/synchron vs. Entkoppelt = asynchron/Mailbox).

### REST (Representational State Transfer)

**Definition**:
Ressourcenbasierter Architekturstil auf Basis einheitlicher Schnittstellen und zustandsloser Kommunikation. Jede Ressource ist über eine eindeutige URI adressierbar. Operationen basieren auf Standard-Methoden (HTTP POST/Create, GET/Read, PUT/Update, DELETE/Delete). Nachrichten sind selbstbeschreibend.

**Beispiel-Code**:
```java
PUT http://mybucket.s3.amazonaws.com/myobject.txt
```

### Linda Tupelraum (Shared Space)

**Definition**:
Ein referenziell und temporal entkoppeltes Koordinationsmodell auf Basis eines gemeinsamen, persistenten Datenraums (Multimenge). Operationen sind out(t) (Tupel schreiben), in(t) (Tupel lesen und entfernen; blockierend falls kein Treffer), und rd(t) (Tupel-Kopie lesen; blockierend).

**Beispiel-Code**:
```java
# Bob schreibt in den Tupelraum:
blog._out(("bob", "distsys", "I am studying chap 2"))
# Chuck liest blockierend mit Template:
t1 = blog._rd(("bob", "distsys", str))
```

### Wrapper / Broker

**Definition**:
Entwurfsmuster zur Integration von Altsystemen (Legacy). Ein Wrapper/Adapter übersetzt Client-Aufrufe in die Legacy-Schnittstelle. Um quadratische Komplexität bei N Systemen zu vermeiden (O(N^2) für 1-zu-1 Wrapper), vermittelt ein Broker die Aufrufe, was die Komplexität auf O(N) reduziert (2N Wrapper).

### Interzeptor

**Definition**:
Komponente zur transparenten Anpassung des Kontrollflusses in Middleware. Request-Level Interzeptoren fangen Aufrufe auf Anwendungsebene ab (z. B. vor der Serialisierung). Message-Level Interzeptoren fangen die fertig serialisierte Nachricht auf Netzwerk-/Betriebssystemebene ab.

### Mehrschichtige Client-Server-Architektur

**Definition**:
Aufteilung eines Systems in Präsentationsebene (GUI, Eingabe), Verarbeitungsebene (Geschäftslogik, Algorithmen) und Datenebene (Datenbanken). Physisch unterscheidet man 2-Tier (Fat Client: GUI+Logik auf Client, DB auf Server; Thin Client: GUI auf Client, Logik+DB auf Server) und 3-Tier (jede Ebene auf eigener Maschine).

### Chord (Verteilte Hash-Tabelle)

**Definition**:
Ein strukturiertes P2P-System, bei dem Knoten und Schlüssel in einem m-Bit Ring angeordnet sind. Ein Schlüssel k wird auf dem Successor (erster Knoten mit ID >= k) gespeichert. Logarithmisches Routing wird durch Finger-Tabellen realisiert, bei denen der i-te Eintrag auf successor((n + 2^(i-1)) mod 2^m) verweist.

**Beispiel-Code**:
```java
# Finger-Tabelle für Knoten 6 in 4-Bit Ring (m=4, 16 Positionen):
# i=1: successor((6 + 1) mod 16) = successor(7) -> 9
# i=2: successor((6 + 2) mod 16) = successor(8) -> 9
# i=3: successor((6 + 4) mod 16) = successor(10) -> 12
# i=4: successor((6 + 8) mod 16) = successor(14) -> 14
```

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Die Telefonauskunft umfasst folgende Komponenten: (1) Benutz...

- **Klausurrelevant**: Ja (Tags: `uebung, architektur, schichten`)


#### Aufgabenstellung:
Die Telefonauskunft umfasst folgende Komponenten: (1) Benutzerschnittstelle, (2) Abfragegenerator, (3) Telefondatenbank und (4) Rangfolgenalgorithmus.

(a) Nennen und beschreiben Sie kurz die drei Anwendungsebenen betrieblicher Informationssysteme.
(b) Ordnen Sie die Komponenten (1)-(4) diesen drei Ebenen zu.
(c) Das System soll auf vier Geräte verteilt werden: R1 (Smartphone), R2 (Workstation), R3 (Webserver) und R4 (Datenbankserver). Beschreiben Sie die Verteilung der Komponenten für:
  - V1: Zwei-Schicht-Architektur mit Fat Client
  - V2: Drei-Schicht-Architektur mit Thin Client


#### Musterlösung:
(a) Die drei Anwendungsebenen:
  1. Präsentationsebene (User Interface Layer): Verantwortlich für die Darstellung der Benutzeroberfläche und Benutzerinteraktionen.
  2. Anwendungsebene / Verarbeitungsebene (Application Layer): Beinhaltet die eigentliche Geschäftslogik der Anwendung.
  3. Datenebene (Data Layer): Verantwortlich für die Speicherung und Bereitstellung von Daten.
(b) Zuordnung:
  - Benutzerschnittstelle (1) -> Präsentationsebene
  - Abfragegenerator (2) -> Anwendungsebene
  - Telefondatenbank (3) -> Datenebene
  - Rangfolgenalgorithmus (4) -> Anwendungsebene
(c) Verteilung auf die Geräte R1-R4:
  - V1 (Zwei-Schicht mit Fat Client):
    * Client (R2 Workstation): Beinhaltet Benutzerschnittstelle (1), Abfragegenerator (2) und Rangfolgenalgorithmus (4) (die gesamte Präsentation und Logik läuft lokal auf dem 'Fat' Client).
    * Server (R4 Datenbankserver): Beinhaltet die Telefondatenbank (3).
    * R1 (Smartphone) und R3 (Webserver) werden nicht verwendet.
  - V2 (Drei-Schicht mit Thin Client):
    * Client (R1 Smartphone): Beinhaltet die Benutzerschnittstelle (1) (der Client ist 'Thin', da er nur Präsentationsaufgaben übernimmt).
    * Anwendungsserver (R3 Webserver): Beinhaltet den Abfragegenerator (2) und Rangfolgenalgorithmus (4).
    * Datenbankserver (R4 Datenbankserver): Beinhaltet die Telefondatenbank (3).
    * R2 (Workstation) wird nicht verwendet.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung zwischen Fat Client (Logik auf Client) und Thin Client (Logik auf Server). Häufige Fehlannahme, dass bei V1 ein Smartphone (R1) als Fat Client genutzt werden kann; Smartphones sind in dieser Vorlesung typischerweise als Thin Clients (V2) eingeplant, da R2 (Workstation) mehr Rechenleistung hat.


---

### Aufgabe 2: In einem Chord-basierten Peer-to-Peer-System mit einem 4-Bit...

- **Klausurrelevant**: Ja (Tags: `klausur_wise_2023_2024, chord, routing, berechnung`)


#### Aufgabenstellung:
In einem Chord-basierten Peer-to-Peer-System mit einem 4-Bit-Adressraum (m=4, Wertebereich 0-15) existieren die vier Knoten 6, 9, 12 und 14.

(a) Berechnen Sie die vollständigen Finger-Tabellen für alle vier Knoten.
(b) Skizzieren Sie den Ablauf der Suche nach Schlüssel 13, ausgehend von Knoten 6 (Notation: 13@06). Welche Knoten werden nacheinander besucht?
(c) Skizzieren Sie den Ablauf der Suche nach Schlüssel 8, ausgehend von Knoten 12 (Notation: 08@12). Welche Knoten werden nacheinander besucht?


#### Musterlösung:
(a) Die Finger-Tabelle für Knoten n berechnet sich über successor((n + 2^(i-1)) mod 16) für i=1, 2, 3, 4:

- Knoten 6:
  * i=1: successor(7) -> 9
  * i=2: successor(8) -> 9
  * i=3: successor(10) -> 12
  * i=4: successor(14) -> 14
  => FT_6 = [9, 9, 12, 14]

- Knoten 9:
  * i=1: successor(10) -> 12
  * i=2: successor(11) -> 12
  * i=3: successor(13) -> 14
  * i=4: successor(1) -> 6
  => FT_9 = [12, 12, 14, 6]

- Knoten 12:
  * i=1: successor(13) -> 14
  * i=2: successor(14) -> 14
  * i=3: successor(0) -> 6
  * i=4: successor(4) -> 6
  => FT_12 = [14, 14, 6, 6]

- Knoten 14:
  * i=1: successor(15) -> 6
  * i=2: successor(0) -> 6
  * i=3: successor(2) -> 6
  * i=4: successor(6) -> 6
  => FT_14 = [6, 6, 6, 6]

(b) Routing für 13@06:
  1. Knoten 6 sucht in seiner FT den größten Knoten, der kleiner als der Zielschlüssel 13 ist. Dies ist Knoten 12.
  2. Knoten 6 leitet die Anfrage an Knoten 12 weiter.
  3. Knoten 12 stellt fest, dass sein Nachfolger (successor) Knoten 14 ist, welcher >= 13 ist. 14 ist somit der Zielknoten für Schlüssel 13.
  => Besuchte Knoten: 12, 14.

(c) Routing für 08@12:
  1. Knoten 12 sucht in seiner FT den größten Knoten, der (modulo 16) vor dem Schlüssel 8 liegt. Auf dem Ring von 12 bis 8 liegen die FT-Einträge 14 und 6. Der größte davon ist 6.
  2. Knoten 12 leitet die Anfrage an Knoten 6 weiter.
  3. Knoten 6 stellt fest, dass der Zielschlüssel 8 zwischen ihm (6) und seinem Nachfolger (9) liegt. Der Nachfolger von 8 ist somit 9.
  4. Knoten 6 leitet die Anfrage an Knoten 9 weiter (wo der Schlüssel 8 gespeichert ist).
  => Besuchte Knoten: 6, 9.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung des Modulo-Betriebs bei der Ring-Richtung. Bei (c) ist zu beachten, dass auf dem Ring ab 12 die Reihenfolge 12 -> 13 -> 14 -> 15 -> 0 -> ... -> 6 -> 7 -> 8 ist. 6 ist somit näher an 8 als 14 und wird daher gewählt. Vergessen, dass der Zielknoten selbst der Successor des Schlüssels ist.




---

# Kapitel 3: Prozesse

## 📖 Guidelines

### Das Problem
Zur Maximierung von Nebenläufigkeit und Performance in verteilten Systemen müssen Prozesse und Threads effizient verwaltet werden. Ein reines Prozess-Modell verursacht durch ständige Umschaltungen zwischen User- und Kernelmodus hohe Latenzen, während reine User-Space-Threads bei blockierendem E/A den gesamten Prozess lahmlegen. Hinzu kommen Herausforderungen bei der Virtualisierung (Schnittstellennachahmung) und Code-Migration, da Ausführungskontexte stark hardwareabhängig sind.

### Die Lösung
Durch Multithreading können Blockierungen vermieden und Netzwerklatenzen verborgen werden. Im Serverbereich steuert ein Dispatcher-Thread die Verteilung an Worker-Threads (Dispatcher/Worker-Modell). Virtual Machine Monitors (Hypervisoren Typ 1 und Typ 2) sowie Prozess-VMs (wie die JVM) kapseln und isolieren Umgebungen. Code-Migration erfolgt nach Modellen wie Code-on-Demand (CoD) oder Remote Evaluation (REV) mittels schwacher (nur Code/Daten) oder starker Mobilität (inkl. Ausführungszustand/Stack).

## 🤖 KI-Anweisungen (AI Instructions)

- Leite den Benutzer an, den Durchsatz von Singlethread- und Multithread-Servern bei gegebenen CPU-Zeiten, Festplatten-Wartezeiten und Cache-Hitraten korrekt zu berechnen.
- Stelle sicher, dass der Benutzer die drei Ebenen von Ausführungskontexten (Prozessor-, Thread- und Prozesskontext) klar abgrenzen kann.
- Erzwinge die korrekte Einteilung von Virtualisierungsarten (Prozess-VM, nativer Hypervisor Typ 1, hosted Hypervisor Typ 2).
- Weise auf den Unterschied zwischen starker und schwacher Mobilität hin und stelle sicher, dass der Benutzer die Migrationsmodelle (CS, REV, CoD, MA) kennt.


## 💡 Konzepte & Definitionen

### Thread-Kontext vs. Prozess-Kontext

**Definition**:
Der Thread-Kontext enthält die minimalen Register- und Speicherwerte für eine Ausführungseinheit (Stack Pointer, Programmzähler, Zustand) innerhalb desselben Adressraums. Der Prozess-Kontext umfasst zusätzlich den gesamten Adressraum und die MMU-Register. Thread-Kontextwechsel sind wesentlich günstiger, da kein Adressraumwechsel stattfindet.

### User-Space- vs. Kernel-Space-Threads

**Definition**:
User-Space-Threads werden komplett in einer Bibliothek ohne BS-Hilfe verwaltet (sehr schnell, blockiert aber bei E/A den ganzen Prozess). Kernel-Space-Threads werden vom OS verwaltet (jede Operation erfordert Systemaufruf, aber blockierende E/A blockiert nur den einzelnen Thread).

### Dispatcher/Worker-Modell

**Definition**:
Server-Thread-Modell zur strukturellen Organisation. Ein Dispatcher-Thread liest eingehende Anfragen aus dem Netzwerk und übergibt sie zur parallelen Abarbeitung an einen freien Worker-Thread aus einem Thread-Pool.

### Hypervisor Typ 1 vs. Typ 2

**Definition**:
Hypervisor Typ 1 (Nativ/Bare-metal) läuft direkt auf der physischen Hardware (z. B. VMware ESXi). Hypervisor Typ 2 (Hosted) läuft als Anwendung auf einem normalen Host-Betriebssystem (z. B. VirtualBox). Prozess-VMs (z. B. JVM) emulieren eine Laufzeitumgebung für einzelne Programme.

### Code-Migration (Modelle)

**Definition**:
Strategien zum Verschieben von Programmcode in verteilten Systemen. Client-Server (CS): Code verbleibt auf Server. Remote Evaluation (REV): Client sendet Code an Server, Server führt aus und liefert Ergebnis. Code-on-Demand (CoD): Client lädt Code von Server und führt ihn lokal aus. Mobile Agents (MA): Autonomer Prozess wandert samt Code und Zustand von Host zu Host.

### Starke vs. Schwache Mobilität

**Definition**:
Schwache Mobilität: Nur Code- und Datensegment werden migriert, das Programm startet am Zielort neu (z. B. Java-Applets). Starke Mobilität: Der gesamte Ausführungszustand (inkl. Stack und Programmzähler) wird übertragen, das Programm fährt exakt an der Unterbrechungsstelle fort.

### TCP-Handoff

**Definition**:
Technik in Server-Clustern zur Vermeidung von CPU-Engpässen am Switch. Der Switch leitet den Request per Hand-off an einen Server weiter, welcher die Response direkt an den Client sendet, unter Beibehaltung der logischen TCP-Verbindung.

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Ein Dateiserver liest Dateien. Das Verarbeiten eines Request...

- **Klausurrelevant**: Ja (Tags: `uebung, berechnung, durchsatz`)


#### Aufgabenstellung:
Ein Dateiserver liest Dateien. Das Verarbeiten eines Requests im Cache dauert 5 ms. In 1/3 der Fälle muss eine Festplattenoperation durchgeführt werden (60 ms zusätzliche Wartezeit, in der der Thread blockiert).

(a) Berechnen Sie den Durchsatz (Anfragen/Sekunde) eines Singlethread-Servers.
(b) Berechnen Sie den Durchsatz (Anfragen/Sekunde) eines Multithread-Servers.


#### Musterlösung:
(a) Mittlere Bearbeitungszeit für Singlethread:
  T_single = T_cache + 1/3 * T_disk = 5 ms + 1/3 * 60 ms = 5 ms + 20 ms = 25 ms.
  Durchsatz = 1000 ms / 25 ms = 40 requests/s.

(b) Für den Multithread-Server entfallen die blockierenden Wartezeiten der CPU, da andere Threads währenddessen eingeplant werden. Der limitierende Faktor ist die CPU-Verarbeitungszeit von 5 ms.
  Durchsatz = 1000 ms / 5 ms = 200 requests/s.


#### Typische Stolpersteine / Fehlerquellen:
Vergessen, die I/O-Wartezeit beim Multithread-Server zu streichen. Falsche Addition der Wartezeit beim Multithread-Server. Vergessen der Angabe der Einheit (requests/s oder Anfragen/Sekunde).


---

### Aufgabe 2: Ein Dateiserver benötigt im Mittel 20 ms, um einen Request a...

- **Klausurrelevant**: Ja (Tags: `klausur_wise_2023_2024, berechnung, durchsatz`)


#### Aufgabenstellung:
Ein Dateiserver benötigt im Mittel 20 ms, um einen Request anzunehmen, zuzuweisen und die restliche CPU-Verarbeitung durchzuführen, wenn die Daten im Cache liegen. Die Cache-Hitrate beträgt 80% (80% aller Anfragen beziehen sich auf Cache-Daten). In den restlichen 20% ist ein blockierender Festplattenaufruf nötig, der 150 ms zusätzliche Wartezeit verursacht, in der der Thread blockiert.

(a) Berechnen Sie die mittlere Bearbeitungszeit und den Durchsatz (Anfragen/Sekunde) für einen Singlethread-Server.
(b) Berechnen Sie den Durchsatz (Anfragen/Sekunde) für einen Multithread-Server und vergleichen Sie die Durchsätze.


#### Musterlösung:
(a) Mittlere Bearbeitungszeit für Singlethread:
  T_single = 0.8 * 20 ms + 0.2 * (20 ms + 150 ms) = 16 ms + 0.2 * 170 ms = 16 ms + 34 ms = 50 ms.
  Durchsatz = 1000 ms / 50 ms = 20 requests/s.

(b) Mittlere CPU-Zeit (Limit für Multithread-Server):
  Da bei Festplattenzugriffen andere Threads gerechnet werden, entfallen die 150 ms Wartezeit. Die reine CPU-Verarbeitung pro Request beträgt konstant 20 ms.
  Durchsatz = 1000 ms / 20 ms = 50 requests/s.

Vergleich: Der Multithread-Server (50 req/s) hat einen um das 2,5-fache höheren Durchsatz als der Singlethread-Server (20 req/s).


#### Typische Stolpersteine / Fehlerquellen:
Beim Singlethread-Server muss die Gesamtzeit für einen Cache-Miss 170 ms betragen (20 ms CPU + 150 ms Disk). Ein häufiger Fehler ist das Rechnen von T_single = 0.8 * 20 + 0.2 * 150 = 46 ms. Für den Multithread-Server wird die Wartezeit komplett abgezogen, da sie asynchron verborgen wird.




---

# Kapitel 4: Kommunikation

## 📖 Guidelines

### Das Problem
Verteilte Prozesse müssen plattformübergreifend kommunizieren, doch systemnahe Sockets sind fehleranfällig und koppeln Systeme zu eng. Prozedurale Abstraktionen (RPC) verbergen Netzwerkdetails, stoßen aber bei heterogenen Datenformaten (z. B. Byte-Reihenfolge) und starren Aufrufsemantiken (Copy-in/Copy-out) an die Grenzen der Zugriffstransparenz. Zudem erfordern asynchrone Systeme (MOM) und Gruppenkommunikation (ALM) komplexe Routing- und Effizienzoptimierungen.

### Die Lösung
Middleware-Protokolle kapseln Serialisierung und Kommunikation. RPC-Stubs automatisieren das Verpacken (Marshaling) von Parametern, während asynchrone RPCs Blockierungen verhindern. Sockets-Bibliotheken wie ZeroMQ bieten höherwertige Kommunikationsmuster (REQ-REP, PUB-SUB, Pipeline) und asynchronen Nachrichtenaustausch. Bei persistentem Messaging (MOM) vermitteln Message Broker zwischen Datenformaten, und im Overlay-basierten Multicasting (ALM) optimiert man Pfadlatenzen (Stretch) und redundanten Paketfluss (Link Stress).

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer die 10 Schritte des klassischen synchronen RPC-Ablaufs in der exakten Reihenfolge (Client-Prozedur -> Client-Stub -> Client-BS -> Server-BS -> Server-Stub -> Server-Prozedur -> zurück) benennen kann.
- Leite den Benutzer an, die Copy-in/Copy-out Semantik (Call-by-Value-Result) bei RPCs mit der lokalen Referenzübergabe (Call-by-Reference) zu vergleichen und die Lücke in der Zugriffstransparenz anhand von Beispielen wie `incr(i,i)` zu erklären.
- Erzwinge das korrekte Berechnungsverfahren für Multicast-Effizienzmetriken: Link Stress (Anzahl Paketkopien pro physischem Link) und Stretch (Verhältnis der Overlay-Gesamtlatenz zur optimalen physischen Route).
- Stelle sicher, dass der Benutzer die ZeroMQ-Muster (Request-Reply, Publish-Subscribe, Pipeline) und ihre typische Implementierung in Python kennt.


## 💡 Konzepte & Definitionen

### Transiente vs. Persistente Kommunikation

**Definition**:
Transient: Eine Nachricht wird verworfen, wenn sie nicht direkt an den Empfänger oder den nächsten Hop zugestellt werden kann (z. B. TCP/UDP). Persistent: Eine Nachricht wird in der Middleware (z. B. in Queues) so lange gespeichert, bis der Empfänger sie abholt, unabhängig davon, ob Sender/Empfänger gleichzeitig aktiv sind.

### Synchrone vs. Asynchrone Kommunikation

**Definition**:
Klassifikation nach Synchronisationspunkten: 1. Synchron bei Anfrageübermittlung (Sender blockiert, bis Nachricht übertragen). 2. Synchron bei Auslieferung (Sender blockiert, bis Empfänger Nachricht erhält). 3. Synchron nach Verarbeitung (Sender blockiert bis Antwort/Ergebnis eintrifft, z. B. Standard-RPC). Asynchron: Sender läuft sofort nach dem Absenden weiter.

### RPC-Ablauf (10 Schritte)

**Definition**:
Sequenz eines synchronen RPC-Aufrufs: 1. Client-Prozedur ruft Client-Stub auf. 2. Stub verpackt Parameter (Marshaling) und ruft Client-BS auf. 3. Client-BS sendet Nachricht an Server-BS. 4. Server-BS übergibt Nachricht an Server-Stub. 5. Server-Stub entpackt Parameter (Unmarshaling) und ruft Server-Prozedur auf. 6. Server-Prozedur arbeitet und gibt Ergebnis an Server-Stub zurück. 7. Server-Stub verpackt Ergebnis und ruft Server-BS auf. 8. Server-BS sendet Nachricht an Client-BS. 9. Client-BS übergibt Nachricht an Client-Stub. 10. Client-Stub entpackt Ergebnis und gibt es an Client-Prozedur zurück.

### Copy-in/Copy-out Semantik

**Definition**:
Auch 'Call-by-Value-Result'. RPC-Parameterübergabe, bei der Argumente beim Aufruf kopiert (Copy-in) und bei Rückkehr zurückkopiert (Copy-out) werden. Da keine echten Speicherreferenzen übertragen werden können, weicht das Verhalten bei Aliasing-Aufrufen wie incr(i,i) von lokaler Referenzübergabe ab, was die Zugriffstransparenz einschränkt.

**Beispiel-Code**:
```java
# incr(i,i) mit i=0 anfangs:
# Lokal (Referenz): i wird zweimal inkrementiert -> i = 2
# RPC (Copy-in/Copy-out): i wird kopiert (0, 0), lokal inkrementiert (1, 1), bei Rückgabe wird i nacheinander mit 1 überschrieben -> i = 1
```

### Berkeley Sockets API

**Definition**:
Systemnahe Abstraktionsebene für transiente Kommunikation. Server nutzt socket(), bind(), listen() und blockiert in accept() für Verbindungen. Client nutzt socket() und connect(). Datenaustausch erfolgt über send() und recv().

**Beispiel-Code**:
```java
# Server-Socket (Python):
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.bind(('localhost', 8080))
s.listen(1)
conn, addr = s.accept()
data = conn.recv(1024)
conn.send(data + b'*')
conn.close()
```

### ZeroMQ

**Definition**:
Bibliothek für asynchrones, nachrichtenorientiertes Transient Messaging. Kapselt systemnahe Sockets und bietet integrierte Muster wie Request-Reply (REQ/REP), Publish-Subscribe (PUB/SUB mit filterbasiertem Empfang) und Pipeline (PUSH/PULL für Lastverteilung).

**Beispiel-Code**:
```java
# Request-Reply Client (Python):
import zmq
ctx = zmq.Context()
s = ctx.socket(zmq.REQ)
s.connect('tcp://localhost:5555')
s.send(b'Hello')
msg = s.recv()
print(msg)
```

### Message Oriented Middleware (MOM)

**Definition**:
Middleware für asynchrone, persistente Kommunikation. Queue Manager verwalten Warteschlangen (Queues). Sender platzieren Nachrichten in lokalen Queues, von wo sie über unidirektionale Channels mittels Message Channel Agents (MCA) geroutet werden. Message Broker dienen zur Übersetzung heterogener Nachrichtenformate.

### Link Stress

**Definition**:
Metrik für die Effizienz von Multicast-Kommunikation. Gibt an, wie viele Kopien derselben Nachricht über einen spezifischen physischen Netzwerklink gesendet werden müssen. Ziel von Application-Level Multicast (ALM) ist ein Link Stress von 1 auf allen physischen Links.

### Stretch (Pfadlatenz-Verhältnis)

**Definition**:
Verhältnis der Gesamtlatenz/Kosten einer Kommunikation über das Overlay-Netzwerk zu den Kosten über den optimalen physischen Routing-Weg im darunterliegenden IP-Netzwerk: Stretch = Kosten(Overlay) / Kosten(Physisch).

**Beispiel-Code**:
```java
# Beispiel aus SS25:
# Kosten über Overlay A->B->C->D = 10 + 16 + 14 = 40
# Bester physischer Weg A->Ra->Rb->Rd->D = 1 + 8 + 10 + 1 = 20
# Stretch = 40 / 20 = 2.0
```

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Betrachten Sie eine Prozedur incr mit zwei ganzzahligen Para...

- **Klausurrelevant**: Ja (Tags: `uebung, rpc, semantik`)


#### Aufgabenstellung:
Betrachten Sie eine Prozedur incr mit zwei ganzzahligen Parametern. Die Prozedur addiert eins zu jedem Parameter. Nehmen Sie nun an, dass incr zweimal mit derselben Variable i aufgerufen wird, also incr(i,i). Sei i anfänglich mit dem Wert 0 initialisiert.

(a) Welchen Wert hat i nach dem Aufruf, wenn i als lokale Referenz übergeben wird?
(b) Welchen Wert hat i nach dem Aufruf, wenn der Aufruf als RPC erfolgt und die Parameterübergabe mit Copy-in/Copy-out Semantik (Call-by-Value-Result) realisiert ist? Begründen Sie.


#### Musterlösung:
(a) Bei lokaler Referenzübergabe verweisen beide Parameter der Prozedur auf denselben Speicherplatz von i. Der erste Inkrement-Schritt erhöht i auf 1, der zweite Schritt erhöht denselben Speicherplatz auf 2. Nach dem Aufruf hat i den Wert 2.

(b) Bei Copy-in/Copy-out werden die Werte der Argumente beim Aufruf in lokale Kopien der Prozedur geladen (Copy-in: param1 = 0, param2 = 0). Die Prozedur inkrementiert beide lokalen Variablen unabhängig voneinander (param1 = 1, param2 = 1). Bei der Rückkehr (Copy-out) werden die lokalen Werte nacheinander in die Originalvariable i zurückkopiert. Da beide lokalen Variablen den Wert 1 haben, wird i unabhängig von der Reihenfolge mit dem Wert 1 überschrieben. Nach dem Aufruf hat i den Wert 1.


#### Typische Stolpersteine / Fehlerquellen:
Fehlende Begründung der Kopiermechanik bei (b). Vergessen, dass bei (a) derselbe Speicherbereich modifiziert wird.


---

### Aufgabe 2: Tragen Sie für einen klassischen, synchronen RPC-Ablauf die ...

- **Klausurrelevant**: Ja (Tags: `klausur_wise_2023_2024, rpc, ablauf`)


#### Aufgabenstellung:
Tragen Sie für einen klassischen, synchronen RPC-Ablauf die Nummern 1 bis 10 ein, um die Schritte in die korrekte zeitliche Reihenfolge zu bringen:

- ( ) Die Server-Prozedur verrichtet die Arbeit und gibt das Ergebnis zurück zum Server-Stub.
- ( ) Das Client-Betriebssystem übergibt die Nachricht an den Client-Stub.
- ( ) Das Client-Betriebssystem sendet die Nachricht an das Server-Betriebssystem.
- ( ) Der Client-Stub erstellt eine Nachricht und ruft das Client-Betriebssystem auf.
- ( ) Der Server-Stub übergibt das Ergebnis als Nachricht an das Server-Betriebssystem.
- ( ) Der Server-Stub entpackt die Parameter und ruft die Server-Prozedur auf.
- ( ) Das Server-Betriebssystem sendet die Nachricht an das Client-Betriebssystem.
- ( ) Das Server-Betriebssystem übergibt die Nachricht an den Server-Stub.
- ( ) Der Client-Stub entpackt das Ergebnis und gibt es an die Client-Prozedur zurück.
- ( ) Die Client-Prozedur ruft den Client-Stub auf übliche Weise auf.


#### Musterlösung:
Die korrekte Reihenfolge (1 bis 10) lautet:
- ( 6 ) Die Server-Prozedur verrichtet die Arbeit und gibt das Ergebnis zurück zum Server-Stub.
- ( 9 ) Das Client-Betriebssystem übergibt die Nachricht an den Client-Stub.
- ( 3 ) Das Client-Betriebssystem sendet die Nachricht an das Server-Betriebssystem.
- ( 2 ) Der Client-Stub erstellt eine Nachricht und ruft das Client-Betriebssystem auf.
- ( 7 ) Der Server-Stub übergibt das Ergebnis als Nachricht an das Server-Betriebssystem.
- ( 5 ) Der Server-Stub entpackt die Parameter und ruft die Server-Prozedur auf.
- ( 8 ) Das Server-Betriebssystem sendet die Nachricht an das Client-Betriebssystem.
- ( 4 ) Das Server-Betriebssystem übergibt die Nachricht an den Server-Stub.
- ( 10) Der Client-Stub entpackt das Ergebnis und gibt es an die Client-Prozedur zurück.
- ( 1 ) Die Client-Prozedur ruft den Client-Stub auf übliche Weise auf.


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung der Richtungen beim Senden/Empfangen zwischen Betriebssystem und Stub. Falsche Reihenfolge der Schritte 4 (Server-BS an Server-Stub) und 5 (Server-Stub ruft Server-Prozedur auf).


---

### Aufgabe 3: Gegeben ist ein Overlay-basiertes Multicast-Netzwerk (Applic...

- **Klausurrelevant**: Ja (Tags: `klausur_sose_2025, multicast, link_stress, stretch, berechnung`)


#### Aufgabenstellung:
Gegeben ist ein Overlay-basiertes Multicast-Netzwerk (Application-Level Multicast, ALM) mit Hosts H = {A, B, C, D} und Routern R = {Ra, Rb, Rc, Rd}. Die Overlay-Verbindungen sind O = {(A, B), (B, C), (C, D)}, so dass eine Nachricht von A nach D über A -> B -> C -> D geleitet wird.
Die physischen Latenzkosten sind:
- V = {(A, Ra): 1, (B, Rb): 1, (C, Rc): 1, (D, Rd): 1}
- W = {(Ra, Rb): 8, (Rb, Rc): 14, (Rc, Rd): 12, (Rb, Rd): 10}

(a) Bestimmen Sie für die Übertragung A -> D alle physischen Links (Verbindungen) mit einem Link Stress > 1.
(b) Berechnen Sie den Stretch für die Übertragung A -> D im gegebenen Overlay-Netzwerk.


#### Musterlösung:
(a) Zuerst ermitteln wir die physischen Wege für jede Overlay-Verbindung:
- A -> B verläuft physisch über: A -> Ra -> Rb -> B.
- B -> C verläuft physisch über: B -> Rb -> Rc -> C.
- C -> D verläuft physisch über: C -> Rc -> Rd -> D.

Nun zählen wir die Vorkommen jedes physischen Links:
- Link {A, Ra}: 1-mal
- Link {Ra, Rb}: 1-mal
- Link {Rb, B}: 2-mal (hin zu B für A->B, und zurück von B für B->C)
- Link {Rb, Rc}: 1-mal
- Link {Rc, C}: 2-mal (hin zu C für B->C, und zurück von C für C->D)
- Link {Rc, Rd}: 1-mal
- Link {Rd, D}: 1-mal

Die physischen Links mit Link Stress > 1 sind somit:
- {B, Rb} mit Stress 2
- {C, Rc} mit Stress 2

(b) Berechnung des Stretch:
- Gesamtlatenzkosten über das Overlay:
  Kosten(Overlay) = Kosten(A -> B) + Kosten(B -> C) + Kosten(C -> D)
  Kosten(Overlay) = (1 + 8 + 1) + (1 + 14 + 1) + (1 + 12 + 1) = 10 + 16 + 14 = 40

- Kosten über die optimale physische Route von A nach D (über Ra -> Rb -> Rd):
  Kosten(Physisch) = e(A, Ra) + e(Ra, Rb) + e(Rb, Rd) + e(Rd, D) = 1 + 8 + 10 + 1 = 20

- Stretch s(A, D) = Kosten(Overlay) / Kosten(Physisch) = 40 / 20 = 2.0.


#### Typische Stolpersteine / Fehlerquellen:
Vergessen, den Rückweg vom Host zum Router bei der Bestimmung des physischen Weges einzubeziehen (z. B. Rb -> B und direkt danach B -> Rb führt zu Stress 2 auf {B, Rb}). Falsche Latenzberechnung bei der optimalen physischen Route (Verwendung einer suboptimalen Route über Rc).




---

# Kapitel 5: Benennung

## 📖 Guidelines

### Das Problem
Namen müssen in verteilten Systemen verlässlich in Adressen aufgelöst werden. Bewegliche Entitäten (z. B. mobile Geräte) erfordern eine flache Benennung, bei der Suchen skaliert werden müssen (Broadcasting-Overhead, Heimatstandort-Last oder DHT-Routing). Bei strukturierten (hierarchischen) Namen wie im DNS entstehen Skalierungsprobleme bei der globalen Verteilung und Latenzprobleme bei geografisch entfernten Nameservern, die durch Replikation und Caching gelöst werden müssen. Attributbasierte Suchen erfordern komplexe Verzeichnisabgleiche.

### Die Lösung
Einsatz von drei grundlegenden Benennungsansätzen: 1. Flache Benennung: Auflösung über Broadcasting (ARP), Heimatstandorte (Mobile IP Tunneling) oder strukturierte P2P-Systeme (Chord DHT). 2. Strukturierte Benennung: Hierarchische Namensräume mit harten/weichen (symbolischen) Links und iterativer/rekursiver DNS-Auflösung mit Caching. 3. Attributbasierte Benennung: Verzeichnisdienste wie LDAP, die Objekte über Attribut-Wert-Paare in einem hierarchischen Directory Information Tree (DIT) organisieren und suchbar machen.

## 🤖 KI-Anweisungen (AI Instructions)

- Stelle sicher, dass der Benutzer den Unterschied zwischen Namen, eindeutigen Bezeichnern (Identifiers) und technischen Zugriffspunkten (Adressen) präzise erklären kann.
- Leite den Benutzer an, die Funktionsweise von Chord DHT (insb. Berechnung von Finger-Tabellen: FT_p[i] = succ(p + 2^(i-1)) und den Routing-Pfad für Schlüsselanfragen) mathematisch korrekt durchzuführen.
- Erzwinge die korrekte Unterscheidung und den Nachrichtenfluss von iterativer und rekursiver DNS-Namensauflösung.
- Erkläre dem Benutzer die DNS-Eintragstypen (A, MX, NS, CNAME, PTR, SOA, SRV) und wie symbolische Links (CNAME) im Benennungsgraphen abgebildet werden.


## 💡 Konzepte & Definitionen

### Namen, Bezeichner und Adressen

**Definition**:
Namen verweisen auf Entitäten. Zugriffspunkte von Entitäten werden durch Adressen identifiziert. Ein ortsunabhängiger Name ist unabhängig von der Adresse. Ein Bezeichner (Identifier) ist ein eindeutiger Name, der: 1. auf höchstens eine Entität verweist, 2. niemals für andere Entitäten wiederverwendet wird und 3. bei dem jede Entität höchstens einen Bezeichner hat.

### Flat Naming: Heimatbasierter Ansatz

**Definition**:
Mechanismus zur Lokalisierung mobiler Entitäten (z. B. Mobile IP). Eine Entität besitzt eine feste Heimatadresse an einem Heimatstandort (Home Agent). Zieht die Entität um, registriert sie ihre aktuelle auswärtige Adresse (Care-of-Address) beim Home Agent. Clients senden Pakete an den Home Agent, welcher diese an den aktuellen Standort tunnelt. Geografisch oft suboptimal.

### Chord Finger-Tabellen

**Definition**:
Um lineare Namen in einem Chord P2P-Ring effizient in O(log N) Schritten nachzuschlagen, hält jeder Knoten p eine Finger-Tabelle FT_p mit maximal m Einträgen: FT_p[i] = successor((p + 2^(i-1)) mod 2^m). Der Successor ist der kleinste Knoten-ID >= dem berechneten Wert.

**Beispiel-Code**:
```java
# i-ter Eintrag für Knoten p bei m-Bit Bezeichner:
# FT_p[i] = successor((p + 2**(i-1)) % (2**m))
```

### Harte vs. Weiche (Symbolische) Links

**Definition**:
Harter Link: Direkte Kante im Benennungsgraphen, die auf den Knoten der Entität verweist. Weicher (Symbolischer) Link: Ein spezieller Verzeichniseintrag (Blattknoten), der den Pfadnamen eines anderen Knotens als String enthält. Bei der Auflösung wird der Pfad ausgelesen und die Suche mit diesem Pfad neu gestartet.

### Iterative vs. Rekursive DNS-Namensauflösung

**Definition**:
Iterativ: Der Client-Resolver sendet eine Anfrage an den Nameserver. Dieser antwortet mit der Adresse des nächsten zuständigen Nameservers (Referral/Delegation). Der Client stellt die Anfrage dann selbst an den nächsten Server. Rekursiv: Der angefragte Nameserver übernimmt die komplette Auflösung, fragt nachgelagerte Server selbstständig ab, wartet auf die Antwort und liefert dem Client das finale Ergebnis. Rekursives Routing profitiert stark von Caching.

### DNS Record Types

**Definition**:
Typen von Ressourceneinträgen im DNS: SOA (Start of Authority - Zonen-Metadaten), A (Host-IPv4-Adresse), MX (Mail Exchange Server), SRV (Service-Location), NS (Autoritativer Nameserver für eine Zone), CNAME (Canonical Name - symbolischer Link), PTR (Pointer für Reverse-DNS).

### LDAP (Lightweight Directory Access Protocol)

**Definition**:
Hierarchischer Verzeichnisdienst für attributbasierte Benennung. Einträge bestehen aus Attribut-Wert-Paaren (z. B. C=NL, O=VU, OU=CS, CN=Main server). Sie werden im Directory Information Tree (DIT) angeordnet. Einträge werden durch ihren Distinguished Name (DN) eindeutig identifiziert, der sich aus Relative Distinguished Names (RDN) zusammensetzt.

**Beispiel-Code**:
```java
# LDAP Search Filter Beispiel:
# search('(&(C=NL)(O=VU University)(CN=Main server))')
```

---

## 📝 Übungsaufgaben & Klausurfragen

### Aufgabe 1: Gegeben ist ein Chord-System auf einem P2P-Ring mit m = 5 Bi...

- **Klausurrelevant**: Ja (Tags: `uebung, chord, finger_tabelle, routing, berechnung`)


#### Aufgabenstellung:
Gegeben ist ein Chord-System auf einem P2P-Ring mit m = 5 Bit (Wertebereich 0 bis 31). Das System umfasst die Knoten 3, 7, 13, 15 und 18.

(a) Bestimmen Sie die Finger-Tabellen für alle fünf Knoten.
(b) Lösen Sie die Suche nach dem Schlüssel 17 ausgehend von Knoten 3 (17@3) auf. Geben Sie den Weiterleitungspfad an.


#### Musterlösung:
(a) Die Finger-Tabellen werden nach der Formel FT_p[i] = successor((p + 2^(i-1)) mod 32) berechnet. Der Successor eines Werts k ist der kleinste Knoten mit ID >= k (bzw. nach Wrap-around ab 0):

- Knoten 3:
  FT_3[1] = succ(3 + 1) = succ(4) = 7
  FT_3[2] = succ(3 + 2) = succ(5) = 7
  FT_3[3] = succ(3 + 4) = succ(7) = 7
  FT_3[4] = succ(3 + 8) = succ(11) = 13
  FT_3[5] = succ(3 + 16) = succ(19) = 3 (Wrap-around, da kein Knoten >= 19 existiert)

- Knoten 7:
  FT_7[1] = succ(7 + 1) = succ(8) = 13
  FT_7[2] = succ(7 + 2) = succ(9) = 13
  FT_7[3] = succ(7 + 4) = succ(11) = 13
  FT_7[4] = succ(7 + 8) = succ(15) = 15
  FT_7[5] = succ(7 + 16) = succ(23) = 3

- Knoten 13:
  FT_13[1] = succ(13 + 1) = succ(14) = 15
  FT_13[2] = succ(13 + 2) = succ(15) = 15
  FT_13[3] = succ(13 + 4) = succ(17) = 18
  FT_13[4] = succ(13 + 8) = succ(21) = 3
  FT_13[5] = succ(13 + 16) = succ(29) = 3

- Knoten 15:
  FT_15[1] = succ(15 + 1) = succ(16) = 18
  FT_15[2] = succ(15 + 2) = succ(17) = 18
  FT_15[3] = succ(15 + 4) = succ(19) = 3
  FT_15[4] = succ(15 + 8) = succ(23) = 3
  FT_15[5] = succ(15 + 16) = succ(31) = 3

- Knoten 18:
  FT_18[1] = succ(18 + 1) = succ(19) = 3
  FT_18[2] = succ(18 + 2) = succ(20) = 3
  FT_18[3] = succ(18 + 4) = succ(22) = 3
  FT_18[4] = succ(18 + 8) = succ(26) = 3
  FT_18[5] = succ(18 + 16) = succ(2) = 3

(b) Weiterleitungspfad für 17@3:
1. Start bei Knoten 3: Der gesuchte Schlüssel ist 17. Der größte Knoten in FT_3, der < 17 ist, ist 13 (Eintrag FT_3[4]). Knoten 3 leitet die Anfrage an Knoten 13 weiter.
2. Weiterleitung an Knoten 13: Der Startwert des 3. Fingers von Knoten 13 ist 13 + 2^(3-1) = 17. Der Eintrag FT_13[3] ist daher exakt succ(17) = 18. Da Knoten 13 den direkten Successor für den Schlüssel 17 kennt, leitet er die Anfrage direkt an Knoten 18 weiter.
3. Ankunft bei Knoten 18: Knoten 18 ist für den Schlüssel 17 zuständig, da 18 der kleinste Knoten ID >= 17 ist.
Der Weiterleitungspfad ist: 3 -> 13 -> 18.


#### Typische Stolpersteine / Fehlerquellen:
Fehlendes Modulo 32 bei der Berechnung der Fingers (z. B. 18+16 = 34 -> 34 mod 32 = 2, succ(2) = 3). Falsches Routing bei Schritt 2: Wenn der exakte Successor eines Schlüssels k in der Finger-Tabelle als FT[i] = succ(k) bekannt ist, wird die Anfrage direkt an diesen Successor weitergeleitet.


---

### Aufgabe 2: Bei der iterativen DNS-Namensauflösung für ftp.cs.vu.nl frag...

- **Klausurrelevant**: Ja (Tags: `klausur_sose_2025, dns, namensaufloesung, iterativ`)


#### Aufgabenstellung:
Bei der iterativen DNS-Namensauflösung für ftp.cs.vu.nl fragt ein Resolver schrittweise Nameserver ab. Weisen Sie die Nameserver (a-d), die Zonen, die übertragenen Namensteile in den Anfragen (Msg 1-8) und die Adressverweise in den Antworten (Msg 1-8) einander zu.

Nameserver-Rollen:
- a: Root-Nameserver
- b: nl-Nameserver
- c: vu-Nameserver
- d: cs-Nameserver

(a) Welche Zone wird von welchem Nameserver verwaltet?
(b) Welche Namensteile werden in welchen Anfrage-Nachrichten übertragen?
(c) Welche Adressverweise werden in welchen Antwort-Nachrichten zurückgegeben?


#### Musterlösung:
(a) Zonen-Zuordnung:
- Server a verwaltet die Root-Domäne.
- Server b verwaltet die nl-Domäne.
- Server c verwaltet die vu-Domäne.
- Server d verwaltet die cs-Domäne.

(b) Übertragene Namensteile in Anfragen:
- Msg 1 (Resolver -> a): [nl, vu, cs, ftp]
- Msg 3 (Resolver -> b): [vu, cs, ftp]
- Msg 5 (Resolver -> c): [cs, ftp]
- Msg 7 (Resolver -> d): [ftp]

(c) Adressverweise in Antworten:
- Msg 2 (a -> Resolver): #[nl] (Referral auf Server b)
- Msg 4 (b -> Resolver): #[vu] (Referral auf Server c)
- Msg 6 (c -> Resolver): #[cs] (Referral auf Server d)
- Msg 8 (d -> Resolver): #[ftp] (Liefert finale IP-Adresse)


#### Typische Stolpersteine / Fehlerquellen:
Verwechslung von iterativer und rekursiver Auflösung (bei rekursiver Auflösung geht die Kette direkt von Server zu Server weiter). Falsches Zuordnen der Nachrichten-Nummern (ungerade Nummern sind Anfragen des Resolvers, gerade Nummern sind Antworten der Nameserver).
