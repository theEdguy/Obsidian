---
id: 678c4592-5641-4944-a843-41ac35dab478
title: "Verzeichnisknoten (Directory Nodes)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - namensauflösung
  - hierarchische_architektur
  - skalierbarkeit
  - netzwerk
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Verzeichnisknoten (Directory Nodes)]]

- **Kernkonzept:** Verzeichnisknoten [[Verzeichnisknoten|Verzeichnisknoten]] sind zentrale Komponenten in hierarchischen [[Namensauflösung|Namensauflösungs]]systemen, die [[Entität|Entitäten]] in verteilten Systemen durch eine strukturierte Baumtopologie lokalisieren. Sie repräsentieren [[Domäne|Domänen]] und ermöglichen die effiziente Auflösung von [[Bezeichner|Bezeichnern]] zu [[Adresse|Adressen]].
- **Nutzen & Zweck:** Verzeichnisknoten [[lösen|lösen]] das Problem der skalierbaren [[Namensauflösung]] in großen verteilten Systemen, indem sie eine hierarchische Organisation von [[Zugriffspunkt|Zugriffspunkten]] ermöglichen. Sie vermeiden die Nachteile flacher Ansätze wie [[Broadcasting]] oder [[Heimatstandort|Heimatstandorten]] (z. B. Single Point of Failure, schlechte geografische Skalierbarkeit) und unterstützen dynamische [[Entität|Entitäten]] mit wechselnden [[Adresse|Adressen]].
- **Abgrenzung & Grenzen:** Verzeichnisknoten [[eignen|eignen sich]] nicht für hochdynamische Systeme mit extrem häufigen [[Adressänderung|Adressänderungen]], da der Verwaltungsaufwand für die Hierarchie steigt. Alternativen wie [[Verteilte Hash-Tabelle|Verteilte Hash-Tabellen]] (z. B. [[Chord]]) sind besser für flache, dezentrale Strukturen geeignet, während [[Broadcasting]] nur in lokalen Netzwerken (LAN) praktikabel ist. Im Vergleich zu [[DNS]] fehlt oft die Standardisierung und globale Integration.
- **Beispiel / Code:** ```plaintext
// Hierarchische Struktur eines Verzeichnisknotensystems (HLS)
Top-Level-Domäne T:
  Verzeichnisknoten dir(T)
    Subdomäne S (in T enthalten):
      Verzeichnisknoten dir(S)
        Blatt-Domäne (z. B. Host mit Bezeichner "user123")
          - Registrierung: dir(S) speichert (user123 → Adresse: 192.168.1.42)
          - Auflösung: Anfrage an dir(T) → Weiterleitung an dir(S) → Rückgabe der Adresse.
```
