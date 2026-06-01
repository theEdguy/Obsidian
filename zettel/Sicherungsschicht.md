---
id: d104f4d1-b185-49d5-b33a-24eb42f0b4d8
title: "Sicherungsschicht"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - kommunikation
  - osi-modell
  - hardware
  - fehlertoleranz
  - protokoll
  - datenübertragung
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Sicherungsschicht]]

- **Kernkonzept:** Die Sicherungsschicht ist die zweite [[Schicht|Schicht]] im [[OSI-Referenzmodell]] und ermöglicht die fehlerfreie Übertragung von [[Bit|Bits]] als [[Frame|Frames]] zwischen direkt verbundenen [[Knoten|Knoten]] in einem [[Netzwerk]]. Sie implementiert [[Fehlererkennung]] und [[Flusskontrolle]] auf [[Hardware]]-Ebene.
- **Nutzen & Zweck:** Sie löst das Problem der [[Datenintegrität]] und [[Übertragungszuverlässigkeit]] auf [[Hardware]]-naher Ebene, indem sie [[Bitfehler]] erkennt, korrigiert und den [[Datenfluss]] zwischen [[Sender]] und [[Empfänger]] synchronisiert. Ohne sie wäre eine stabile [[Kommunikation]] in [[verteilten Systemen]] unmöglich.
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Ende-zu-Ende]]-Kommunikation über mehrere [[Netzwerksegmente]] (hierfür ist die [[Vermittlungsschicht]] zuständig). Unterscheidet sich von der [[Bitübertragungsschicht]] durch zusätzliche [[Logik]] für [[Fehlerbehandlung]] und [[Flusssteuerung]], während letztere nur die physische Übertragung von [[Bit|Bits]] übernimmt. Für [[Anwendungen]] ist sie zu [[Hardware]]-nah und bietet keine [[Abstraktion]] wie die [[Transportschicht]].
- **Beispiel / Code:** Ein typisches Beispiel ist das **Ethernet-Protokoll (IEEE 802.3)**, das auf der Sicherungsschicht arbeitet:

```
Frame-Format (vereinfacht):
| Präambel (7 Byte) | SFD (1 Byte) | Ziel-MAC (6 Byte) | Quelle-MAC (6 Byte) | Typ/Länge (2 Byte) | Nutzdaten (46-1500 Byte) | FCS (4 Byte) |
```

- **FCS (Frame Check Sequence)**: 32-Bit-CRC zur [[Fehlererkennung]].
- **Flusskontrolle**: Durch Mechanismen wie **CSMA/CD** (bei klassischem Ethernet) oder **Switching** (bei modernen Netzen).
