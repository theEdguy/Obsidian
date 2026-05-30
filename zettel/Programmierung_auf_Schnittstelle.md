---
id: 7aee5838-1d7f-4dc1-84d0-d37758d1bc06
title: "Programmierung_auf_Schnittstelle"
date: 2026-05-30
tags:
  - software_engineering
  - design_principle
  - oop
  - entkopplung
  - draft
source: "SWE Slides (Folien 316-330)"
---

# [[Programmierung_auf_Schnittstelle]]

- **Kernkonzept:** Die [[Programmierung_auf_Schnittstelle]] ist ein [[Designprinzip]], bei dem [[Klasse|Klassen]] gegen [[Schnittstelle|Schnittstellen]] statt gegen konkrete Implementierungen programmiert werden. Dies fördert [[Lose_Kopplung]] und [[Flexibilität]].
- **Nutzen & Zweck:** Sie löst das Problem der engen Kopplung zwischen [[Klasse|Klassen]] und ermöglicht die einfache Austauschbarkeit von [[Implementierung|Implementierungen]] zur Laufzeit. Dies verbessert die [[Testbarkeit]] und [[Erweiterbarkeit]] des [[Systems]].
- **Abgrenzung & Grenzen:** Nicht sinnvoll, wenn die [[Schnittstelle]] nur eine einzige Implementierung hat oder wenn die [[Komplexität]] durch zusätzliche [[Abstraktion|Abstraktionen]] unnötig erhöht wird.
- **Beispiel / Code:** ```java
// Client nutzt Schnittstelle, nicht Implementierung
public class MemberService {
    private final MemberRepository repository;
    
    public MemberService(MemberRepository repository) {
        this.repository = repository;
    }
    
    public void addMember(Member member) {
        repository.save(member);
    }
}
```
