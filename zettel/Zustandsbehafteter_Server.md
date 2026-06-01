---
id: d6e14100-b32c-4e90-a373-eeb221c0a86f
title: "Zustandsbehafteter Server"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - server-architektur
  - zustandsverwaltung
  - netzwerkprotokolle
  - performanzoptimierung
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Zustandsbehafteter Server]]

- **Kernkonzept:** Ein [[zustandsbehafteter|zustandsbehafteter]] [[Server]] verwaltet den [[Zustand]] seiner [[Client|Clients]] über mehrere [[Anfrage|Anfragen]] hinweg, um effizientere [[Interaktion|Interaktionen]] und [[Leistungsoptimierung|Leistungsoptimierungen]] zu ermöglichen.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] ineffizienter [[Kommunikation]] und wiederholter [[Datenübertragung]] zwischen [[Client]] und [[Server]]. Durch das Speichern von [[Zustand|Zuständen]] (z. B. geöffnete [[Datei|Dateien]] oder [[Cache|Caches]]) kann der [[Server]] [[Antwortzeit|Antwortzeiten]] verkürzen, [[Netzwerkverkehr]] reduzieren und [[Benutzererfahrung|Benutzererfahrungen]] verbessern.
- **Abgrenzung & Grenzen:** Nicht nutzen, wenn [[Ausfallsicherheit]] oder [[Skalierbarkeit]] Priorität haben, da [[Zustandsverlust]] die [[Funktionalität]] beeinträchtigen kann. Im Gegensatz zu [[zustandslosen|zustandslosen]] [[Servern]] erfordert es [[Wiederherstellungsmechanismen]] nach [[Ausfall|Ausfällen]] und ist anfälliger für [[Inkonsistenz|Inkonsistenzen]]. Geeignet für [[Systeme]] mit hoher [[Lokalität]] der [[Daten]] und stabilen [[Client-Server-Beziehungen]].
- **Beispiel / Code:** Ein [[Dateiserver]] speichert, welche [[Datei|Dateien]] ein [[Client]] geöffnet hat und welche [[Datenblock|Datenblöcke]] bereits im [[Cache]] liegen. Bei erneuter [[Anfrage]] kann er vorausschauend [[Daten]] laden:

```
class StatefulFileServer {
    private Map<ClientID, Set<FileHandle>> openFiles;
    private Map<ClientID, Set<DataBlock>> cachedBlocks;

    public DataBlock read(ClientID client, FileHandle file, long offset) {
        if (cachedBlocks.get(client).contains(blockAt(offset))) {
            return cachedBlocks.get(client).get(blockAt(offset));
        }
        DataBlock block = preloadNextBlocks(file, offset);
        cachedBlocks.get(client).add(block);
        return block;
    }
}
```
