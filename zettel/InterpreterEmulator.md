---
id: 47b8a1b3-bdcb-45df-9dfb-e1909ecf865a
title: "Interpreter/Emulator"
date: 2026-06-01
tags:
  - verteilte_systeme
  - virtualisierung
  - programmausführung
  - kompatibilität
  - abstraktion
  - systemarchitektur
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Interpreter/Emulator]]

- **Kernkonzept:** Ein [[Interpreter]] führt [[Programm|Programme]] in einer höheren [[Programmiersprache|Programmiersprache]] direkt aus, während ein [[Emulator]] die [[Hardware]]- oder [[Systemumgebung]] eines anderen [[System|Systems]] nachbildet, um [[Software]] auszuführen, die für diese Umgebung entwickelt wurde.
- **Nutzen & Zweck:** Ein [[Interpreter]] ermöglicht die plattformunabhängige Ausführung von [[Code]] ohne vorherige [[Kompilierung]], während ein [[Emulator]] die Kompatibilität von [[Software]] auf nicht-nativer [[Hardware]] oder in virtuellen [[Umgebung|Umgebungen]] sicherstellt. Beide lösen das Problem der [[Portabilität]] und [[Abstraktion]] von [[Systemressource|Systemressourcen]].
- **Abgrenzung & Grenzen:** Ein [[Interpreter]] ist langsamer als [[kompilierter Code]], da er [[Anweisung|Anweisungen]] zur Laufzeit übersetzt. Ein [[Emulator]] verursacht zusätzlichen [[Overhead]], da er [[Hardware]]-Funktionen simuliert, und ist oft ineffizienter als native Ausführung. Alternativen wie [[Kompilierung]] oder [[Hardware-Virtualisierung]] (z. B. [[Hypervisor]]) sind performanter, aber weniger flexibel.
- **Beispiel / Code:** Ein einfacher [[Interpreter]] für eine fiktive Sprache könnte so aussehen:
```python
code = "ADD 5, SUB 3"
stack = []
for token in code.split():
    if token == "ADD":
        stack.append(int(next_token))
    elif token == "SUB":
        stack.append(-int(next_token))
    else:
        next_token = token.strip(",")
print(sum(stack))  # Ausgabe: 2
```

Ein [[Emulator]]-Beispiel wäre die Nachbildung eines [[Prozessor]]-Befehlssatzes in [[Software]], z. B. QEMU für x86- auf ARM-[[Hardware]].
