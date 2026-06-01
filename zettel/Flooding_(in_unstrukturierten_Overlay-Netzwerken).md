---
id: af4c1b59-7f09-433a-ab5d-49a0dd106c68
title: "Flooding (in unstrukturierten Overlay-Netzwerken)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - peer-to-peer
  - routing
  - suche
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Flooding (in unstrukturierten Overlay-Netzwerken)]]

- **Kernkonzept:** [[Flooding]] ist ein [[Routing]]-Verfahren in [[unstrukturierten Overlay-Netzwerk|unstrukturierten Overlay-Netzwerken]], bei dem eine [[Nachricht]] an alle direkten [[Nachbarn]] eines [[Knoten]] weitergeleitet wird, bis sie ihr Ziel erreicht.
- **Nutzen & Zweck:** Ermöglicht die einfache und robuste [[Suche]] nach Ressourcen in [[Netzwerk|Netzwerken]] ohne zentrale Steuerung. Löst das Problem der [[Datenlokalisierung]] in dynamischen und unstrukturierten Umgebungen.
- **Abgrenzung & Grenzen:** Führt zu hohem [[Netzwerk]]-Traffic und Skalierbarkeitsproblemen, da [[Nachrichten]] unkontrolliert verbreitet werden. Nicht geeignet für große [[Netzwerk|Netzwerke]] mit vielen [[Knoten]].
- **Beispiel / Code:** In [[Gnutella]] wird [[Flooding]] verwendet, um [[Datei|Dateien]] zu suchen: Eine [[Suchanfrage]] wird an alle [[Nachbarn]] weitergeleitet, bis die [[Datei]] gefunden oder ein Abbruchkriterium erreicht ist.
