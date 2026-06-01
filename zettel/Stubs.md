---
id: 18a98922-131e-4c7f-892c-b5af4f64d47c
title: "Stubs"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - rpc
  - netzwerk
  - abstraktion
  - software-architektur
  - kommunikation
  - serialisierung
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Stubs]]

- **Kernkonzept:** Ein [[Stub]] ist eine lokale Repräsentation einer entfernten [[Prozedur|Prozedur]] oder eines entfernten [[Objekt|Objekts]], die die Kommunikation in [[Remote Procedure Call|Remote Procedure Calls (RPCs)]] kapselt und [[Transparenz|Zugriffstransparenz]] ermöglicht. [[Stub|Stubs]] dienen als Vermittler zwischen [[Client]] und [[Server]], indem sie [[Parameter]] serialisieren und deserialisieren.
- **Nutzen & Zweck:** [[Stub|Stubs]] lösen das Problem der [[Komplexität|Komplexität]] in verteilten Systemen, indem sie die technische [[Implementierung]] der [[Netzwerkkommunikation]] vor dem [[Entwickler]] verbergen. Sie ermöglichen die Nutzung entfernter [[Ressource|Ressourcen]] wie lokaler [[Funktion|Funktionen]] und verbessern so die [[Modularität]] und [[Wartbarkeit]] von [[System|Systemen]].
- **Abgrenzung & Grenzen:** [[Stub|Stubs]] sollten nicht genutzt werden, wenn [[Latenz]] oder [[Netzwerküberhead]] kritisch sind, da sie zusätzliche [[Abstraktionsschicht|Abstraktionsschichten]] einführen. Alternativen wie [[Nachrichtenorientierte Kommunikation]] (z. B. [[Socket|Sockets]] oder [[ZeroMQ]]) bieten mehr Kontrolle über die [[Datenübertragung]], erfordern jedoch manuelle Handhabung der [[Serialisierung]] und [[Fehlerbehandlung]]. [[Stub|Stubs]] sind weniger flexibel bei [[asynchroner Kommunikation]] oder [[Multicast]]-Szenarien.
- **Beispiel / Code:** Im [[DCE RPC]]-Beispiel generiert der [[IDL-Compiler]] [[Stub|Stubs]] aus der [[Schnittstellendefinition]]. Der [[Client-Stub]] serialisiert die [[Parameter]] des Aufrufs `incr(i, i)` und sendet sie an den [[Server-Stub]], der die [[Prozedur]] ausführt und das Ergebnis zurückgibt. Bei [[Copy-in/Copy-out-Semantik]] wird `i` nach dem RPC den Wert `2` haben (da beide [[Parameter]] unabhängig kopiert und inkrementiert werden).

Beispiel (Pseudocode):
```
// Client-Stub
void incr_stub(int* a, int* b) {
    serialize(a, b);
    send_to_server();
    receive_result(a, b);
}

// Server-Stub
void incr_skeleton() {
    deserialize(a, b);
    *a += 1; *b += 1;
    serialize(a, b);
    send_to_client();
}
```
