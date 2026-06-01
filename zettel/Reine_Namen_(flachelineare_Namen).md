---
id: 3c661143-e047-42c9-acc3-e4847118b623
title: "Reine Namen (flache/lineare Namen)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - namensauflösung
  - bezeichner
  - skalierbarkeit
  - netzwerk
  - dht
  - mobile-ip
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Reine Namen (flache/lineare Namen)]]

- **Kernkonzept:** Ein [[reiner Name|reine Name]] ist eine bedeutungslose Zeichenkette, die ausschließlich zur Identifikation und zum Vergleich von [[Entität|Entitäten]] in [[verteilte Systeme|verteilten Systemen]] dient. Er trägt keine strukturelle oder semantische Information und ermöglicht eine eindeutige Referenzierung ohne Abhängigkeit von [[Adresse|Adressen]] oder [[Ort|Orten]].
- **Nutzen & Zweck:** Reine Namen lösen das Problem der ortsunabhängigen [[Benennung]] in [[verteilte Systeme|verteilten Systemen]], indem sie eine stabile und eindeutige Identifikation von [[Entität|Entitäten]] ermöglichen – unabhängig von deren [[Zugriffspunkt|Zugriffspunkten]] oder [[Adresse|Adressen]]. Sie bilden die Grundlage für [[Bezeichner]] und [[Namensauflösung]] in skalierbaren Architekturen wie [[verteilte Hash-Tabellen]] oder [[Mobile IP]].
- **Abgrenzung & Grenzen:** Reine Namen sollten nicht genutzt werden, wenn semantische Informationen (z. B. Hierarchien oder Metadaten) für die [[Namensauflösung]] erforderlich sind, da sie keine Struktur aufweisen. Alternativen wie hierarchische Namen (z. B. [[DNS]]) oder attributbasierte [[Benennung]] eignen sich besser für komplexe Suchanfragen oder nutzerfreundliche Systeme. Zudem sind reine Namen ungeeignet für Systeme, die [[Wiederverwendung]] von Namen oder dynamische [[Bindung|Bindungen]] benötigen.
- **Beispiel / Code:** Beispiel für einen [[reiner Name|reinen Namen]] in einer [[verteilte Hash-Tabelle|DHT]] (Chord):

- Knoten-ID: `3A7F2B` (zufällige 160-Bit-Hexadezimalzahl)
- Schlüssel einer [[Entität]]: `5E9C4D`

Die [[Namensauflösung]] erfolgt durch Suche des Knotens mit der kleinsten ID ≥ Schlüssel (Successor-Prinzip). Finger-Tabellen beschleunigen die Suche:
```
FT_3A7F2B[1] = succ(3A7F2B + 2^0) = 3A7F2C
FT_3A7F2B[2] = succ(3A7F2B + 2^1) = 3A7F2E
FT_3A7F2B[3] = succ(3A7F2B + 2^2) = 3A7F32
```
