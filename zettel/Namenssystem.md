---
id: 3aedd381-ffa6-43c9-a8e5-043ce7e3d185
title: "Namenssystem"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - namensauflösung
  - netzwerk
  - skalierbarkeit
  - dht
  - adressierung
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Namenssystem]]

- **Kernkonzept:** Ein [[Namenssystem]] bindet [[Name|Namen]] von [[Entität|Entitäten]] in einem [[Verteiltes System|verteilten System]] an deren [[Adresse|Adressen]] und ermöglicht die [[Namensauflösung]] von benutzerfreundlichen [[Bezeichner|Bezeichnern]] zu technischen Zugriffspunkten.
- **Nutzen & Zweck:** Es löst das [[Problem]] der Abstraktion zwischen nutzerorientierten [[Name|Namen]] und systeminternen [[Adresse|Adressen]], um [[Entität|Entitäten]] ortsunabhängig und effizient lokalisieren zu können. Ohne [[Namenssystem]] müssten [[Client|Clients]] direkte [[Adresse|Adressen]] kennen, was [[Skalierbarkeit]] und [[Flexibilität]] stark einschränkt.
- **Abgrenzung & Grenzen:** Nicht geeignet für Systeme mit extrem dynamischen [[Adresse|Adressen]] (z. B. hochmobile Knoten) oder wenn [[Latenz]] durch [[Namensauflösung]] kritisch ist. Alternativen wie [[Broadcasting]] oder [[Heimatbasierter Ansatz|heimatbasierte Ansätze]] skalieren schlechter, während [[Verteilte Hash-Tabelle|verteilte Hash-Tabellen]] (DHT) komplexer, aber skalierbarer sind. [[Hierarchische Ansätze]] (z. B. DNS) erfordern administrative Struktur.
- **Beispiel / Code:** Beispiel für eine einfache [[Namensauflösung]] in einer Tabelle:
```
{
  "www.example.com": "93.184.216.34",
  "file-server": "192.168.1.100"
}
```

Chord-DHT (vereinfacht):
- [[Knoten]] mit ID `5` sucht Schlüssel `26`.
- Finger-Tabelle von `5`: `[9, 9, 18, 28]`
- Weiterleitung an `28` (nächster [[Knoten]] ≥ `26`), der die [[Adresse]] der [[Entität]] zurückgibt.
