---
id: 3b82aa40-44d3-4768-8d0c-937b9e5b50fe
title: "Zugriffspunkte"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - netzwerk
  - namensauflösung
  - adressierung
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Zugriffspunkte]]

- **Kernkonzept:** Ein [[Zugriffspunkt|Zugriffspunkt]] ist eine [[Entität]] in [[verteilte Systeme|verteilten Systemen]], die mit einer [[Adresse]] benannt wird und den [[Zugriff]] auf eine andere [[Entität]] ermöglicht. Er dient als Schnittstelle, um mit der [[Entität]] zu interagieren, unabhängig von ihrem [[ortsunabhängiger Name|ortsunabhängigen Namen]].
- **Nutzen & Zweck:** [[Zugriffspunkte]] lösen das Problem der [[Namensauflösung]] in [[verteilte Systeme|verteilten Systemen]], indem sie eine technische [[Adresse]] bereitstellen, über die [[Entitäten]] lokalisiert und angesprochen werden können. Sie ermöglichen die Trennung von benutzerfreundlichen [[Bezeichner|Bezeichnern]] und systeminternen [[Adressen]], was die Flexibilität und Skalierbarkeit des Systems erhöht.
- **Abgrenzung & Grenzen:** [[Zugriffspunkte]] sollten nicht verwendet werden, wenn die [[Entität]] keine feste oder dynamisch aktualisierbare [[Adresse]] besitzt, z. B. in hochmobilen oder flüchtigen Netzwerken. Alternativen wie [[Broadcasting]] oder [[verteilte Hash-Tabellen]] (DHT) können in solchen Fällen effizienter sein, sind jedoch weniger skalierbar oder komplexer in der Implementierung. Zudem sind [[Zugriffspunkte]] ungeeignet, wenn die [[Entität]] keine klare Schnittstelle für den [[Zugriff]] bietet.
- **Beispiel / Code:** Beispiel für einen [[Zugriffspunkt]] in Mobile IP:
1. Ein [[Client]] sendet ein Paket an die [[Heimatadresse]] eines mobilen Hosts.
2. Der [[Heimatstandort]] des Hosts antwortet mit der aktuellen [[Adresse]] des Hosts.
3. Der [[Client]] tunnelt das Paket zur aktuellen [[Adresse]] des Hosts.
4. Folgepakete werden direkt an die aktuelle [[Adresse]] gesendet.

Pseudocode für die Namensauflösung in Chord (DHT):
```
function lookup(key, node):
    if key ∈ (node, node.successor]:
        return node.successor
    else:
        next_node = node.closest_preceding_node(key)
        return lookup(key, next_node)
```
