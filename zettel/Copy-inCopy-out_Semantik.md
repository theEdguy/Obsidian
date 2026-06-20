---
id: db1030bf-0675-598d-9d63-09f205eb4478
title: "Copy-in/Copy-out Semantik"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_4
  - draft
source: "Kapitel 4: Kommunikation"
---

# [[Copy-in/Copy-out Semantik]]

- **Kernkonzept:** Auch 'Call-by-Value-Result'. RPC-Parameterübergabe, bei der Argumente beim Aufruf kopiert (Copy-in) und bei Rückkehr zurückkopiert (Copy-out) werden. Da keine echten Speicherreferenzen übertragen werden können, weicht das Verhalten bei Aliasing-Aufrufen wie incr(i,i) von lokaler Referenzübergabe ab, was die Zugriffstransparenz einschränkt.
- **Nutzen & Zweck:** Auch 'Call-by-Value-Result'. RPC-Parameterübergabe, bei der Argumente beim Aufruf kopiert (Copy-in) und bei Rückkehr zurückkopiert (Copy-out) werden. Da keine echten Speicherreferenzen übertragen werden können, weicht das Verhalten bei Aliasing-Aufrufen wie incr(i,i) von lokaler Referenzübergabe ab, was die Zugriffstransparenz einschränkt.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
# incr(i,i) mit i=0 anfangs:
# Lokal (Referenz): i wird zweimal inkrementiert -> i = 2
# RPC (Copy-in/Copy-out): i wird kopiert (0, 0), lokal inkrementiert (1, 1), bei Rückgabe wird i nacheinander mit 1 überschrieben -> i = 1
```
