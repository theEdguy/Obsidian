---
id: 3835a55a-ea71-4d7f-84ce-392ca77b5952
title: "Design_Patterns"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - entwurfsmuster
  - draft
source: "SWE Slides (Folien 316-330)"
---

# [[Design_Patterns]]

- **Kernkonzept:** [[Design_Patterns]] sind bewährte [[Lösungsmuster]] für wiederkehrende [[Problem|Probleme]] in der [[Softwareentwicklung]]. Sie beschreiben [[Struktur|Strukturen]] und [[Verhalten]] von [[Klasse|Klassen]], [[Schnittstelle|Schnittstellen]] und deren Beziehungen.
- **Nutzen & Zweck:** Sie lösen das Problem der Wiederverwendung von [[Entwurf|Entwürfen]] und verbessern die [[Wartbarkeit]] und [[Verständlichkeit]] von [[Code]]. Sie ermöglichen die gezielte Umsetzung von Anforderungen wie [[Flexibilität]], [[Austauschbarkeit]] oder [[Wiederverwendbarkeit]].
- **Abgrenzung & Grenzen:** Nicht sinnvoll für triviale [[Problem|Probleme]] oder wenn der [[Aufwand]] für die Implementierung den Nutzen übersteigt. Übermäßiger Einsatz kann zu unnötiger [[Komplexität]] führen.
- **Beispiel / Code:** ```java
// Beispiel für das [[Factory_Pattern]]
public interface MemberFactory {
    Member createMember(String type);
}

public class StandardMemberFactory implements MemberFactory {
    @Override
    public Member createMember(String type) {
        return new StandardMember();
    }
}
```
