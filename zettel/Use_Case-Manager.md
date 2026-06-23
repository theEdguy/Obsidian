---
id: 8b37861e-10c6-41e1-b218-a7ee064100a6
title: "Use_Case-Manager"
date: 2026-06-23
tags:
  - software_engineering
  - softwarearchitektur
  - use_case
  - design_principle
  - designkonzept
  - verantwortung
  - draft
source: "software_engineering_kapitel_13"
---

# [[Use_Case-Manager]]

- **Kernkonzept:** Ein [[Use_Case-Manager]] ist ein zentraler [[Akteur]] in der [[Softwarearchitektur]], der alle [[Operation|Operationen]] eines spezifischen [[Use_Case|Use Cases]] bündelt und verantwortet. Er dient als dedizierte [[Klasse]] im [[Objektorientiertes_Design|objektorientierten Design]], die als [[Schnittstelle]] zwischen dem [[System]] und den [[Komponente|Komponenten]] fungiert, welche den [[Use_Case]] umsetzen.
- **Nutzen & Zweck:** Der [[Use_Case-Manager]] löst das Problem der verteilten [[Verantwortung]] in komplexen [[System|Systemen]], indem er die [[Zuständigkeit]] für einen gesamten [[Use_Case]] klar einer einzigen [[Klasse]] zuweist. Dies fördert die [[Kohäsion]] und [[Lose_Kopplung|lose Kopplung]] zwischen [[Komponente|Komponenten]], vereinfacht die [[Wartbarkeit]] und [[Erweiterbarkeit]] des [[Systems]] und ermöglicht eine konsistente Umsetzung der [[Geschäftslogik]]. Zudem erleichtert er die [[Nachverfolgbarkeit]] von [[Anforderung|Anforderungen]] im [[Code]] und reduziert die [[Komplexität]] durch zentrale Steuerung aller [[Operation|Operationen]] eines [[Use_Case|Use Cases]].
- **Abgrenzung & Grenzen:** Ein [[Use_Case-Manager]] sollte nicht eingesetzt werden, wenn der [[Use_Case]] trivial ist oder nur wenige, einfache [[Interaktion|Interaktionen]] erfordert, da der Overhead der zusätzlichen [[Klasse]] dann unnötig ist. Alternativen wie direkte [[Delegation]] an bestehende [[Klasse|Klassen]] oder die Nutzung von [[Fassade|Fassaden]] sind in solchen Fällen vorzuziehen. Zudem eignet sich das Konzept weniger für [[System|Systeme]] mit stark verteilten oder [[Mikroservice-Architektur|mikroservice-basierten Architekturen]], wo [[Use_Case|Use Cases]] oft über mehrere [[Service|Services]] hinweg verteilt sind. Im Gegensatz zu allgemeinen [[Fassade|Fassaden]], die mehrere [[Use_Case|Use Cases]] kapseln können, ist ein [[Use_Case-Manager]] spezifisch auf einen einzigen [[Use_Case]] zugeschnitten. Nicht geeignet ist das Konzept auch, wenn [[Use_Case|Use Cases]] stark voneinander abhängen oder wenn die [[Komplexität]] des [[Systems]] durch zu viele [[Manager]] unnötig erhöht wird. In solchen Fällen können [[Mediator_Pattern|Mediatoren]] oder [[Entwurfsmuster|Muster]] wie das [[Command_Pattern]] sinnvollere Lösungen bieten.
- **Beispiel / Code:** ```java
// Beispiel 1: Einfache Implementierung eines Use-Case-Managers
public class ManageMembers {
    private Vereinsmanager manager;
    
    public void addMember(Member member) {
        manager.validate(member);
        manager.persist(member);
    }
    
    public void removeMember(Member member) {
        manager.remove(member);
    }
}

// Beispiel 2: Erweiterte Implementierung mit Schnittstelle und Dependency Injection
public interface ManageMembers {
    void addMember(Member member);
    void removeMember(String memberId);
    Member findMember(String memberId);
}

@ApplicationScope
@Component
public class ManageMembersImpl implements ManageMembers {
    @Autowired
    private MemberRepository memberRepository;
    
    @Autowired
    private NotificationService notificationService;
    
    @Override
    public void addMember(Member member) {
        memberRepository.save(member);
        notificationService.sendWelcomeNotification(member);
    }
    
    @Override
    public void removeMember(String memberId) {
        Member member = memberRepository.findById(memberId).orElseThrow();
        memberRepository.delete(member);
        notificationService.sendFarewellNotification(member);
    }
    
    @Override
    public Member findMember(String memberId) {
        return memberRepository.findById(memberId).orElseThrow();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1e2
- **Vorgänger / Parent:** [[Verantwortungszuweisung]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
