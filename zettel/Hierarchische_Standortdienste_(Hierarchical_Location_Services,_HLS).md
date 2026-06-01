---
id: 877f9c4d-5060-4dc1-8db3-31380aca150d
title: "Hierarchische Standortdienste (Hierarchical Location Services, HLS)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - namensauflösung
  - verteilte-systeme
  - netzwerk
  - hierarchische-architektur
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Hierarchische Standortdienste (Hierarchical Location Services, HLS)]]

- **Kernkonzept:** Hierarchische Standortdienste (HLS) organisieren die [[Namensauflösung|Namensauflösungen]] in [[verteilte Systeme|verteilten Systemen]] durch einen Suchbaum, der das Netzwerk in hierarchische [[Domäne|Domänen]] gliedert. Jede [[Domäne]] wird von einem Verzeichnisknoten verwaltet, der die [[Adresse|Adressen]] der enthaltenen [[Entität|Entitäten]] speichert.
- **Nutzen & Zweck:** HLS löst das [[Skalierbarkeitsproblem|Skalierbarkeitsproblem]] bei der [[Auflösung|Auflösung]] linearer [[Bezeichner]] in großen [[verteilte Systeme|verteilten Systemen]], indem es die Suche nach [[Zugriffspunkt|Zugriffspunkten]] effizient strukturiert. Es vermeidet die Nachteile von [[Broadcasting]] oder heimatbasierten Ansätzen, wie unnötige Netzlast oder schlechte geografische Skalierbarkeit.
- **Abgrenzung & Grenzen:** HLS ist weniger geeignet für hochdynamische Umgebungen mit häufigen [[Entität|Entitäts]]-Umzügen, da die hierarchische Struktur Verwaltungsaufwand verursacht. Im Vergleich zu [[verteilte Hash-Tabellen (DHT)|verteilten Hash-Tabellen]] (z. B. Chord) bietet HLS bessere geografische Lokalität, skaliert aber schlechter bei extrem großen oder flachen Netzwerken. Einfache Lösungen wie [[Broadcasting]] sind für kleine, lokale Netzwerke oft ausreichend.
- **Beispiel / Code:** Ein HLS-Suchbaum könnte wie folgt strukturiert sein:

1. Wurzelverzeichnisknoten `dir(T)` verwaltet die Top-Level-Domäne `T`.
2. Untergeordnete Verzeichnisknoten wie `dir(S)` verwalten Subdomänen (z. B. `S ⊂ T`).
3. Blattknoten repräsentieren lokale Domänen mit konkreten [[Entität|Entitäten]].

Beispiel-Auflösung:
- Ein Client sucht die [[Adresse]] der [[Entität]] mit dem [[Bezeichner]] `E`.
- Die Anfrage wird an `dir(T)` gesendet, der sie an `dir(S)` weiterleitet.
- `dir(S)` findet die lokale [[Adresse]] von `E` und gibt sie zurück.
