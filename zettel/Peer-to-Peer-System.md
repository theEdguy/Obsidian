---
id: 74f9e52c-fbe2-48cf-a41b-31c7b9dc3799
title: "Peer-to-Peer Systeme (P2P)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerkarchitektur
  - dezentralisierung
  - overlay_netzwerke
  - suche_algorithmik
  - skalierbarkeit
  - kollaboration
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Peer-to-Peer Systeme (P2P)]]

- **Kernkonzept:** Peer-to-Peer [[System|Systeme]] (P2P) sind dezentrale [[Netzwerk|Netzwerke]], in denen alle [[Knoten|Knoten]] gleichberechtigt agieren und sowohl [[Ressource|Ressourcen]] bereitstellen als auch konsumieren, ohne zentrale [[Instanz|Instanzen]].
- **Nutzen & Zweck:** P2P [[System|Systeme]] lösen das Problem der Skalierbarkeit und [[Ausfallsicherheit|Ausfallsicherheiten]] in verteilten [[Umgebung|Umgebungen]], indem sie [[Last|Lasten]] verteilen und Single-Points-of-Failure vermeiden. Sie ermöglichen effiziente [[Daten|Datenverteilung]] und [[Kollaboration]] ohne zentrale [[Kontrolle]].
- **Abgrenzung & Grenzen:** P2P [[System|Systeme]] sind ungeeignet, wenn starke Konsistenz, zentrale [[Kontrolle]] oder deterministische [[Suche|Suchmechanismen]] erforderlich sind. Im Vergleich zu [[Client-Server-Architektur|Client-Server-Architekturen]] fehlt oft die Vorhersehbarkeit, und [[Sicherheit|Sicherheitsmechanismen]] sind komplexer umzusetzen. Super-Peer [[Netzwerk|Netzwerke]] oder hybride [[Architektur|Architekturen]] können hier Abhilfe schaffen.
- **Beispiel / Code:** Unstrukturiertes P2P mit Flooding-Suche (Pseudocode):

```
function suche(startKnoten, datenId, ttl):
    if ttl <= 0:
        return None
    if startKnoten.hatDaten(datenId):
        return startKnoten
    for nachbar in startKnoten.nachbarn:
        if nachbar.nichtBesucht(datenId):
            ergebnis = suche(nachbar, datenId, ttl - 1)
            if ergebnis:
                return ergebnis
    return None
```
