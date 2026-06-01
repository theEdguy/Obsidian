---
id: 015f31d7-9a29-417b-b8b4-6c9ec051ab44
title: "Kodierung von Basistypen und komplexen Typen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - datenrepräsentation
  - rpc
  - middleware
  - netzwerkprotokolle
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Kodierung von Basistypen und komplexen Typen]]

- **Kernkonzept:** Die Kodierung von [[Basistyp|Basistypen]] und [[komplexer Typ|komplexen Typen]] ermöglicht die Transformation von Daten in eine standardisierte [[Bytesequenz|Bytesequenz]], um eine einheitliche Interpretation über heterogene [[System|Systeme]] in [[Verteiltes System|verteilten Systemen]] sicherzustellen.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem|Problem]] der unterschiedlichen [[Datenrepräsentation|Datenrepräsentationen]] (z. B. [[Byteordnung|Byteordnung]]) zwischen [[Client]] und [[Server]] in [[Verteilte Systeme|verteilten Systemen]]. Es gewährleistet, dass [[Nachricht|Nachrichten]] korrekt interpretiert und in maschinenabhängige Formate umgewandelt werden können, insbesondere bei [[Remote Procedure Call|RPC]] oder [[Nachrichtenkommunikation]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[System|Systeme]] bereits eine einheitliche [[Datenrepräsentation]] verwenden oder wenn der Overhead der Kodierung/Dekodierung die [[Performance]] unnötig beeinträchtigt. Alternativen wie [[Binärprotokoll|Binärprotokolle]] (z. B. Protocol Buffers) oder [[Textbasierte Protokolle|textbasierte Protokolle]] (z. B. JSON, XML) können je nach Anwendungsfall effizienter sein.
- **Beispiel / Code:** Beispiel für die Kodierung eines [[Integer|Integers]] (Big-Endian vs. Little-Endian):

- Wert: 4660 (0x1234)
- Big-Endian: [0x12, 0x34]
- Little-Endian: [0x34, 0x12]

Ein [[RPC-Stub]] könnte diese Kodierung wie folgt umsetzen:
```
// Client-Stub (Kodierung)
byte[] encodeInteger(int value) {
    return new byte[] {
        (byte)(value >> 8),
        (byte)(value)
    };
}

// Server-Stub (Dekodierung)
int decodeInteger(byte[] data) {
    return ((data[0] & 0xFF) << 8) | (data[1] & 0xFF);
}
```
