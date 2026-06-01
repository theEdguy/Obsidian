---
id: "a1b2c3d4-e5f6-4789-8a0b-123456789012"
title: "Vorlesung: Prozesse in Verteilten Systemen"
date: 2023-10-15
tags:
  - verteilte_systeme
  - vorlesung
  - lektürenotiz
  - literature
source: "subjects/distributed_systems/video/03-Prozesse.mp4"
---

# Vorlesung: Prozesse in Verteilten Systemen

- **Quelle:** `subjects/distributed_systems/video/03-Prozesse.mp4`
- **Fach:** Distributed Systems

## 🧩 Einführung in Prozesse und Threads

*Timestamp im Video:* `00:00:13 - 00:10:47`

- **Verteilte Systeme** bestehen aus autonomen Rechen-Elementen, die als kohärentes Gesamtsystem agieren. Die logische Struktur wird durch Komponenten und Konnektoren definiert.
- **Prozesse** sind Programme in Ausführung und kombinieren mehrere **Threads**, die die kleinsten Ausführungseinheiten darstellen.
- **Threads** beinhalten einen Kontext (z.B. Stack-Speicher, Adressregister, Programmzähler) und ermöglichen effizientes Umschalten zwischen verschiedenen Ausführungssträngen innerhalb eines Prozesses.
- **Kontextwechsel** zwischen Threads sind effizienter als zwischen Prozessen, da kein Wechsel zwischen User- und Kernel-Modus erforderlich ist.
- **Vorteile von Threads** umfassen die Vermeidung von Blockierungen, Nutzung mehrerer Prozessorkerne und bessere Strukturierung von Programmen.

**Referenzierte Zettel:**
- [[Verteilte Systeme]]
- [[Prozess (Informatik)]]
- [[Thread (Informatik)]]
- [[Kontextwechsel]]
- [[User-Modus vs. Kernel-Modus]]

---

## 🔄 Virtualisierung und Ressourcenverwaltung

*Timestamp im Video:* `00:24:12 - 00:33:14`

- **Virtualisierung** ermöglicht die Nutzung von Ressourcen durch Abstraktion der physikalischen Hardware oder Software-Plattformen.
- **Virtuelle Prozessoren** teilen die Rechenzeit zwischen mehreren Threads und Prozessen auf, um die Hardware effizient zu nutzen.
- **Drei Ebenen der Virtualisierung**:
  - Hardware-Ebene (Maschineninstruktionen)
  - Betriebssystem-Ebene (Systemaufrufe)
  - Bibliotheksebene (APIs)
- **Typen von Virtualisierungslösungen**:
  - **Prozess-Virtual Machines** (z.B. Java Virtual Machine)
  - **Native Virtual Machine Monitors** (direkt auf der Hardware)
  - **Hosted Virtual Machine Monitors** (auf Basis eines Host-Betriebssystems)
- **Cloud Computing** nutzt Virtualisierung, um Ressourcen als Dienst anzubieten (IaaS, PaaS, SaaS).

**Referenzierte Zettel:**
- [[Virtualisierung]]
- [[Cloud Computing]]
- [[Infrastructure as a Service (IaaS)]]
- [[Platform as a Service (PaaS)]]
- [[Software as a Service (SaaS)]]

---

## 🌐 Client- und Server-Architekturen

*Timestamp im Video:* `00:36:08 - 00:58:59`

- **Client-Server-Modell** basiert auf dem Request-Reply-Prinzip, bei dem Clients Anfragen an Server senden und auf Antworten warten.
- **Server-Implementierungen** können iterativ (sequentielle Bearbeitung) oder nebenläufig (parallele Bearbeitung durch Threads) erfolgen.
- **Dispatcher-Worker-Modell** trennt die Annahme von Anfragen (Dispatcher) von der Verarbeitung (Worker), um die Effizienz zu steigern.
- **Zustandsbehaftete vs. zustandslose Server**:
  - **Zustandsbehaftet**: Merkt sich Interaktionszustände (z.B. offene Dateien), ermöglicht Caching und Performance-Optimierungen.
  - **Zustandslos**: Einfacher zu implementieren, robuster bei Ausfällen, aber weniger performant.
- **Server-Cluster** nutzen einen logischen Switch, um Anfragen auf mehrere Server zu verteilen (z.B. Round-Robin, Lastverteilung).

**Referenzierte Zettel:**
- [[Client-Server-Modell]]
- [[Dispatcher-Worker-Modell]]
- [[Zustandsbehafteter Server]]
- [[Zustandsloser Server]]
- [[Server-Cluster]]
- [[Lastverteilung]]

---

## 🔄 Code-Migration und Mobile Agenten

*Timestamp im Video:* `01:05:57 - 01:25:26`

- **Code-Migration** bezeichnet das Verschieben von Code oder laufenden Prozessen zwischen Rechenknoten, um Lastverteilung, Netzwerkbelastung oder Flexibilität zu optimieren.
- **Motivationen für Code-Migration**:
  - Lastverteilung auf unterausgelasteten Knoten.
  - Reduzierung der Netzwerkbelastung (z.B. bei großen Datenmengen).
  - Flexibilität durch dynamisches Nachladen von Code (z.B. bei Updates).
- **Varianten der Code-Migration**:
  - **Remote Evaluation** (Code wird vom Client zum Server gesendet und dort ausgeführt).
  - **Code on Demand** (Client lädt Code vom Server und führt ihn lokal aus).
  - **Mobile Agenten** (laufende Programme mit Ausführungszustand migrieren zwischen Knoten).
- **Starke vs. schwache Mobilität**:
  - **Schwache Mobilität**: Nur Code und Daten werden verschoben, Ausführung startet neu.
  - **Starke Mobilität**: Ausführungszustand wird mit migriert, Prozess läuft nahtlos weiter.
- **Virtualisierung** ermöglicht Migration in heterogenen Umgebungen (z.B. Java VM, VM-Monitore).

**Referenzierte Zettel:**
- [[Code-Migration]]
- [[Mobile Agenten]]
- [[Remote Evaluation]]
- [[Code on Demand]]
- [[Starke Mobilität]]
- [[Schwache Mobilität]]
- [[Virtualisierung in heterogenen Systemen]]