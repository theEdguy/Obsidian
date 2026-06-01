---
id: 9b9a950c-bd70-44b2-95b3-cd74fbaa95f5
title: "Lineare Benennung"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - namensauflösung
  - bezeichner
  - netzwerk
  - dht
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Lineare Benennung]]

- **Kernkonzept:** Lineare [[Benennung|Benennungen]] verwenden [[Bezeichner]], die keine inhärente Struktur oder Bedeutung tragen (z. B. zufällige Zeichenketten), um [[Entität|Entitäten]] in [[Verteiltes System|verteilten Systemen]] eindeutig zu referenzieren. Sie ermöglichen die [[Namensauflösung]] von [[Zugriffspunkt|Zugriffspunkten]] ohne Abhängigkeit von der [[Adresse]] der [[Entität]].
- **Nutzen & Zweck:** Lineare [[Benennung|Benennungen]] lösen das Problem der eindeutigen und ortsunabhängigen Identifikation von [[Entität|Entitäten]] in [[Verteiltes System|verteilten Systemen]]. Sie ermöglichen skalierbare [[Namensauflösung]] durch Mechanismen wie [[Broadcasting]], heimatgestützte Ansätze oder [[Verteilte Hash-Tabelle|verteilte Hash-Tabellen (DHT)]], ohne dass Nutzer technische [[Adresse|Adressen]] kennen müssen.
- **Abgrenzung & Grenzen:** Lineare [[Benennung|Benennungen]] sind ungeeignet, wenn [[Bezeichner]] semantische Informationen tragen sollen (z. B. hierarchische Pfade). Sie skalieren schlecht bei einfachen Lösungen wie [[Broadcasting]] und erfordern komplexere Ansätze (z. B. [[DHT]]) für große Systeme. Im Vergleich zu hierarchischen [[Benennung|Benennungen]] fehlt ihnen die Fähigkeit, strukturelle Beziehungen abzubilden.
- **Beispiel / Code:** Beispiel für eine lineare [[Benennung]] in Chord (DHT):

1. Knoten und [[Entität|Entitäten]] erhalten zufällige m-Bit-[[Bezeichner]] (z. B. 128 Bit).
2. Eine [[Entität]] mit Schlüssel k wird dem Knoten mit dem kleinsten [[Bezeichner]] ≥ k zugeordnet (Successor).
3. Finger-Tabellen beschleunigen die Suche:
   ```
   FT_p[i] = succ(p + 2^(i-1))
   ```
4. Beispielsuche: Schlüssel 26 von Knoten 1 aus → Weiterleitung über Finger-Tabellen bis zum zuständigen Knoten.
