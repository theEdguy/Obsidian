---
id: 7e60ea31-55de-48f2-b869-66a043861721
title: "Single-Thread-Prozesse"
date: 2026-06-01
tags:
  - verteilte_systeme
  - prozesse
  - threads
  - verteilte-systeme
  - kontextwechsel
  - e-a-operationen
  - skalierbarkeit
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Single-Thread-Prozesse]]

- **Kernkonzept:** Ein [[Prozess|Single-Thread-Prozess]] besteht aus genau einem [[Thread]], der alle [[Instruktion|Instruktionen]] im [[Kontext]] des [[Prozess|Prozesses]] sequenziell ausführt. Er nutzt keinen parallelen [[Kontrollfluss]] innerhalb desselben Adressraums.
- **Nutzen & Zweck:** Single-Thread-Prozesse vereinfachen die [[Programmierung]] und [[Synchronisation]], da keine [[Race Condition|Race Conditions]] oder [[Deadlock|Deadlocks]] durch konkurrierende [[Thread|Threads]] auftreten. Sie lösen das [[Problem]] der [[Komplexität]] bei [[E/A-Operation|E/A-Operationen]], indem sie blockierende Aufrufe ohne Unterbrechung abarbeiten – allerdings auf Kosten der [[Parallelität]].
- **Abgrenzung & Grenzen:** Nicht geeignet für [[Anwendung|Anwendungen]], die [[Parallelität]] oder [[Skalierbarkeit]] auf [[Multicore-Prozessor|Multicore-Prozessoren]] benötigen. Im Vergleich zu [[Multi-Thread-Prozess|Multi-Thread-Prozessen]] blockieren sie bei [[E/A-Operation|E/A-Operationen]] vollständig und können [[Netzwerklatenz]] nicht verstecken. Alternativen wie [[Endlicher Automat|Endliche Automaten]] oder [[Event Loop|Event Loops]] vermeiden Blockaden, erfordern aber nicht-blockierende [[Systemaufruf|Systemaufrufe]].
- **Beispiel / Code:** ```c
// Beispiel: Single-Thread-Dateiserver (blockierend)
while (1) {
    request = accept_connection();  // Blockiert bis Anfrage eintrifft
    data = read_file(request);     // Blockiert bei Festplattenzugriff
    send_response(data);           // Blockiert bis Übertragung fertig
}
```

*Erläuterung*: Der Server verarbeitet Anfragen sequenziell. Bei Festplattenzugriff (z. B. 60 ms) bleibt der [[Prozess]] blockiert und kann keine weiteren Anfragen bearbeiten.
