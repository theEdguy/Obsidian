---
id: 0ae3afa6-b97a-40da-9ddb-67db6da7e82a
title: "Klassen-Adapter"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - vererbung
  - adapter
  - draft
source: "SWE Slides (Folien 361-375)"
---

# [[Klassen-Adapter]]

- **Kernkonzept:** Eine Variante des [[Adapter_Pattern|Adapter-Musters]], bei der der Adapter eine [[Unterklasse]] der zu adaptierenden [[Klasse]] (Adaptee) ist und die [[Schnittstelle]] des Clients durch [[Vererbung]] anpasst.
- **Nutzen & Zweck:** Ermöglicht die Anpassung einer bestehenden [[Klasse]] an eine neue [[Schnittstelle]], indem Teile der [[Funktionalität]] des Adaptees überschrieben werden können. Geeignet, wenn nur eine [[Klasse]] angepasst werden muss.
- **Abgrenzung & Grenzen:** Eingeschränkt auf die Anpassung einer einzelnen [[Klasse]] und deren [[Unterklasse|Unterklassen]]. Nicht geeignet, wenn mehrere [[Klasse|Klassen]] oder [[Schnittstelle|Schnittstellen]] angepasst werden müssen. Im Gegensatz zum [[Objekt-Adapter]] nutzt es [[Vererbung]] statt [[Komposition]].
- **Beispiel / Code:** ```java
// Klassen-Adapter
class ClassAdapter extends Adaptee implements Target {
    void targetOp() {
        super.existingOp();
    }
}
```
