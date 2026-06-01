---
id: f0611296-393a-4498-a079-9362ca9f4b18
title: "Isolation (in verteilten Systemen)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - virtualisierung
  - sicherheit
  - fehlertoleranz
  - parallelität
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Isolation (in verteilten Systemen)]]

- **Kernkonzept:** Isolation bezeichnet in verteilten Systemen die [[Abschottung|Abschottung]] von [[Prozess|Prozessen]], [[Thread|Threads]] oder [[Komponente|Komponenten]], um unerwünschte [[Wechselwirkung|Wechselwirkungen]] (z. B. [[Datenzugriff|Datenzugriffe]] oder [[Fehlerausbreitung|Fehlerausbreitungen]]) zu verhindern und [[Konsistenz|konsistente]] [[Zustand|Zustände]] zu gewährleisten.
- **Nutzen & Zweck:** Isolation löst das Problem der [[Interferenz|Interferenz]] zwischen [[Prozess|Prozessen]] oder [[Dienst|Diensten]] in verteilten Systemen, indem sie [[Fehlerisolation|Fehlerisolierung]], [[Sicherheit]] und [[Parallelität]] ermöglicht. Sie ist essenziell für [[Skalierbarkeit]], [[Fehlertoleranz]] und [[Schutz]] vor [[Angriff|Angriffen]] oder [[Ressourcenkonflikt|Ressourcenkonflikten]].
- **Abgrenzung & Grenzen:** Isolation sollte nicht genutzt werden, wenn enge [[Kooperation]] zwischen [[Komponente|Komponenten]] erforderlich ist (z. B. bei [[Shared-Memory|Shared-Memory]]-Systemen) oder wenn der [[Overhead]] für [[Kontextwechsel]] oder [[Virtualisierung]] die [[Leistung]] unnötig beeinträchtigt. Alternativen wie [[Lock|Locks]] oder [[Transaktion|Transaktionen]] bieten weniger strikte, aber effizientere [[Synchronisation]].
- **Beispiel / Code:** ```java
// Beispiel: Isolation durch Prozessgrenzen in Java (mit ProcessBuilder)
ProcessBuilder pb = new ProcessBuilder("java", "Worker");
Process worker = pb.start(); // Isolierter Prozess mit eigenem Adressraum
// Kommunikation nur über Streams oder IPC (z. B. Sockets)
```

*Erläuterung*: Der `Worker`-Prozess läuft in einer eigenen [[JVM]]-Instanz und ist von [[Speicherzugriff|Speicherzugriffen]] des Hauptprozesses isoliert. [[Fehler]] im `Worker` führen nicht zum Absturz des Hauptprozesses.
