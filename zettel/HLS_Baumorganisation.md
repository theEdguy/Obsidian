---
id: 9fc5ed5f-1f31-4f1a-bfd8-71ce0ecfdacd
title: "HLS: Baumorganisation"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - namensauflösung
  - baumstruktur
  - hierarchische-benennung
  - skalierbarkeit
  - adressverwaltung
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[HLS: Baumorganisation]]

- **Kernkonzept:** Die [[HLS|HLS]]-Baumorganisation ist ein hierarchisches [[Benennungssystem|Benennungssystem]] in [[Verteilte Systeme|Verteilten Systemen]], das [[Entität|Entitäten]] und deren [[Adresse|Adressen]] in einer Baumstruktur speichert. Jeder Knoten enthält [[Zeiger]] auf seine [[Kindknoten]], während [[Blattknoten]] die tatsächlichen [[Adresse|Adressen]] der [[Entität|Entitäten]] halten.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der effizienten [[Suche]], [[Einfügung]] und Verwaltung von [[Entität|Entitäten]] in großen [[Verteilte Systeme|Verteilten Systemen]]. Es ermöglicht skalierbare [[Namensauflösung]] und reduziert die [[Komplexität]] bei der [[Adressverwaltung]] durch hierarchische Strukturierung.
- **Abgrenzung & Grenzen:** Die [[HLS|HLS]]-Baumorganisation eignet sich nicht für hochdynamische Systeme mit häufigen [[Adresse|Adressänderungen]], da die [[Invariante|Invarianten]] der Baumstruktur aufwendig zu warten sind. Im Vergleich zu [[lineare Benennung|linearen Benennungssystemen]] ist sie komplexer, bietet aber bessere Skalierbarkeit. Alternativen wie [[DHT|Distributed Hash Tables]] sind bei flachen [[Namensräume|Namensräumen]] effizienter.
- **Beispiel / Code:** Ein Beispiel für die Baumstruktur:
```
Wurzel (kennt alle Entitäten)
├── Domäne D1 (Zeiger auf Kindknoten)
│   └── Knoten M (enthält Standort für Entität E)
│       └── Blattknoten (speichert Adresse von E)
└── Domäne D2 (Zeiger auf Kindknoten)
    └── Knoten N (leerer Knoten ohne Daten)
```
Bei einer [[Suche]] nach Entität E startet der Prozess am lokalen Blattknoten und folgt den [[Zeiger|Zeigern]] aufwärts oder abwärts, bis die [[Adresse]] gefunden wird.
