---
id: 7b4cc78f-170f-4bb6-993d-3f3ca69cf67c
title: "Index Server"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - koordination
  - peer-to-peer
  - suche
  - metadaten
  - hybride-systeme
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Index Server]]

- **Kernkonzept:** Ein [[Index Server]] ist ein zentraler oder semi-zentraler Knoten in [[Peer-to-Peer-System|Peer-to-Peer-Systemen]], der Metadaten oder [[Verweis|Verweise]] auf [[Ressource|Ressourcen]] speichert, um die [[Suche|Suche]] und [[Koordination]] effizienter zu gestalten.
- **Nutzen & Zweck:** Der [[Index Server]] löst das [[Problem]] ineffizienter [[Suche|Suchanfragen]] in unstrukturierten [[Peer-to-Peer-System|Peer-to-Peer-Systemen]], indem er eine zentrale [[Anlaufstelle]] für [[Metadaten]] bereitstellt. Dadurch wird die [[Performanz]] erhöht und die [[Netzwerkbelastung]] reduziert, da nicht jeder [[Knoten]] bei jeder [[Anfrage]] durchsucht werden muss.
- **Abgrenzung & Grenzen:** Ein [[Index Server]] sollte nicht genutzt werden, wenn vollständige [[Dezentralisierung]] erforderlich ist, da er einen [[Single Point of Failure]] darstellen kann. Alternativen wie [[Flooding]] oder [[Random Walk]] in unstrukturierten [[Netzwerk|Netzwerken]] sind robuster, aber weniger effizient. In [[Super-Peer-Netzwerk|Super-Peer-Netzwerken]] wird die [[Symmetrie]] des [[Systems]] durchbrochen, was zu [[Skalierbarkeitsproblem|Skalierbarkeitsproblemen]] führen kann.
- **Beispiel / Code:** Ein einfaches Beispiel für einen [[Index Server]] in einem [[Peer-to-Peer-System]]:

1. Ein [[Knoten]] registriert eine [[Datei]] beim [[Index Server]] mit Metadaten (z. B. Dateiname, Hash, Speicherort).
2. Ein anderer [[Knoten]] fragt den [[Index Server]] nach der [[Datei]] ab und erhält eine Liste von [[Knoten]], die die [[Datei]] besitzen.
3. Die [[Datei]] wird direkt zwischen den [[Knoten]] ausgetauscht, ohne den [[Index Server]] weiter zu belasten.

Pseudocode für eine Suchanfrage:
```
function sucheDatei(dateiname):
    ergebnis = indexServer.frageAn(dateiname)
    if ergebnis:
        return ergebnis.knotenListe
    else:
        return "Datei nicht gefunden"
```
