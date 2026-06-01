---
id: "a1b2c3d4-e5f6-4789-b012-3456789abcde"
title: "Vorlesung: Einführung in Verteilte Systeme"
date: "2023-10-15"
tags:
  - verteilte_systeme
  - vorlesung
  - lektürenotiz
  - literature
source: "subjects/distributed_systems/video/01-Einfuehrung.mp4"
---

# Vorlesung: Einführung in Verteilte Systeme

- **Quelle:** `subjects/distributed_systems/video/01-Einfuehrung.mp4`
- **Fach:** Distributed Systems

---

## 📌 Definition und Grundkonzepte Verteilter Systeme

*Timestamp im Video:* `00:00:18 - 00:07:07`

**Zusammenfassung des Dozenten:**
- **Definition:** Ein Verteiltes System besteht aus autonomen Rechenelementen, die als ein einzelnes, kohärentes System erscheinen.
  - Autonome Rechenelemente können Computer, Sensoren oder Prozesse sein.
  - Diese Elemente arbeiten zusammen, um eine gemeinsame Aufgabe zu erfüllen, die für den Benutzer wie ein einzelnes System wirkt.
- **Charakteristika:**
  - Kein gemeinsamer Speicher: Kommunikation erfolgt über Nachrichten.
  - Keine gemeinsame Uhrzeit: Synchronisierung ist komplex und erfordert spezielle Algorithmen.
  - Verwaltung der Knoten: Identifikation, Adressierung und Authentifizierung der Knoten sind essenziell.
- **Sicherheitsmechanismen:** Kritisch, um betrügerische Knoten (z.B. bei Phishing-Angriffen) zu verhindern.
- **Middleware:** Eine Softwareschicht oberhalb der Betriebssysteme, die die Programmierung verteilter Anwendungen vereinfacht.
  - Bietet allgemeine Funktionen wie Knotenverwaltung, Datentransformation und Sicherheitsprotokolle.

**Referenzierte Zettel:**
- [[Verteilungstransparenz]]
- [[Middleware]]
- [[Synchronisationsalgorithmen]]
- [[Sicherheit in verteilten Systemen]]

---

## 🎯 Anforderungen und Transparenz in Verteilten Systemen

*Timestamp im Video:* `00:07:07 - 00:14:36`

**Zusammenfassung des Dozenten:**
- **Verteilungstransparenz:** Ziel ist es, dem Benutzer das Gefühl zu geben, ein einzelnes System zu nutzen, unabhängig von der tatsächlichen Verteilung der Knoten.
  - **Ortstransparenz:** Der Benutzer muss den physischen Ort der Ressource nicht kennen.
  - **Migrations- und Relokationstransparenz:** Ressourcen können ihren Ort ändern, ohne dass der Benutzer dies bemerkt.
  - **Replikationstransparenz:** Mehrere Kopien einer Ressource existieren, ohne dass der Benutzer Unterschiede wahrnimmt.
  - **Nebenläufigkeitstransparenz:** Mehrere Benutzer greifen gleichzeitig auf Ressourcen zu, ohne sich gegenseitig zu beeinflussen.
  - **Ausfalltransparenz:** Temporäre oder partielle Ausfälle von Knoten bleiben für den Benutzer unsichtbar.
- **Replikation:** Technik zur Leistungssteigerung durch Vervielfältigung von Ressourcen.
  - Problem: Inkonsistenz der Kopien, wenn sich der Zustand der Ressource ändert.
  - Lösung: Synchronisation der Zugriffe, um Konsistenz zu gewährleisten.
- **Ausfallsicherheit:** In großen Systemen (z.B. Google) sind Ausfälle einzelner Knoten unvermeidbar.
  - Das System muss trotzdem korrekte Ergebnisse liefern, selbst wenn einzelne Knoten fehlerhafte Daten zurückgeben.

**Referenzierte Zettel:**
- [[Replikation]]
- [[Konsistenzmodelle]]
- [[Fehlertoleranz]]
- [[Transparenz in verteilten Systemen]]

---

## 🔧 Entwurfsziele: Offenheit und Skalierbarkeit

*Timestamp im Video:* `00:14:36 - 00:29:14`

**Zusammenfassung des Dozenten:**
- **Offenheit:** Verteilte Systeme sollen offen sein, d.h. Schnittstellen und Protokolle sind klar spezifiziert und öffentlich zugänglich.
  - Ermöglicht die Integration verschiedener Komponenten und die Erweiterung des Systems.
  - Beispiel: Webbasierte Systeme, die auf offenen Standards wie HTTP und HTML basieren.
