---
id: 0f2cbe7e-ba1f-43e9-bcd4-fb413bd1c973
title: "Bindung von Namen und Adressen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - namensauflösung
  - netzwerk
  - skalierbarkeit
  - dht
  - mobilität
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Bindung von Namen und Adressen]]

- **Kernkonzept:** Die Bindung von [[Name|Namen]] und [[Adresse|Adressen]] ermöglicht die [[Auflösung|Auflösung]] eines benutzerfreundlichen [[Bezeichner|Bezeichners]] in eine technische [[Adresse]], um auf [[Entität|Entitäten]] in [[Verteiltes System|verteilten Systemen]] zuzugreifen.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der Diskrepanz zwischen benutzerfreundlichen [[Bezeichner|Bezeichnern]] (z. B. Domain-Namen) und technischen [[Adresse|Adressen]] (z. B. IP-Adressen). Es ermöglicht die [[Lokalisierung]] von [[Entität|Entitäten]] in [[Verteiltes System|verteilten Systemen]] und unterstützt [[Mobilität]] sowie [[Skalierbarkeit]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Bezeichner]] keine eindeutige [[Bindung]] erfordern oder wenn die [[Auflösung]] in Echtzeit mit minimaler Latenz erfolgen muss (z. B. in lokalen Netzwerken mit [[Broadcasting]]). Alternativen wie [[Broadcasting]] oder direkte [[Adressierung]] sind einfacher, skalieren aber schlecht. [[Hierarchische Ansätze]] (z. B. DNS) sind komplexer, aber besser für große Systeme geeignet.
- **Beispiel / Code:** Ein einfaches [[Namenssystem]] als Tabelle:
```
{
  "www.example.com": "93.184.216.34",
  "mail.example.com": "93.184.216.35"
}
```
In [[Chord]] (DHT) wird ein [[Schlüssel]] (z. B. Hash eines Namens) einem [[Knoten]] zugeordnet, der die [[Adresse]] der [[Entität]] speichert.
