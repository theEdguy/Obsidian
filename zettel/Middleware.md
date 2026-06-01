---
id: 3875e10c-d16d-43ba-8426-67a498f6e118
title: "Middleware"
date: 2026-06-01
tags:
  - verteilte_systeme
  - software
  - architektur
  - kommunikation
  - integration
  - middleware
  - publish-subscribe
  - tupelraum
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Middleware]]

- **Kernkonzept:** Eine [[Software]]-Schicht, die als Vermittler zwischen [[Anwendung|Anwendungen]] oder [[Systemkomponente|Systemkomponenten]] fungiert und häufig genutzte Funktionen in [[Verteilte Systeme|verteilten Systemen]] bereitstellt. Sie abstrahiert die [[Kommunikation]], [[Datenverwaltung]] und [[Ressource]]-Nutzung, um die [[Komplexität]] für [[Anwendung|Anwendungsentwickler]] zu reduzieren.
- **Nutzen & Zweck:** Middleware löst das Problem der [[Heterogenität]] und [[Komplexität]] in [[Verteilte Systeme|verteilten Systemen]], indem sie standardisierte [[Schnittstelle|Schnittstellen]] und Dienste wie [[Transparenz]], [[Entkopplung]] von [[Client|Clients]] und [[Server|Servern]], [[Integration]] von [[Legacy-Systeme|Legacy-Systemen]] sowie [[Skalierbarkeit]] und [[Fehlertoleranz]] bereitstellt. Sie vereinfacht die Entwicklung durch Abstraktion von [[Netzwerkkommunikation|Netzwerkkommunikationsdetails]] und fördert die [[Wiederverwendbarkeit]] von [[Komponente|Komponenten]].
- **Abgrenzung & Grenzen:** Middleware ist nicht für alle [[Systemarchitektur|Systemarchitekturen]] geeignet: In einfachen, monolithischen Systemen führt sie zu unnötigem Overhead, während direkte [[Netzwerkkommunikation]] oder [[Protokoll|Protokolle]] wie HTTP effizienter sein können. Zudem stößt sie in [[Echtzeitsystem|Echtzeitsystemen]] mit strengen [[Latenz|Latenzanforderungen]] an ihre Grenzen, da die zusätzliche Abstraktionsschicht die Performance beeinträchtigen kann. Die Abhängigkeit von einer spezifischen Middleware kann zudem die [[Portabilität]] einschränken und die [[Wartbarkeit]] erschweren, wenn [[Technologie-Stack|Technologie-Stacks]] gewechselt werden müssen.
- **Beispiel / Code:** {'beschreibung': 'Middleware kann verschiedene [[Kommunikationsmuster]] unterstützen, darunter [[Client-Server-Architektur|Client-Server]] und [[Publish-Subscribe]]. Ein Beispiel für den [[Publish-Subscribe]]-Ansatz mit dem [[Linda-Tupelraum]] als Middleware:', 'code': '```python\n# Bob (Produzent) schreibt Nachrichten in den Tupelraum\nblog = linda.universe._rd(("MicroBlog", linda.TupleSpace))[1]\nblog._out(("bob", "distsys", "I am studying chap 2"))\nblog._out(("bob", "distsys", "The linda example’s pretty simple"))\n\n# Chuck (Konsument) liest Nachrichten aus dem Tupelraum\nblog = linda.universe._rd(("MicroBlog", linda.TupleSpace))[1]\nt1 = blog._rd(("bob", "distsys", str))  # Blockiert bis passendes Tupel verfügbar\n```', 'erlaeuterung': 'Der [[Linda-Tupelraum]] fungiert hier als Middleware, die eine [[Entkopplung]] von [[Produzent|Produzenten]] (Bob) und [[Konsument|Konsumenten]] (Chuck) ermöglicht. Die Operationen `_out` (Schreiben), `_rd` (lesendes Warten) und `_in` (entfernendes Lesen) abstrahieren die [[Kommunikation]] und [[Synchronisation]], ohne dass direkte [[Netzwerkverbindung|Netzwerkverbindungen]] zwischen den [[Prozess|Prozessen]] hergestellt werden müssen. Ein weiteres Beispiel ist CORBA (Common Object Request Broker Architecture), das die Kommunikation zwischen [[Objekt|Objekten]] in heterogenen Umgebungen standardisiert.'}
