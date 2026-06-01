---
id: dfa890bc-f1b8-4aad-9d04-321d5343ac7a
title: "Replikation"
date: 2026-06-01
tags:
  - verteilte_systeme
  - datenhaltung
  - fehlertoleranz
  - koordination
  - datenmanagement
  - zuverlässigkeit
  - skalierbarkeit
  - verfügbarkeit
  - konsistenz
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Replikation]]

- **Kernkonzept:** Unter [[Replikation]] versteht man das Erstellen und Verwalten mehrerer [[Kopie|Kopien]] von [[Daten]] oder [[Dienst|Diensten]] auf mehreren [[Knoten]] oder [[Maschine|Maschinen]] in einem [[verteilten System]], um [[Verfügbarkeit]], [[Ausfalltoleranz]] und [[Fehlertoleranz]] zu erhöhen. Dies kann sowohl als temporäres [[Caching]] als auch als dauerhafte Replikation in [[verteilte_Datenbank|verteilten Datenbanken]] umgesetzt werden.
- **Nutzen & Zweck:** [[Replikation]] erhöht die [[Ausfallsicherheit]] und [[Performance]] eines [[verteilten Systems]], indem [[Daten]] oder [[Dienst|Dienste]] redundant an mehreren [[Ort|Orten]] gespeichert oder bereitgestellt werden. Dadurch wird [[Datenverlust]] bei [[Knoten]]-Ausfällen verhindert, die [[Leseperformance]] durch Verteilung von Anfragen auf mehrere [[Replikat|Replikate]] verbessert und [[Lastverteilung]] ermöglicht. Zudem reduziert sie die [[Latenz]] durch lokale Verfügbarkeit von [[Daten]] und verhindert [[Single_Point_of_Failure|Single Points of Failure]].
- **Abgrenzung & Grenzen:** [[Replikation]] führt zu höherem [[Speicherbedarf]] und erhöht die Komplexität der [[Synchronisation]] von [[Daten]], insbesondere bei der Sicherstellung von [[Konsistenz]]. Im Vergleich zu [[zentralisierten Systemen]] ist die Verwaltung aufwendiger, da Mechanismen zur [[Konsistenz]]-Sicherung (z. B. [[Konsistenzmodell|Konsistenzmodelle]] wie [[Starke_Konsistenz]] oder [[Eventuelle_Konsistenz]]) implementiert werden müssen. [[Konsistenzproblem|Konsistenzprobleme]] entstehen, wenn [[Änderung|Änderungen]] nicht synchronisiert werden, und globale [[Synchronisation]] kann die [[Skalierbarkeit]] beeinträchtigen. Nicht geeignet ist [[Replikation]] für Anwendungen, die strenge [[Konsistenz]] erfordern, wie z. B. [[Banktransaktion|Banktransaktionen]], da der [[Overhead]] für die Synchronisation die [[Performance]] beeinträchtigen kann.
- **Beispiel / Code:** Ein typisches Beispiel für [[Replikation]] ist ein [[verteilte Datenbank|verteiltes Datenbanksystem]] wie Cassandra, das [[Daten]] auf mehrere [[Server]] repliziert, um [[Ausfalltoleranz]] und [[Leseperformance]] zu verbessern. Auch Websites werden häufig auf mehrere [[Server]] repliziert, um [[Lastverteilung]] zu ermöglichen und [[Ausfall|Ausfälle]] zu vermeiden.

```java
// Beispiel: Konfiguration der Replikationsfaktor in Cassandra
CREATE KEYSPACE mein_keyspace
WITH REPLICATION = {
  'class': 'SimpleStrategy',
  'replication_factor': 3
};
```

In diesem Beispiel wird ein [[Keyspace]] mit einem [[Replikationsfaktor]] von 3 erstellt, was bedeutet, dass jede [[Daten]]-Partition auf drei [[Knoten]] repliziert wird.
