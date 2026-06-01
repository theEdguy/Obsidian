---
id: 7311bf48-0597-45f8-928c-370945ec1887
title: "Mobile IP"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - mobilität
  - benennung
  - protokoll
  - verteilte-systeme
  - ip-adressierung
  - tunneling
  - draft
source: "VS2 Handout Chapter 05 (Benennung)"
---

# [[Mobile IP]]

- **Kernkonzept:** Mobile IP ist ein [[Protokoll|Protokolle]], das die [[Mobilität|mobilen]] [[Endgerät|Endgeräte]] in [[IP-Netzwerk|IP-Netzwerken]] ermöglicht, indem es deren [[Erreichbarkeit]] trotz Standortwechsel durch [[Heimatadresse|Heimatadressen]] und [[Tunneling]] sicherstellt.
- **Nutzen & Zweck:** Es löst das [[Problem]] der [[Unterbrechung|unterbrochenen]] [[Netzwerkverbindung|Netzwerkverbindungen]] bei [[Bewegung|bewegten]] [[Gerät|Geräten]] in [[IP-basiert|IP-basierten]] [[Netzwerk|Netzwerken]], indem es eine [[ortsunabhängige]] [[Adressierung]] ermöglicht. Ohne Mobile IP müssten [[Endgerät|Endgeräte]] bei jedem [[Netzwerkwechsel]] eine neue [[IP-Adresse]] beziehen, was [[Kommunikation|laufende Kommunikationen]] unterbricht.
- **Abgrenzung & Grenzen:** Mobile IP ist nicht geeignet für [[Szenario|Szenarien]], in denen [[Endgerät|Endgeräte]] häufig zwischen vielen kleinen [[Netzwerk|Netzwerken]] wechseln (z. B. Mikro-Mobilität), da der [[Heimatstandort]] zur [[Engpass|Engstelle]] werden kann. Alternativen wie [[Proxy Mobile IP]] oder [[hierarchische]] [[Lösungsansatz|Lösungsansätze]] (z. B. [[Hierarchical Location Services]]) sind hier effizienter. Zudem verursacht das [[Tunneling]] [[Overhead]], der in [[Bandbreite|bandbreitenbeschränkten]] [[Umgebung|Umgebungen]] problematisch sein kann.
- **Beispiel / Code:** Ein typischer Ablauf in Mobile IP:
1. Ein [[Client]] sendet ein [[Datenpaket]] an die [[Heimatadresse]] eines [[mobilen Knoten|mobilen Knotens]].
2. Der [[Heimatstandort]] (Home Agent) erkennt, dass der [[Knoten]] nicht lokal ist, und leitet das [[Paket]] per [[Tunnel]] an die [[auswärtige Adresse]] (Care-of Address) weiter.
3. Der [[auswärtige Standort]] (Foreign Agent) empfängt das [[Paket]] und übergibt es an den [[mobilen Knoten]].
4. Für [[Folgekommunikation|Folgekommunikationen]] sendet der [[Client]] direkt an die [[auswärtige Adresse]].

Pseudocode für die [[Paketweiterleitung]]:
```
if (Zieladresse == Heimatadresse) {
    if (Knoten ist lokal) {
        übergebePaketLokal();
    } else {
        tunnelnZu(auswärtigeAdresse);
    }
}
```
