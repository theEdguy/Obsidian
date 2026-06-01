---
id: e6d1d733-fbf3-4c46-b56a-fd0b779ad473
title: "Ortsunabhängige Namen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - benennung
  - verteilte-systeme
  - namensauflösung
  - mobilität
  - adressierung
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Ortsunabhängige Namen]]

- **Kernkonzept:** Ein [[ortsunabhängiger Name]] bezeichnet eine [[Entität]] in einem [[verteilten System]], dessen [[Bezeichner]] unabhängig von der [[Adresse]] ihres [[Zugriffspunkt|Zugriffspunkts]] ist. Dies ermöglicht die Trennung von logischer Identifikation und physischer Lokalisierung.
- **Nutzen & Zweck:** Ortsunabhängige Namen lösen das Problem der [[Mobilität]] und [[Dynamik]] in [[verteilten Systemen]], indem sie [[Entitäten]] dauerhaft referenzierbar machen – selbst wenn sich deren [[Zugriffspunkt|Zugriffspunkte]] (z. B. durch Migration oder Replikation) ändern. Sie ermöglichen [[Namensauflösung]] ohne direkte Abhängigkeit von [[Adressen]] und unterstützen so [[Skalierbarkeit]] und [[Flexibilität]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Adressen]] direkt und ohne [[Namensauflösung]] genutzt werden können (z. B. in statischen Systemen mit festen [[Zugriffspunkt|Zugriffspunkten]]). Unterscheidet sich von [[reinen Namen]] oder [[Bezeichnern]] ohne Ortsunabhängigkeit, da diese keine Trennung von Identität und Ort ermöglichen. Alternativen wie [[Broadcasting]] oder [[heima|heimatbasierte Ansätze]] skalieren schlechter oder erfordern feste [[Heimatadressen]].
- **Beispiel / Code:** Beispiel: Mobile IP (vereinfacht)
1. Client sendet Paket an [[ortsunabhängigen Namen]] (z. B. `host.example.com`).
2. [[Namenssystem]] löst den Namen in die [[Heimatadresse]] des Hosts auf (z. B. `192.168.1.100`).
3. [[Heimatstandort]] leitet das Paket an die aktuelle [[Adresse]] des Hosts weiter (z. B. `10.0.0.5`).
4. Folgepakete werden direkt an die aktuelle [[Adresse]] gesendet.

Pseudocode für [[Namensauflösung]]:
```
resolve(name):
    home_addr = dns_lookup(name)  // Auflösung in Heimatadresse
    current_addr = home_location_service(home_addr)  // Abfrage aktueller Adresse
    return current_addr
```
