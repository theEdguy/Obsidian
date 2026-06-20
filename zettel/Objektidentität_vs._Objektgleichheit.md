---
id: d0534119-f913-5029-89c3-426ff08bcac5
title: "Objektidentität vs. Objektgleichheit"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_3
  - draft
source: "Kapitel 3: Objektorientierung – eine durchgängige Sichtweise"
---

# [[Objektidentität vs. Objektgleichheit]]

- **Kernkonzept:** Objektidentität (== in Java/C++): Zwei Referenzen zeigen auf exakt dasselbe Objekt im Speicher. Objektgleichheit (.equals() in Java): Zwei unterschiedliche Objekte besitzen identische Attributwerte.
- **Nutzen & Zweck:** Objektidentität (== in Java/C++): Zwei Referenzen zeigen auf exakt dasselbe Objekt im Speicher. Objektgleichheit (.equals() in Java): Zwei unterschiedliche Objekte besitzen identische Attributwerte.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
String x = new String("test");
String y = new String("test");
System.out.println(x == y);      // false (nicht identisch)
System.out.println(x.equals(y)); // true (gleich)
```
