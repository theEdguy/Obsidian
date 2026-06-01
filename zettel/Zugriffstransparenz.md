---
id: 67a01905-a299-444a-ac46-57fc534a4154
title: "Zugriffstransparenz"
date: 2026-06-01
tags:
  - verteilte_systeme
  - transparenz
  - middleware
  - client_server
  - netzwerk
  - kommunikation
  - rpc
  - abstraktion
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Zugriffstransparenz]]

- **Kernkonzept:** Zugriffstransparenz verbirgt in [[Verteiltes_System|verteilten Systemen]] die Unterschiede in der [[Repräsentation|Repräsentationen]] und [[Zugriffsmethode|Zugriffsmethoden]] von [[Ressource|Ressourcen]], sodass [[Lokaler_Zugriff|lokale]] und [[Entfernter_Zugriff|entfernte]] [[Ressource|Ressourcen]] für den [[Nutzer]] oder [[Programmierer]] identisch erscheinen und die physische Verteilung verborgen bleibt.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der Komplexität in [[Verteiltes_System|verteilten Systemen]], indem es [[Nutzer|Nutzern]] und [[Anwendung|Anwendungen]] ermöglicht, auf [[Ressource|Ressourcen]] einheitlich zuzugreifen – unabhängig davon, ob diese lokal oder remote verfügbar sind. Es abstrahiert [[Ortstransparenz]] und [[Implementierungsdetail|Implementierungsdetails]] der Kommunikation (z. B. [[Netzwerkprotokoll|Netzwerkprotokolle]]), reduziert den [[Programmieraufwand]] und fördert [[Einheitliche_Schnittstelle|einheitliche Schnittstellen]] in [[Client-Server-Architektur|Client-Server-Architekturen]].
- **Abgrenzung & Grenzen:** Zugriffstransparenz ist nicht immer vollständig realisierbar, insbesondere bei [[Remote_Procedure_Call|RPCs]] mit [[Copy-in/Copy-out-Semantik]], da [[Referenzübergabe|Referenzen]] auf [[Globale_Daten|globale Daten]] nicht direkt unterstützt werden. Sie sollte vermieden werden, wenn spezifische [[Eigenschaft|Eigenschaften]] der [[Ressource|Ressourcen]] (z. B. [[Latenz]], [[Bandbreite]] oder [[Sicherheit]]) explizit berücksichtigt werden müssen. Alternativen wie [[Nachrichtenorientierte_Kommunikation]] (z. B. Sockets) bieten weniger Transparenz, aber mehr Kontrolle über [[Netzwerkfehler]] und [[Latenz]]. Andere [[Transparenzart|Transparenzarten]] wie [[Ortstransparenz]] oder [[Migrationstransparenz]] adressieren andere Aspekte der Verteilung, ohne die [[Zugriffsmethode|Zugriffsmethoden]] zu verbergen.
- **Beispiel / Code:** Ein Beispiel für Zugriffstransparenz ist ein [[Remote_Procedure_Call|RPC]]-Stub auf der Client-Seite, der den Aufruf einer entfernten Funktion wie einen lokalen Funktionsaufruf erscheinen lässt. Allerdings zeigt sich bei [[Copy-in/Copy-out-Semantik]] eine Einschränkung der Transparenz:

```c
// Lokale Prozedur: i wird zweimal inkrementiert (Ergebnis: i = 2)
void incr(int &x, int &y) { x++; y++; }
int i = 0;
incr(i, i);  // i = 2

// RPC mit Copy-in/Copy-out: Parameter werden kopiert (Ergebnis: i = 1)
// Client-Stub sendet Kopien von i (0, 0), Server modifiziert diese (1, 1),
// Client erhält zwei separate Kopien (i bleibt 0, wird aber mit 1 überschrieben).
int result = remote_incr(i, i); // i = 1
```

Der Stub übernimmt die Serialisierung der Parameter, den Netzwerktransfer und die Deserialisierung der Antwort, sodass der [[Nutzer]] keine Kenntnis über den entfernten [[Zugriff]] hat.
