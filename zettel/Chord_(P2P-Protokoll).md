---
id: 56fb6b77-7c31-4502-bfc5-ef54212f10fb
title: "Chord (P2P-Protokoll)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - peer-to-peer
  - hash-tabellen
  - routing
  - skalierbarkeit
  - dezentralisierung
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Chord (P2P-Protokoll)]]

- **Kernkonzept:** Chord ist ein strukturiertes [[Peer-to-Peer-System|Peer-to-Peer-System]], das [[Knoten]] in einem logischen Ring organisiert und durch verteilte [[Hash-Tabellen]] effizientes [[Routing]] und [[Datenverwaltung|Datenverwalten]] in dezentralen [[Netzwerk|Netzwerken]] ermöglicht.
- **Nutzen & Zweck:** Chord löst das Problem der skalierbaren und effizienten [[Datenverwaltung|Datenverwaltung]] in verteilten Systemen, indem es [[Schlüssel]]-basiertes [[Routing]] mit logarithmischer Komplexität ermöglicht. Es vermeidet zentrale [[Index|Indizes]] und ermöglicht robuste [[Suche|Suchoperationen]] auch bei dynamischen [[Knoten]]-Ein- und Austritten.
- **Abgrenzung & Grenzen:** Chord eignet sich nicht für Anwendungen mit stark ungleichmäßiger [[Datenverteilung|Datenverteilung]] oder wenn [[Latenz]]-kritische Echtzeitanforderungen bestehen. Im Vergleich zu unstrukturierten [[Peer-to-Peer-System|Peer-to-Peer-Systemen]] (z. B. Gnutella) erfordert es höhere Wartungskosten für die Ringstruktur, bietet aber garantierte [[Suche|Suchergebnisse]]. Für kleine [[Netzwerk|Netzwerke]] oder zentralisierte [[Architektur|Architekturen]] ist es oft überdimensioniert.
- **Beispiel / Code:** Ein Chord-Ring mit m=5 Bit (Knoten-IDs 0–31):
- Knoten 9 speichert [[Schlüssel]] 5, 6, 7, 8, 9 (Successor-Prinzip).
- Eine [[Suche|Suchanfrage]] für Schlüssel 3 von Knoten 9:
  1. Knoten 9 leitet Anfrage an Knoten 28 weiter (nächster Finger-Eintrag).
  2. Knoten 28 leitet an Knoten 1 weiter.
  3. Knoten 1 leitet an Knoten 4 weiter (Successor von 3).
- Ergebnis: Knoten 4 ist verantwortlich für Schlüssel 3.
