---
id: 523fde72-39ce-43d4-a7ce-a7f733a4b821
title: "IDL Compiler"
date: 2026-06-01
tags:
  - verteilte_systeme
  - kommunikation
  - interface_definition
  - codegenerierung
  - rpc
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[IDL Compiler]]

- **Kernkonzept:** Ein [[IDL Compiler|IDL-Compiler]] übersetzt [[Interface Definition Language|IDL-Definitionen]] in [[Stub|Stubs]] und [[Skeleton|Skeletons]], die die Kommunikation in [[Remote Procedure Call|RPCs]] ermöglichen. Er abstrahiert die [[Serialisierung|Serialisierung]] und [[Deserialisierung|Deserialisierung]] von [[Parameter|Parametern]] und [[Datenstruktur|Datenstrukturen]] in verteilten Systemen.
- **Nutzen & Zweck:** Der [[IDL Compiler|IDL-Compiler]] löst das [[Problem]] der manuellen Erstellung von [[Netzwerkprotokoll|Netzwerkprotokollen]] und [[Datenformat|Datenformaten]] für die Kommunikation zwischen [[Client|Clients]] und [[Server|Servern]]. Er automatisiert die Generierung von [[Stub|Stubs]] und [[Skeleton|Skeletons]], die [[Zugriffstransparenz]] und [[Interoperabilität]] zwischen heterogenen Systemen gewährleisten.
- **Abgrenzung & Grenzen:** Ein [[IDL Compiler|IDL-Compiler]] sollte nicht genutzt werden, wenn die Kommunikation zwischen [[Prozess|Prozessen]] lokal oder über einfache [[Nachrichtenorientierte Kommunikation|nachrichtenorientierte Mechanismen]] (z. B. [[Socket|Sockets]]) erfolgt, da der Overhead der [[Stub|Stub]]-Generierung unnötig ist. Alternativen wie [[gRPC]] oder [[REST]] können je nach Anwendungsfall flexibler sein, bieten aber weniger strenge [[Typprüfung|Typprüfungen]] zur [[Kompilierzeit]].
- **Beispiel / Code:** Beispiel einer IDL-Definition (DCE/RPC):
```
interface Example {
    const long MAX = 100;
    void incr([in, out] long *x, [in, out] long *y);
}
```
Der [[IDL Compiler|IDL-Compiler]] generiert daraus [[Client-Stub|Client-Stubs]] und [[Server-Skeleton|Server-Skeletons]] in der Zielsprache (z. B. C), die die [[Parameterübergabe]] mit [[Copy-in/Copy-out Semantik]] umsetzen.
