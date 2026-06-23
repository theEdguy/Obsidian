---
id: 9465fb7e-f89b-4bf0-bdb1-63407f69ed29
title: "Wiederverwendung"
date: 2026-06-24
tags:
  - software_engineering
  - grundlagen
  - software-architektur
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Wiederverwendung]]

- **Kernkonzept:** Die Nutzung bestehender [[Komponenten]], [[Bibliotheken]] oder [[Muster]] in der [[Software-Entwicklung]], um [[Entwicklungszeit]] und [[Kosten]] zu reduzieren.
- **Nutzen & Zweck:** Erhöht [[Produktivität]] und [[Qualität]] durch Nutzung bewährter [[Lösungen]]. Grundlage für [[Design_Patterns]] und [[Frameworks]].
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Anpassung]], da [[Komponenten]] oft modifiziert werden müssen. Unterscheidet sich von [[Redundanz]] durch Fokus auf [[DRY_Prinzip]]. Nicht sinnvoll bei [[Spezialanforderungen]].
- **Beispiel / Code:** ```java
// Beispiel für Wiederverwendung (Bibliothek)
import org.apache.commons.lang3.StringUtils;

public class TextProcessor {
    public String reverse(String input) {
        return StringUtils.reverse(input);
    }
}
```
