---
id: 5fb2e7d6-03bb-4c02-b784-317ae12ded55
title: "Benennung in verteilten Systemen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - benennung
  - namensauflösung
  - netzwerk
  - skalierbarkeit
  - adressierung
  - dht
  - mobile-ip
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Benennung in verteilten Systemen]]

- **Kernkonzept:** Die Benennung in [[verteiltes System|verteilten Systemen]] ermöglicht das eindeutige Referenzieren von [[Entität|Entitäten]] durch [[Name|Namen]], [[Bezeichner]] oder [[Adresse|Adressen]], um [[Zugriffspunkt|Zugriffspunkte]] zu lokalisieren. Sie trennt ortsunabhängige [[Name|Namen]] von technischen [[Adresse|Adressen]] und löst diese über [[Namensauflösung]] auf.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der Identifikation und Lokalisierung von [[Entität|Entitäten]] in [[verteiltes System|verteilten Systemen]], wo [[Nutzer]] benutzerfreundliche [[Bezeichner]] verwenden, während die [[Protokoll]]ebene technische [[Adresse|Adressen]] benötigt. Es ermöglicht Skalierbarkeit, Mobilität und effiziente [[Kommunikation]].
- **Abgrenzung & Grenzen:** Lineare [[Benennung]] skaliert schlecht für große [[Netzwerk|Netzwerke]] (z. B. Broadcasting). Heimatbasierte Ansätze sind ungeeignet für [[Entität|Entitäten]] mit häufigen Standortwechseln oder globaler Verteilung. Hierarchische Ansätze (wie DNS) erfordern komplexe Verwaltung. [[Verteilte Hash-Tabelle|Verteilte Hash-Tabellen]] (DHTs) sind effizient, aber weniger flexibel für dynamische [[Name|Namen]] mit semantischer Bedeutung.
- **Beispiel / Code:** // Beispiel: Namensauflösung in Chord (DHT)
// Knoten 1 sucht Schlüssel 26:
1. Finger-Tabelle von Knoten 1: [9, 9, 9, 18, 20]
2. Suche nach succ(26):
   - 26 > FT[1] (9) → Weiterleitung an Knoten 9
   - Knoten 9 leitet an Knoten 20 weiter
   - Knoten 20 leitet an Knoten 28 weiter (succ(26))
3. Rückgabe der Adresse von Knoten 28.

// Mobile IP (Heimatbasiert):
1. Client sendet Paket an Heimatadresse.
2. Heimatstandort antwortet mit aktueller Adresse.
3. Paket wird zum aktuellen Standort getunnelt.
