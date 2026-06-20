---
id: 6805231b-1e94-508d-ae7d-d996e8f25464
title: "User-Space- vs. Kernel-Space-Threads"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_3
  - draft
source: "Kapitel 3: Prozesse"
---

# [[User-Space- vs. Kernel-Space-Threads]]

- **Kernkonzept:** User-Space-Threads werden komplett in einer Bibliothek ohne BS-Hilfe verwaltet (sehr schnell, blockiert aber bei E/A den ganzen Prozess). Kernel-Space-Threads werden vom OS verwaltet (jede Operation erfordert Systemaufruf, aber blockierende E/A blockiert nur den einzelnen Thread).
- **Nutzen & Zweck:** User-Space-Threads werden komplett in einer Bibliothek ohne BS-Hilfe verwaltet (sehr schnell, blockiert aber bei E/A den ganzen Prozess). Kernel-Space-Threads werden vom OS verwaltet (jede Operation erfordert Systemaufruf, aber blockierende E/A blockiert nur den einzelnen Thread).
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
