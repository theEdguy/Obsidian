---
id: 90059877-d133-4e93-9758-52f7101bc4fe
title: "HLS: Suche"
date: 2026-06-02
tags:
  - verteilte_systeme
  - verteilte-systeme
  - namensaufloesung
  - hierarchische-strukturen
  - baum-algorithmen
  - netzwerk-koordination
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[HLS: Suche]]

- **Kernkonzept:** Die [[HLS|Hierarchisch-Lokale-Suche]] ist ein Verfahren zur [[Adressauflösung|Adressauflösungen]] in [[verteilte Systeme|verteilten Systemen]], bei dem die Suche nach einer [[Entität]] in einem [[Baum|baumartigen]] [[Namensraum]] beginnt und sich bei Misserfolg nach oben zur [[Wurzel]] fortsetzt.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der effizienten Lokalisierung von [[Entität|Entitäten]] in hierarchisch organisierten [[Namensräume|Namensräumen]], indem es die Suche lokal startet und nur bei Bedarf auf höhere Ebenen ausweitet. Es reduziert die [[Latenz]] und den [[Netzwerkverkehr]] im Vergleich zu flachen [[Benennung|Benennungsverfahren]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Namensräume]], die häufige Änderungen aufweisen oder keine hierarchische Struktur besitzen. Im Vergleich zu [[iterative Namensauflösung|iterativen]] oder [[rekursive Namensauflösung|rekursiven]] Verfahren ist HLS weniger flexibel, wenn die [[Entität|Entitäten]] dynamisch zwischen Knoten wechseln. Alternativen wie [[DNS]] nutzen oft andere Mechanismen für globale Skalierbarkeit.
- **Beispiel / Code:** Beispiel einer Suchanfrage in einem HLS-Baum:
1. Starte bei lokalem Blattknoten M (z. B. Domäne D).
2. Falls M die Entität E kennt: Folge dem Zeiger zum Kindknoten mit E.
3. Falls M E nicht kennt: Gehe zum Elternknoten und wiederhole Schritt 2.
4. Die Suche endet spätestens an der Wurzel, die alle Entitäten kennt.

Pseudocode:
```
function suche_hls(knoten, entitaet):
    if entitaet in knoten.eintraege:
        return knoten.zeiger[entitaet]
    else if knoten.ist_wurzel:
        return "Entität nicht gefunden"
    else:
        return suche_hls(knoten.elternknoten, entitaet)
```
