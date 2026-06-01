---
id: 9ff9ff80-eeae-4d58-ab90-30afc4bdda7f
title: "Benennungsgraph"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - namensverwaltung
  - hierarchische-strukturen
  - namensauflösung
  - skalierbarkeit
  - netzwerk-architektur
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Benennungsgraph]]

- **Kernkonzept:** Ein [[Benennungsgraph|Benennungsgraph]] ist eine hierarchische Struktur zur Repräsentation von [[Namensraum|Namensräumen]] in [[Verteiltes System|verteilten Systemen]], bei der [[Knoten|Knoten]] entweder [[Entität|Entitäten]] (Blattknoten) oder Verzeichnisse (Verzeichnisknoten) darstellen und durch Kanten verbunden sind.
- **Nutzen & Zweck:** Der [[Benennungsgraph]] löst das Problem der eindeutigen und strukturierten [[Adressierung]] von [[Ressource|Ressourcen]] in verteilten Systemen. Er ermöglicht die [[Namensauflösung]] durch Pfadverfolgung und unterstützt Mechanismen wie [[Linking]] (Hard/Soft Links) sowie die Verteilung von Namensräumen über mehrere [[Server|Server]] und Administrationsebenen.
- **Abgrenzung & Grenzen:** Ein [[Benennungsgraph]] ist ungeeignet für flache oder lineare [[Benennung|Benennungsmodelle]], bei denen keine Hierarchie benötigt wird. Alternativen wie [[Hashtabelle|Hashtabellen]] oder zentrale [[Registry|Registries]] bieten bessere Performance für einfache [[Zugriffsmuster]], skalieren aber schlechter bei komplexen Namensräumen oder verteilten [[Administration|Administrationen]].
- **Beispiel / Code:** Ein Beispiel für einen Benennungsgraphen (DNS-ähnlich):
```
/home (Verzeichnisknoten)
├── steen (Verzeichnisknoten)
│   ├── keys (Blattknoten, Adresse: /home/steen/keys)
│   └── mbox (Blattknoten, Adresse: /home/steen/mbox)
└── elke (Blattknoten)
```
Namensauflösung von `/home/steen/keys`:
1. Starte bei Wurzel `/`.
2. Folge Kante `home` → Verzeichnisknoten `/home`.
3. Folge Kante `steen` → Verzeichnisknoten `/home/steen`.
4. Folge Kante `keys` → Blattknoten mit Zieladresse.
