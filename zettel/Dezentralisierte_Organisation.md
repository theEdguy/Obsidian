---
id: 3b54ad79-45ac-4171-a537-31bd7b321a08
title: "Dezentralisierte Organisation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - dezentralisierung
  - peer-to-peer
  - verteilte-systeme
  - skalierbarkeit
  - suchverfahren
  - overlay-netzwerke
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Dezentralisierte Organisation]]

- **Kernkonzept:** Eine [[Organisation|organisatorische]] Struktur in [[verteilte Systeme|verteilten Systemen]], bei der [[Knoten]] ohne zentrale [[Instanz|Instanzen]] direkt miteinander interagieren, um Ressourcen zu teilen oder Aufgaben zu koordinieren. Typisch sind [[Peer-to-Peer-Systeme|Peer-to-Peer-Systeme (P2P)]], die [[Skalierbarkeit]] und [[Ausfallsicherheit]] durch [[Dezentralisierung]] erhöhen.
- **Nutzen & Zweck:** Löst das Problem der [[Single Point of Failure|Single Points of Failure]] und [[Engpässe|Engpässe]] in [[zentralisierte Systeme|zentralisierten Systemen]], indem es [[Lastverteilung]] und [[Redundanz]] durch direkte [[Knoten|Knoten]]-Interaktion ermöglicht. Ermöglicht robuste [[Datenverteilung]] und [[Ressourcennutzung]] in [[Netzwerke|Netzwerken]] mit dynamischer [[Teilnehmer|Teilnehmerschaft]].
- **Abgrenzung & Grenzen:** Nicht geeignet für Szenarien, die starke [[Konsistenz]] oder deterministische [[Suchanfragen|Suchanfragen]] erfordern, da unstrukturierte P2P-Systeme auf probabilistische [[Suchverfahren]] wie [[Flooding]] oder [[Random Walk]] setzen. Hybride Ansätze (z. B. [[Super-Peer-Netzwerke]]) oder [[strukturierte P2P-Systeme]] (z. B. [[DHT|Distributed Hash Tables]]) sind oft effizienter, wenn [[Performanz]] oder [[Vorhersagbarkeit]] Priorität haben. Unterscheidet sich von [[Client-Server-Architekturen]] durch fehlende zentrale [[Kontrolle]].
- **Beispiel / Code:** Unstrukturiertes P2P-Suchverfahren (Flooding mit TTL-Begrenzung):
```python
class Knoten:
    def __init__(self, id):
        self.id = id
        self.nachbarn = []  # Ad-hoc-Liste von Nachbarn
        self.bekannte_anfragen = set()

    def suche(self, anfrage, ttl):
        if ttl <= 0 or anfrage in self.bekannte_anfragen:
            return False
        self.bekannte_anfragen.add(anfrage)
        if self.lokale_suche(anfrage):
            return True
        for nachbar in self.nachbarn:
            if nachbar.suche(anfrage, ttl - 1):
                return True
        return False
```
*Erläuterung*: Jeder [[Knoten]] leitet die [[Anfrage]] an alle [[Nachbarn]] weiter, bis die [[Time-To-Live (TTL)|TTL]] abgelaufen ist oder die [[Ressource]] gefunden wurde.
