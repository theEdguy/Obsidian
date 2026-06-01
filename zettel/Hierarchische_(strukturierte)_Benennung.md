---
id: 4e4e04da-deb0-4e39-a410-4a2ffb947d3f
title: "Hierarchische (strukturierte) Benennung"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - namensvergabe
  - namensauflösung
  - skalierbarkeit
  - baumstruktur
  - netzwerk
  - koordination
  - datenorganisation
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Hierarchische (strukturierte) Benennung]]

- **Kernkonzept:** Hierarchische [[Benennung|Benennungen]] organisieren [[Entität|Entitäten]] in einem baumartigen [[Namensraum|Namensraum]], wobei [[Verzeichnisknoten]] auf untergeordnete Knoten verweisen und [[Blattknoten]] die eigentlichen [[Entität|Entitäten]] repräsentieren. Dies ermöglicht eine strukturierte und skalierbare [[Adressierung]] von Ressourcen in [[Verteilte Systeme|verteilten Systemen]].
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der eindeutigen und effizienten [[Adressierung]] von [[Entität|Entitäten]] in großen, verteilten Systemen. Es ermöglicht eine klare [[Strukturierung]] von [[Namensräume|Namensräumen]], vereinfacht die [[Namensauflösung]] und unterstützt die [[Skalierbarkeit]] durch Partitionierung und [[Replikation]] von Knoten.
- **Abgrenzung & Grenzen:** Hierarchische [[Benennung|Benennungen]] sind weniger geeignet für Systeme mit häufigen Änderungen der [[Struktur]] oder flachen [[Namensräume|Namensräumen]], da der Verwaltungsaufwand für die Baumstruktur hoch sein kann. Alternativen wie lineare (flache) [[Benennung|Benennungen]] oder dezentrale Ansätze (z. B. [[DHT|verteilte Hash-Tabellen]]) können hier effizienter sein. Zudem erfordert die [[Namensauflösung]] einen [[Closure-Mechanismus]], der nicht immer trivial zu implementieren ist.
- **Beispiel / Code:** Ein Beispiel für einen hierarchischen [[Namensraum]] ist das Dateisystem unter Unix/Linux:

```
/
├── home
│   ├── user1
│   │   ├── documents
│   │   │   └── report.txt
│   │   └── images
│   │       └── photo.jpg
│   └── user2
│       └── projects
│           └── code.py
└── etc
    └── hosts
```

- Jeder Pfad (z. B. `/home/user1/documents/report.txt`) repräsentiert eine eindeutige [[Entität]] (hier: eine Datei).
- [[Verzeichnisknoten]] wie `home` oder `user1` verweisen auf untergeordnete Knoten.
- Die [[Namensauflösung]] erfolgt durch schrittweises Durchlaufen des Pfads, beginnend bei der Wurzel (`/`).
