---
id: 51617934-8a90-4cc4-ab7d-28d7098d7058
title: "Datenrepräsentation (Byte-Ordnung)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - kommunikation
  - datenrepräsentation
  - netzwerkprotokolle
  - middleware
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Datenrepräsentation (Byte-Ordnung)]]

- **Kernkonzept:** Die [[Datenrepräsentation|Datenrepräsentationen]] (Byte-Ordnung) beschreibt, wie numerische [[Wert|Werte]] in einer [[Bytefolge|Bytefolge]] gespeichert werden, insbesondere die Reihenfolge der [[Byte|Bytes]] bei [[Mehrbyte-Datentyp|Mehrbyte-Datentypen]] wie [[Integer]] oder [[Float]].
- **Nutzen & Zweck:** Sie löst das [[Problem]] der [[Inkompatibilität]] zwischen [[System|Systemen]] mit unterschiedlicher [[Hardware]]-Architektur, indem sie eine einheitliche [[Repräsentation]] für den [[Datenaustausch]] in [[verteilten Systemen]] definiert. Ohne sie wären [[Nachricht|Nachrichten]] zwischen [[Client]] und [[Server]] nicht korrekt interpretierbar.
- **Abgrenzung & Grenzen:** Nicht relevant, wenn [[Daten]] nur lokal auf einem [[System]] mit homogener Architektur verarbeitet werden. Alternativen wie [[Textbasierte Protokolle]] (z. B. JSON, XML) vermeiden das [[Problem]], sind aber weniger effizient für [[Binärdaten]].
- **Beispiel / Code:** Beispiel für Little-Endian vs. Big-Endian:

- Zahl: 0x12345678 (305419896 in Dezimal)
- Big-Endian:    [0x12, 0x34, 0x56, 0x78]
- Little-Endian: [0x78, 0x56, 0x34, 0x12]

Bei falscher Interpretation würde der [[Wert]] als 0x78563412 (2018915346) gelesen werden.
