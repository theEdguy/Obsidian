---
id: 4969a2e5-5b79-43f3-b9bc-6c53f084e181
title: "Bezeichner"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - namensauflösung
  - identifikation
  - dht
  - netzwerk
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Bezeichner]]

- **Kernkonzept:** Ein [[Bezeichner]] ist ein spezieller [[Name|Namen]], der in [[verteilte Systeme|verteilten Systemen]] genau eine [[Entität]] eindeutig identifiziert und keine Wiederverwendung erlaubt. Im Gegensatz zu [[Adresse|Adressen]] oder allgemeinen [[Name|Namen]] trägt er oft keine semantische Bedeutung, kann aber strukturierte Informationen enthalten.
- **Nutzen & Zweck:** [[Bezeichner]] lösen das Problem der eindeutigen und dauerhaften Referenzierung von [[Entität|Entitäten]] in [[verteilte Systeme|verteilten Systemen]], unabhängig von deren [[Adresse|Adressen]] oder [[Zugriffspunkt|Zugriffspunkten]]. Sie ermöglichen [[Namensauflösung]] und bilden die Grundlage für [[Namenssysteme]] wie [[DNS]] oder [[verteilte Hash-Tabellen]].
- **Abgrenzung & Grenzen:** [[Bezeichner]] sind ungeeignet, wenn [[Name|Namen]] semantische Informationen tragen sollen (z. B. lesbare URLs) oder wenn [[Adresse|Adressen]] dynamisch wechseln müssen (z. B. bei mobilen Geräten ohne feste Heimatadresse). Alternativen wie [[Broadcasting]] oder hierarchische [[Namensauflösung]] skalieren besser für bestimmte Anwendungsfälle, erfordern aber zusätzliche Mechanismen zur Eindeutigkeit.
- **Beispiel / Code:** Beispiel für einen [[Bezeichner]] in einer [[verteilte Hash-Tabelle|verteilten Hash-Tabelle (DHT)]] wie Chord:
```
// Eindeutiger 160-Bit-Bezeichner für eine Entität
Bezeichner entityID = SHA1("Datei_XYZ");
// Knoten mit nächsthöherem Bezeichner speichert die Entität
Knoten responsibleNode = findSuccessor(entityID);
```

In [[Mobile IP]] wird ein [[Bezeichner]] (z. B. die Heimatadresse) von der aktuellen [[Adresse]] (Care-of-Adresse) getrennt aufgelöst.
