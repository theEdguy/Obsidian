---
id: 262d7235-c0de-4e92-9cf8-b01644c7f516
title: "Copy-in/Copy-out Semantik"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - rpc
  - parameteruebergabe
  - semantik
  - netzwerkkommunikation
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Copy-in/Copy-out Semantik]]

- **Kernkonzept:** Die Copy-in/Copy-out Semantik beschreibt eine [[Parameterübergabe|Parameterübergaben]]-Methode in [[Remote Procedure Call|RPCs]], bei der alle Daten als Kopien übergeben werden. Während der [[Prozedurausführung|Prozedurausführung]] sind keine Annahmen über [[Parameterwert|Parameterwerte]] möglich, da keine Referenzen auf globale Daten erlaubt sind.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der [[Zugriffstransparenz]] in [[Verteilte Systeme|verteilten Systemen]] durch klare Trennung von Datenkopien. Es verhindert unerwartete [[Nebenwirkung|Nebenwirkungen]] durch Modifikation globaler Daten und vereinfacht die [[Fehlerbehandlung]] in [[RPC|RPCs]].
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn [[Referenz|Referenzen]] auf gemeinsame Daten benötigt werden oder Performance durch Kopieren leidet. Unterscheidet sich von [[Call-by-Reference]] durch fehlende direkte Modifikation der Originaldaten. Alternativen wie entfernte Referenzen bieten mehr [[Zugriffstransparenz]], erhöhen aber die Komplexität.
- **Beispiel / Code:** Beispiel aus der Übung:
```
// Lokale Prozedur mit Referenzübergabe:
void incr(int &a, int &b) { a++; b++; }
int i = 0;
incr(i, i); // i = 2 (Referenzsemantik)

// RPC mit Copy-in/Copy-out:
void incr_rpc(int a, int b) { a++; b++; }
int i = 0;
incr_rpc(i, i); // i bleibt 0 (Kopien werden modifiziert, Original unverändert)
```
