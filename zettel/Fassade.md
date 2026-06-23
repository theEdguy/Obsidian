---
id: bfe92bf7-3ad2-4c4d-b1cd-b488a8f77e00
title: "Fassade"
date: 2026-06-23
tags:
  - software_engineering
  - design_pattern
  - schnittstelle
  - draft
source: "software_engineering_kapitel_13"
---

# [[Fassade]]

- **Kernkonzept:** Eine Fassade ist ein strukturelles Design-Pattern, das eine vereinfachte Schnittstelle zu einem komplexen Subsystem bereitstellt. Sie kapselt die Interaktion mit mehreren Klassen oder Komponenten hinter einer einzigen, leicht verständlichen Schnittstelle.
- **Nutzen & Zweck:** Die Fassade existiert, um die Komplexität eines Systems zu reduzieren, indem sie eine klare und einheitliche Schnittstelle für Clients bereitstellt. Sie löst das Problem der engen Kopplung zwischen Client-Code und Subsystemen, indem sie Abhängigkeiten minimiert und die Wartbarkeit sowie Erweiterbarkeit des Systems verbessert. Zudem erleichtert sie die Nutzung des Subsystems, da Clients nicht alle Details der internen Implementierung kennen müssen.
- **Abgrenzung & Grenzen:** Eine Fassade sollte nicht genutzt werden, wenn das Subsystem einfach strukturiert ist und keine komplexen Interaktionen erfordert, da sie dann unnötigen Overhead erzeugt. Im Gegensatz zu einem Adapter, der bestehende Schnittstellen anpasst, oder einem Mediator, der die Kommunikation zwischen Objekten zentralisiert, dient die Fassade ausschließlich der Vereinfachung des Zugriffs auf ein Subsystem. Sie sollte auch nicht als Ersatz für eine detaillierte API verwendet werden, wenn Clients direkten Zugriff auf die Funktionalität des Subsystems benötigen.
- **Beispiel / Code:** ```java
public interface ManagementFactory {
    ManagementFactory FACTORY = new ManagementFacade();
    
    MemberManagement memberManagement();
    // Weitere Methoden zur Interaktion mit dem Subsystem
}

@ApplicationScope
@Component
class ManagementFacade implements MemberManagement {
    @Autowired
    private StateMachine stateMachine;
    
    @Override
    public void addMember(Member member) {
        stateMachine.validate(member);
        stateMachine.persist(member);
    }
    // Weitere Methoden zur Kapselung der Subsystem-Logik
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1
- **Vorgänger / Parent:** [[Entwurfsmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