- **Skalierbarkeit:** Fähigkeit eines Systems, sich an gestiegene Anforderungen anzupassen.
  - **Größenmäßige Skalierbarkeit:** Erhöhung der Leistungsfähigkeit durch Hinzufügen weiterer Knoten.
  - **Geografische Skalierbarkeit:** Ausdehnung des Systems über größere räumliche Distanzen.
    - Herausforderungen: Höhere Latenzzeiten, unzuverlässige Netzwerkverbindungen, fehlende Broadcast/Multicast-Funktionalität.
  - **Administrative Skalierbarkeit:** Nutzung des Systems über mehrere Organisationen hinweg.
    - Herausforderungen: Konflikte durch unterschiedliche Richtlinien (z.B. Sicherheit, Nutzung, Abrechnung).
- **Techniken zur Skalierbarkeit:**
  - **Verbergen von Kommunikationslatenz:** Nutzung asynchroner Kommunikation, um Wartezeiten zu minimieren.
  - **Partitionierung:** Aufteilung von Daten oder Berechnungen auf verschiedene Knoten (z.B. DNS, World Wide Web).
  - **Replikation/Caching:** Erstellung von Kopien von Ressourcen, um die Last zu verteilen und die Leistung zu steigern.
    - Problem: Inkonsistenz der Kopien, abhängig von der Anwendung (z.B. Wetterdaten vs. Banktransaktionen).

**Referenzierte Zettel:**
- [[Skalierbarkeit]]
- [[Partitionierung]]
- [[Asynchrone Kommunikation]]
- [[Geografische Verteilung]]

---

## 🏗️ Architektur und Typen Verteilter Systeme

*Timestamp im Video:* `00:29:14 - 00:47:29`

**Zusammenfassung des Dozenten:**
- **Hochleistungsrechnen:**
  - **Cluster Computing:** Homogene Knoten mit identischer Hardware und Betriebssystemen, verbunden über Hochgeschwindigkeitsnetzwerke.
    - Beispiel: Apache Hadoop für Big Data-Verarbeitung mit MapReduce.
  - **Grid Computing:** Heterogene Knoten, oft über mehrere Organisationen verteilt.
    - Beispiel: BW-HPC (Baden-Württemberg High Performance Computing).
  - **Cloud Computing:** Bereitstellung von Ressourcen als Dienstleistung (IaaS, PaaS, SaaS).
    - Beispiele: Amazon EC2 (Infrastruktur), Google App Engine (Plattform), Google Docs (Software).
- **Verteilte betriebliche Informationssysteme:**
  - Integration heterogener Anwendungen in Unternehmen (Enterprise Application Integration, EAI).
  - **Client-zentrierte Integration:** Externer Client steuert die Interaktion zwischen Anwendungen.
  - **Direkte Kommunikation:** Anwendungen kommunizieren direkt miteinander (z.B. über Remote Procedure Calls oder Publish-Subscribe-Systeme).
  - **Transaktionsverarbeitung:** Nutzung verschachtelter Transaktionen, um Konsistenz in verteilten Systemen zu gewährleisten.
    - ACID-Eigenschaften: Atomarität, Konsistenz, Isolation, Dauerhaftigkeit.

**Referenzierte Zettel:**
- [[Cluster Computing]]
- [[Grid Computing]]
- [[Cloud Computing]]
- [[Enterprise Application Integration (EAI)]]
- [[Transaktionsverarbeitung]]
- [[Publish-Subscribe-Systeme]]

---

## 🌐 Pervasive Systeme und Internet der Dinge (IoT)

*Timestamp im Video:* `00:47:29 - 01:04:09`

**Zusammenfassung des Dozenten:**
- **Ubiquitäre Systeme:** Allgegenwärtige, in die Umgebung integrierte Systeme (z.B. Smart Home).
  - Interaktion erfolgt unauffällig (z.B. über Sensoren, Schalter).
  - Kontextbewusstsein: Systeme passen ihr Verhalten an die Umgebung an (z.B. Lichtsteuerung abhängig von Tageszeit).
  - Autonomie: Neue Geräte fügen sich automatisch in das System ein.
- **Mobile Computing:** Fokus auf mobile Geräte (Smartphones, Tablets), die ihren Standort wechseln.
  - Herausforderungen: Dynamische Netzwerkerkennung (Discovery), unzuverlässige Verbindungen.
- **Sensornetze:** Große Anzahl ressourcenbeschränkter Sensoren zur Umweltüberwachung.
  - Energieeffizienz: Arbeitszyklen (Aktiv-/Ruhephasen) zur Reduzierung des Energieverbrauchs.
  - Synchronisation: Uhren der Sensoren müssen regelmäßig synchronisiert werden, um Kommunikation zu ermöglichen.
  - Datenverarbeitung: Abfragen an das Sensornetz können zentral (Betreiberknoten) oder dezentral (lokal in Sensoren) verarbeitet werden.

**Referenzierte Zettel:**
- [[Ubiquitous Computing]]
- [[Mobile Computing]]
- [[Sensornetze]]
- [[Energieeffizienz in verteilten Systemen]]
- [[Kontextbewusstsein]]