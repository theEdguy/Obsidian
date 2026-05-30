---
id: 1df62f0a-0f8b-4d58-b012-449376eb5216
title: "Objektkomposition_vs_Vererbung"
date: 2026-05-30
tags:
  - software_engineering
  - design_principle
  - oop
  - entwurfsmuster
  - draft
source: "SWE Slides (Folien 316-330)"
---

# [[Objektkomposition_vs_Vererbung]]

- **Kernkonzept:** [[Objektkomposition]] ist ein [[Designprinzip]], bei dem [[Funktionalität]] durch die Kombination von [[Objekt|Objekten]] (Komposition) statt durch [[Vererbung]] erreicht wird. Dies ermöglicht [[Flexibilität]] zur Laufzeit.
- **Nutzen & Zweck:** Sie löst das Problem der starren [[Vererbungshierarchie|Vererbungshierarchien]], die zur [[Compile-Zeit]] festgelegt werden und schwer anpassbar sind. [[Objektkomposition]] fördert [[Wiederverwendbarkeit]] und [[Erweiterbarkeit]].
- **Abgrenzung & Grenzen:** Nicht sinnvoll, wenn eine klare [[Ist-ein-Beziehung]] (Vererbung) vorliegt oder wenn die [[Komplexität]] durch zusätzliche [[Objekt|Objekte]] unnötig erhöht wird.
- **Beispiel / Code:** ```java
// Komposition statt Vererbung
public class Member {
    private final MembershipType type;
    
    public Member(MembershipType type) {
        this.type = type;
    }
    
    public void applyDiscount() {
        type.applyDiscount();
    }
}
```
