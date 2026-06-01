---
id: 65bb60d7-1ffe-45da-bd39-075e470be4ff
title: "Adressen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - netzwerk
  - namensauflösung
  - adressierung
  - dht
  - chord
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Adressen]]

- **Kernkonzept:** In [[Verteilte Systeme|verteilten Systemen]] sind Adressen spezifische [[Bezeichner|Bezeichner]], die [[Zugriffspunkt|Zugriffspunkte]] einer [[Entität]] eindeutig identifizieren und deren Lokalisierung ermöglichen. Sie sind essenziell für die [[Kommunikation]] zwischen [[Komponente|Komponenten]], unterscheiden sich jedoch von ortsunabhängigen [[Name|Namen]] oder [[Bezeichner|Bezeichnern]].
- **Nutzen & Zweck:** Adressen lösen das Problem der technischen Erreichbarkeit von [[Entität|Entitäten]] in [[Verteilte Systeme|verteilten Systemen]], indem sie eine direkte [[Namensauflösung]] ermöglichen. Ohne Adressen wäre keine effiziente [[Kommunikation]] oder [[Dienstnutzung]] möglich, da [[Bezeichner]] allein keine physische oder logische Position angeben.
- **Abgrenzung & Grenzen:** Adressen sollten nicht mit [[Name|Namen]] oder [[Bezeichner|Bezeichnern]] verwechselt werden, die keine Ortsinformation tragen. Sie sind ungeeignet für Szenarien, in denen [[Ortsunabhängigkeit]] gefordert ist (z. B. bei mobilen [[Entität|Entitäten]]). Alternativen wie [[Broadcasting]] oder [[Heimatbasierte Ansätze]] skalieren schlecht oder sind ineffizient für große Systeme. [[Verteilte Hash-Tabellen]] oder hierarchische [[Namenssysteme]] (z. B. DNS) sind oft besser geeignet.
- **Beispiel / Code:** Beispiel für eine Adressauflösung in Chord (DHT):

1. Knoten 1 sucht Schlüssel `k = 26`.
2. Finger-Tabelle von Knoten 1:
   ```
   FT1[1] = succ(1 + 2^0) = succ(2) = 9
   FT1[2] = succ(1 + 2^1) = succ(3) = 9
   FT1[3] = succ(1 + 2^2) = succ(5) = 14
   ```
3. Anfrage wird an Knoten 9 weitergeleitet, der `k = 26` verwaltet.

Mobile IP-Beispiel:
- Client sendet Paket an Heimatadresse eines Hosts.
- Heimatstandort leitet Paket per Tunnel an aktuellen Standort weiter.
