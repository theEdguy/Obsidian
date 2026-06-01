---
id: bdafe222-83c7-4bbe-aa3c-c58542a7f1d6
title: "Heimatbasierte Ansätze (Home-based Approaches)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - namensauflösung
  - mobilität
  - netzwerk
  - verteilte-systeme
  - adressierung
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Heimatbasierte Ansätze (Home-based Approaches)]]

- **Kernkonzept:** Heimatbasierte Ansätze [[Heimatbasierter Ansatz|ermöglichen]] die [[Namensauflösung]] mobiler [[Entität|Entitäten]] in [[Verteilte Systeme|verteilten Systemen]], indem ein fester [[Heimatstandort]] den aktuellen [[Zugriffspunkt]] der Entität nachverfolgt und [[Client|Clients]] dorthin weiterleitet.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der [[Ortsunabhängigkeit]] bei der [[Adressierung]] mobiler Entitäten, indem es eine stabile [[Heimatadresse]] als Ankerpunkt nutzt. Es vereinfacht die [[Kommunikation]], da [[Client|Clients]] nur die Heimatadresse kennen müssen, während der Heimatstandort die dynamische Weiterleitung übernimmt.
- **Abgrenzung & Grenzen:** Heimatbasierte Ansätze skalieren schlecht bei häufigen [[Ortswechsel|Ortswechseln]] der Entität, da der Heimatstandort zum Flaschenhals wird. Sie sind ungeeignet für Systeme mit hoher Mobilität oder globaler Verteilung, da die [[Latenz]] durch den Umweg über den Heimatstandort steigt. Alternativen wie [[Verteilte Hash-Tabellen]] oder [[Hierarchische Ansätze]] vermeiden diese Probleme durch dezentrale oder strukturierte [[Namensauflösung]].
- **Beispiel / Code:** Mobile IP als klassisches Beispiel:
1. Ein [[Client]] sendet ein Paket an die [[Heimatadresse]] eines mobilen Hosts.
2. Der [[Heimatstandort]] antwortet mit der aktuellen [[Auswärtige Adresse|auswärtigen Adresse]] des Hosts.
3. Der Client tunnelt das Paket zum aktuellen Standort.
4. Folgepakete werden direkt an die auswärtige Adresse gesendet.

Pseudocode für Heimatstandort-Logik:
```
function resolveHomeAddress(entityId):
    if entityId in homeRegistry:
        return foreignAddress[entityId]
    else:
        return None
```
