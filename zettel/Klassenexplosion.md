---
id: d45494f3-9f00-4f70-96ce-c3f1e0fca039
title: "Klassenexplosion"
date: 2026-05-30
tags:
  - software_engineering
  - anti_pattern
  - architektur
  - skalierbarkeit
  - draft
source: "SWE Slides (Folien 361-375)"
---

# [[Klassenexplosion]]

- **Kernkonzept:** [[Klassenexplosion]] beschreibt das unkontrollierte Wachstum der Anzahl von [[Klasse|Klassen]] in einem [[System]], das durch die Kombination mehrerer [[Abstraktion|Abstraktionen]] und [[Implementierung|Implementierungen]] entsteht.
- **Nutzen & Zweck:** Dient als Warnsignal für schlechte [[Architektur]]-Entscheidungen, die zu [[Hohe_Kopplung|hoher Kopplung]], schlechter [[Wartbarkeit]] und [[Skalierbarkeit]]-Problemen führen.
- **Abgrenzung & Grenzen:** Kein [[Entwurfsmuster]], sondern ein Anti-Pattern. Wird durch [[Entwurfsmuster|Muster]] wie [[Bridge_Pattern]] oder [[Strategy_Pattern]] vermieden, die [[Abstraktion]] und [[Implementierung]] trennen.
- **Beispiel / Code:** ```java
// Beispiel für Klassenexplosion
class DESFileCipher { /* ... */ }
class AESFileCipher { /* ... */ }
class DESDirCipher { /* ... */ }
class AESDirCipher { /* ... */ }
// Problem: Jede Kombination erfordert eine neue Klasse
```
