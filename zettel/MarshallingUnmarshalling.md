---
id: 89db1cae-880f-4527-83af-1b420694b601
title: "Marshalling/Unmarshalling"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - datenrepräsentation
  - verteilte-systeme
  - middleware
  - serialisierung
  - netzwerk
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Marshalling/Unmarshalling]]

- **Kernkonzept:** Unter [[Marshalling]] versteht man das Umwandeln von Datenstrukturen oder Objekten in ein [[Format|Formate]], das für die Übertragung oder Speicherung geeignet ist. [[Unmarshalling]] bezeichnet den umgekehrten Prozess, bei dem die übertragenen Daten wieder in ihre ursprüngliche [[Struktur|Strukturen]] zurückgeführt werden.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der heterogenen Datenrepräsentation in [[verteilten System|verteilten Systemen]]. Es ermöglicht die Kommunikation zwischen [[System|Systemen]] mit unterschiedlichen [[Architektur|Architekturen]] oder [[Programmiersprache|Programmiersprachen]], indem Daten in ein standardisiertes [[Format]] überführt werden, das von allen [[Kommunikationspartner|Kommunikationspartnern]] interpretiert werden kann.
- **Abgrenzung & Grenzen:** Marshalling/Unmarshalling sollte nicht genutzt werden, wenn die Kommunikation zwischen homogenen Systemen stattfindet, die dieselbe Datenrepräsentation verwenden, da der Overhead der Umwandlung unnötig ist. Alternativen wie direkte [[Speicher|Speicher]]-Kopien oder [[Serialisierung]] ohne Typkonvertierung können hier effizienter sein. Zudem ist es für Echtzeit-Systeme mit strengen Latenzanforderungen oft ungeeignet.
- **Beispiel / Code:** Ein Beispiel in Python mit dem `json`-Modul:

```python
import json

# Marshalling: Python-Dictionary in JSON-String umwandeln
daten = {"name": "Alice", "alter": 30}
json_string = json.dumps(daten)
print(json_string)  # Ausgabe: '{"name": "Alice", "alter": 30}'

# Unmarshalling: JSON-String zurück in Python-Dictionary
zurueckgewandelt = json.loads(json_string)
print(zurueckgewandelt)  # Ausgabe: {'name': 'Alice', 'alter': 30}
```

In verteilten Systemen könnte ein RPC-Stub diese Schritte automatisch durchführen, um Parameter zwischen Client und Server zu übertragen.
