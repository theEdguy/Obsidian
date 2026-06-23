---
id: 95554154-fb80-4a03-bf5c-8f1fbe98969f
title: "Komponentenzerlegung"
date: 2026-06-23
tags:
  - software_engineering
  - architecture
  - design
  - draft
source: "software_engineering_kapitel_11"
---

# [[Komponentenzerlegung]]

- **Kernkonzept:** Komponentenzerlegung ist ein Architekturprinzip im Software-Engineering, bei dem ein Softwaresystem in kleinere, unabhängige und funktional abgeschlossene Einheiten (Komponenten) unterteilt wird, um die Komplexität zu reduzieren und die Wartbarkeit zu erhöhen. Jede Komponente realisiert spezifische Use Cases oder Aufgaben eines Akteurs und kapselt ihre interne Logik.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Skalierbarkeit, Wiederverwendbarkeit und Testbarkeit von Software zu verbessern. Es löst das Problem monolithischer Systeme, die schwer zu warten, zu erweitern oder zu debuggen sind, indem es klare Schnittstellen und Verantwortlichkeiten schafft. Durch die Zerlegung in Komponenten können Teams parallel arbeiten, Änderungen lokal begrenzt bleiben und die Systemarchitektur übersichtlicher gestaltet werden.
- **Abgrenzung & Grenzen:** Komponentenzerlegung sollte nicht angewendet werden, wenn das System sehr klein oder trivial ist, da der Overhead der Schnittstellen und Kommunikation zwischen Komponenten die Vorteile überwiegen kann. Alternativen wie monolithische Architekturen oder Microservices (bei verteilten Systemen) können je nach Kontext besser geeignet sein. Im Gegensatz zu Microservices bleiben Komponenten jedoch meist innerhalb eines gemeinsamen Adressraums und teilen sich Ressourcen, was die Kommunikation vereinfacht, aber die Unabhängigkeit einschränkt.
- **Beispiel / Code:** ```java
// Beispiel: Zerlegung in Komponenten für einen Vereinsverwaltungssystem-Kern
public interface MemberManagementComponent {
    void addMember(Member member) throws ValidationException;
    void updateMember(Member member) throws NotFoundException;
    List<Member> getAllMembers();
    void removeMember(String memberId) throws NotFoundException;
}

public class MemberManagementComponentImpl implements MemberManagementComponent {
    private final MemberRepository repository;
    private final NotificationService notificationService;

    public MemberManagementComponentImpl(MemberRepository repository, 
                                        NotificationService notificationService) {
        this.repository = repository;
        this.notificationService = notificationService;
    }

    @Override
    public void addMember(Member member) {
        repository.save(member);
        notificationService.notifyMemberAdded(member);
    }
    // Weitere Implementierungen...
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1
- **Vorgänger / Parent:** [[MVC-Strukturen]]
- **Folgezettel / Unterzettel:**
  - [[Use-Case-Komponenten]]
  - [[Akteurspezifische_Komponenten]]
- **Querverweise:**
  - [[Modularisierung]]
  - [[Microservices]]
