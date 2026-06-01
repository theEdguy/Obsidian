---
id: 9aa012c5-4b8e-4955-bbd1-b89046110a39
title: "Geschichtete Architekturen (Layered Architectures)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - schichtenmodell
  - modularität
  - netzwerkprotokolle
  - software-design
  - netzwerk
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Geschichtete Architekturen (Layered Architectures)]]

- **Kernkonzept:** Geschichtete [[Architektur|Architekturen]] organisieren [[Komponente|Komponenten]] eines [[System|Systems]] in hierarchischen [[Schicht|Schichten]], wobei jede [[Schicht]] definierte [[Schnittstelle|Schnittstellen]] und [[Funktion|Funktionen]] für die darüber- oder darunterliegende [[Schicht]] bereitstellt. Dies ermöglicht eine klare [[Trennung der Verantwortlichkeiten]] und fördert [[Abstraktion|Abstraktionen]] auf verschiedenen [[Ebene|Ebenen]].
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der [[Komplexität]] in [[System|Systemen]], indem es [[Trennung der Verantwortlichkeiten]] (Separation of Concerns) und [[Modularität]] ermöglicht. Es verbessert [[Wartbarkeit]], [[Skalierbarkeit]] und [[Wiederverwendbarkeit]], da [[Schicht|Schichten]] unabhängig entwickelt, getestet und ausgetauscht werden können. Zudem reduziert es unübersichtliche [[Abhängigkeit|Abhängigkeiten]] zwischen [[Komponente|Komponenten]] und unterstützt die [[Kapselung]] spezifischer [[Funktion|Funktionen]].
- **Abgrenzung & Grenzen:** Geschichtete [[Architektur|Architekturen]] sind ungeeignet für [[System|Systeme]] mit hohen [[Performance|Performanceanforderungen]] oder [[Echtzeit|Echtzeitsystemen]], da der [[Overhead]] durch [[Schicht|Schichten]]-übergreifende Kommunikation die [[Latenz]] erhöhen kann. Alternativen wie [[monolithische Architekturen]], [[Microservices]] oder [[ereignisgesteuerte Architekturen]] können hier effizienter sein. Im Vergleich zu [[Objekt-basierte Architektur|objektbasierten]] oder [[Service-orientierte Architektur|serviceorientierten]] [[Architektur|Architekturen]] zeichnen sie sich durch strengere [[Hierarchie]] und [[Kopplung]] aus, was die [[Flexibilität]] einschränken kann. Für stark vernetzte [[Komponente|Komponenten]] sind sie weniger geeignet.
- **Beispiel / Code:** ```
// Beispiel: TCP/IP-Protokollstapel als geschichtete Architektur

Layer 4 (Anwendung): [[HTTP]], [[FTP]], [[SMTP]]
Layer 3 (Transport): [[TCP]], [[UDP]]
Layer 2 (Internet): [[IP]]
Layer 1 (Netzwerkzugriff): [[Ethernet]], [[Wi-Fi]]

// Jede Schicht kapselt spezifische Funktionen und kommuniziert
// nur mit der direkt benachbarten Schicht über definierte Schnittstellen.
// Dies illustriert die Prinzipien der [[Kapselung]] und [[Trennung der Verantwortlichkeiten]].
```
