---
id: 88f89be4-e2b8-44cf-9ed8-74128ed4406a
title: "Bitübertragungsschicht"
date: 2026-06-01
tags:
  - verteilte_systeme
  - netzwerk
  - kommunikation
  - osi-modell
  - hardware
  - protokolle
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Bitübertragungsschicht]]

- **Kernkonzept:** Die Bitübertragungsschicht (engl. [[Physical Layer|Physical Layer]]) ist die unterste Schicht im [[OSI-Referenzmodell|OSI-Referenzmodell]] und definiert die physikalische Übertragung von [[Bit|Bits]] zwischen [[Sender|Sendern]] und [[Empfänger|Empfängern]] über ein [[Übertragungsmedium]].
- **Nutzen & Zweck:** Sie löst das Problem der verlustfreien und standardisierten Übertragung von [[Daten]] auf physikalischer Ebene, indem sie elektrische, optische oder funkbasierte Signale sowie deren Kodierung und Modulation festlegt. Ohne sie wäre keine zuverlässige [[Kommunikation]] in [[verteilten Systemen]] möglich.
- **Abgrenzung & Grenzen:** Die Bitübertragungsschicht sollte nicht genutzt werden, wenn höhere Abstraktionsebenen (z. B. [[Sicherungsschicht]] oder [[Transportschicht]]) bereits die gewünschte Funktionalität bereitstellen. Sie ist rein auf die Signalübertragung beschränkt und bietet keine Fehlererkennung, Flusskontrolle oder logische Adressierung. Alternativen wie [[Middleware]] oder [[Remote Procedure Call|RPC]] arbeiten auf höheren Ebenen und abstrahieren die Hardware-Details.
- **Beispiel / Code:** Ein Beispiel für die Bitübertragungsschicht ist die Spezifikation von Ethernet (IEEE 802.3), die u. a. folgende Parameter definiert:

- Übertragungsmedium: Kupferkabel (z. B. Twisted-Pair) oder Glasfaser
- Signalpegel: Spannungspegel für logische 0 (z. B. -0,85 V) und 1 (z. B. +0,85 V)
- Kodierung: Manchester-Kodierung zur Taktrückgewinnung
- Datenrate: z. B. 100 Mbit/s (Fast Ethernet) oder 1 Gbit/s (Gigabit Ethernet)

Ein vereinfachtes Code-Snippet zur Simulation einer Bitübertragung (Python):
```python
import numpy as np

def manchester_encode(bits):
    encoded = []
    for bit in bits:
        if bit == 1:
            encoded.extend([1, 0])
        else:
            encoded.extend([0, 1])
    return np.array(encoded)

bits = [1, 0, 1, 1, 0]
signal = manchester_encode(bits)
print("Kodierte Bits:", signal)
```
