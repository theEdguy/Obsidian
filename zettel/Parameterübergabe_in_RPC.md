---
id: a1af80c8-7b15-45f6-ba83-58fa36d4b7c2
title: "Parameterübergabe in RPC"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - rpc
  - datenrepräsentation
  - middleware
  - netzwerk
  - parameterübergabe
  - netzwerkkommunikation
  - semantik
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Parameterübergabe in RPC]]

- **Kernkonzept:** Die [[Parameterübergabe]] in [[Remote_Procedure_Call|RPCs]] ermöglicht die Transformation von [[Parameter|Parametern]] zwischen unterschiedlichen [[Datenrepräsentation|Datenrepräsentationen]] auf [[Client]]- und [[Server]]-Seite, um [[Prozeduraufruf|Prozeduraufrufe]] über [[Netzwerk|Netzwerke]] hinweg konsistent auszuführen. Dabei wird die [[Copy-in/Copy-out-Semantik]] verwendet, um lokale [[Referenz|Referenzen]] auszuschließen und die [[Zugriffstransparenz]] einzuschränken.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] heterogener [[Datenformat|Datenformate]] in [[Verteilte_Systeme|verteilten Systemen]], indem es eine standardisierte [[Kodierung]] für [[Parameter]] definiert. Dadurch wird die [[Interoperabilität]] zwischen Systemen mit unterschiedlicher [[Architektur]] (z. B. [[Byte-Reihenfolge]]) sichergestellt und die [[Datenkonsistenz]] während der [[Ausführung]] garantiert. Die [[Parameterübergabe]] abstrahiert [[Prozeduraufruf|Prozeduraufrufe]] über Netzwerkgrenzen hinweg und ermöglicht so eine effiziente Kommunikation in verteilten Umgebungen.
- **Abgrenzung & Grenzen:** Die [[Parameterübergabe]] in [[Remote_Procedure_Call|RPCs]] ist nicht geeignet für Szenarien mit häufigen [[Änderung|Änderungen]] globaler Daten oder wenn die [[Latenz]] durch das Kopieren der [[Parameter]] kritisch ist. Alternativen wie [[Nachrichtenorientierte_Kommunikation|nachrichtenorientierte Kommunikation]], [[Entfernte_Referenz|entfernte Referenzen]] oder [[REST]] bieten mehr Flexibilität, erfordern jedoch komplexere [[Koordination]] oder manuelle [[Serialisierung]]. Zudem ist sie ungeeignet für [[Kommunikation|Kommunikationsformen]], die keine [[Prozeduraufruf|Prozeduraufrufe]] benötigen, wie [[Streaming]] oder [[Ereignisgesteuerte_Architektur|ereignisgesteuerte Architekturen]].
- **Beispiel / Code:** ```java
// Beispiel: Marshaling/Unmarshaling in RPC (Pseudocode)
// Client-Seite (Marshaling)
byte[] marshaledParams = RPCStub.marshal("add", intParam1, intParam2);

// Server-Seite (Unmarshaling)
(int a, int b) = RPCStub.unmarshal(marshaledParams);
int result = add(a, b);

// Datenrepräsentation: Big-Endian vs. Little-Endian
// Client (Little-Endian): 0x1234 → [0x34, 0x12]
// Server (Big-Endian):   0x1234 → [0x12, 0x34]

// Beispiel: Copy-in/Copy-out-Semantik
// Prozedur `incr(i, i)` mit `i = 0`:
// - **Lokal (Referenzübergabe):** Ergebnis `i = 2` (beide Parameter referenzieren dieselbe Variable).
// - **RPC (Copy-in/Copy-out):** Ergebnis `i = 1` (jeder Parameter wird unabhängig kopiert und zurückgeschrieben).
```
