---
id: cc2e710f-3fa1-4309-8aa4-4a5db94d5d1b
title: "Verteilte Hash-Tabellen (Distributed Hash Tables, DHT)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - benennung
  - peer-to-peer
  - datenstrukturen
  - netzwerk
  - skalierbarkeit
  - algorithmen
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Verteilte Hash-Tabellen (Distributed Hash Tables, DHT)]]

- **Kernkonzept:** Verteilte Hash-Tabellen (DHTs) sind dezentrale [[Datenstruktur|Datenstrukturen]], die eine effiziente [[Namensauflösung|Namensauflösung]] in [[verteilte Systeme|verteilten Systemen]] ermöglichen, indem sie [[Bezeichner|Bezeichner]] auf [[Adresse|Adressen]] abbilden und dabei Skalierbarkeit und Fehlertoleranz gewährleisten.
- **Nutzen & Zweck:** DHTs lösen das [[Problem]] der [[Skalierbarkeit]] bei der [[Auflösung]] linearer [[Name|Namen]] in großen [[Netzwerk|Netzwerken]], indem sie die [[Lastverteilung]] auf viele [[Knoten]] verteilen und ohne zentrale [[Instanz]] auskommen. Sie ermöglichen effizientes [[Nachschlagen]] von [[Ressource|Ressourcen]] in [[Peer-to-Peer-Systeme|Peer-to-Peer-Systemen]] oder [[verteilte Speichersysteme|verteilten Speichersystemen]].
- **Abgrenzung & Grenzen:** DHTs sind ungeeignet für [[Anwendung|Anwendungen]], die hierarchische [[Benennung]] oder komplexe [[Abfrage|Abfragen]] erfordern (z. B. [[Datenbank|Datenbanken]] mit SQL). Im Vergleich zu [[Broadcasting]]- oder [[heimatbasierte Ansätze|heimatbasierten Ansätzen]] bieten sie bessere Skalierbarkeit, erfordern aber eine strukturierte [[Topologie]] und sind weniger effizient für hochdynamische [[Netzwerk|Netzwerke]] mit häufigen [[Knotenausfall|Knotenausfällen]]. Alternativen wie [[DNS]] oder [[Hierarchical Location Services (HLS)]] sind besser für geografisch verteilte oder mobile [[Entität|Entitäten]] geeignet.
- **Beispiel / Code:** Beispiel: Chord-DHT (vereinfacht)

1. **Knoten- und Schlüsselverteilung**:
   - Jeder [[Knoten]] erhält einen zufälligen m-Bit-Bezeichner (z. B. 160 Bit).
   - Jede [[Ressource]] erhält einen Schlüssel k (ebenfalls m-Bit).
   - Die Ressource mit Schlüssel k wird auf dem [[Knoten]] gespeichert, dessen Bezeichner der kleinste Wert ≥ k ist (Successor succ(k)).

2. **Finger-Tabelle (Routing-Tabelle)**:
   - Jeder Knoten p verwaltet eine Finger-Tabelle mit Einträgen:
     FTp[i] = succ(p + 2^(i-1)) für 1 ≤ i ≤ m.
   - Beispiel: Für m=6 und Knoten p=1:
     FT1[1] = succ(1 + 1) = succ(2) = 3
     FT1[2] = succ(1 + 2) = succ(3) = 3
     FT1[3] = succ(1 + 4) = succ(5) = 9

3. **Suche nach Schlüssel k=26 von Knoten 1** (aus der Vorlesung):
   - Knoten 1 leitet die Anfrage an FT1[5] = succ(1 + 16) = 28 weiter.
   - Knoten 28 leitet die Anfrage an FT28[2] = succ(28 + 2) = succ(30) = 1 weiter.
   - Knoten 1 erkennt, dass succ(26) = 28 ist, und gibt die Adresse von Knoten 28 zurück.
