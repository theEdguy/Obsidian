---
id: 4bbf9cb9-3037-4898-84ed-ea611a723705
title: "Entfernte Referenzen"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - rpc
  - datenverwaltung
  - netzwerkkommunikation
  - transparenz
  - stubs
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Entfernte Referenzen]]

- **Kernkonzept:** Entfernte Referenzen ermöglichen einen uniformen Zugriff auf [[Daten|Datenobjekte]] in [[Verteilte Systeme|verteilten Systemen]], indem sie als Parameter in [[Remote Procedure Call|RPCs]] übergeben werden können. Sie verbessern die [[Zugriffstransparenz]] im Vergleich zu reiner [[Copy-in/Copy-out-Semantik]].
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der eingeschränkten [[Zugriffstransparenz]] bei [[Remote Procedure Call|RPCs]], wo [[Referenz|Referenzen]] auf [[globale Daten]] nicht direkt übergeben werden können. Entfernte Referenzen ermöglichen die [[Übergabe]] von [[Datenstrukturen]] über [[Systemgrenzen]] hinweg, ohne vollständige Kopien zu erstellen.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Latenz]] oder [[Netzwerkstabilität]] kritisch sind, da entfernte Referenzen zusätzliche [[Kommunikationsschritte]] erfordern. Alternativen wie [[Serialisierung]] oder [[Copy-in/Copy-out-Semantik]] sind einfacher, aber weniger flexibel. Unterscheidet sich von [[lokalen Referenzen]] durch die Notwendigkeit von [[Stub|Stubs]] oder [[Proxy|Proxies]] zur [[Vermittlung]].
- **Beispiel / Code:** In einem [[DCE RPC|DCE-RPC-System]] könnte ein Client eine entfernte Referenz auf ein [[Datenobjekt]] auf dem Server erhalten:

```c
// Server-seitige Definition (IDL)
interface Example {
    void modifyData([in, out] remote_ref<int> dataRef);
}

// Client-seitiger Aufruf
remote_ref<int> ref = getRemoteReference(serverData);
modifyData(ref); // Übergabe der entfernten Referenz
```

*Anmerkung: Stubs dienen hier als Vermittler für die entfernte Referenz.*
