---
id: a4caf61d-6e09-4e17-9988-e68723f8fc7e
title: "Use-Case-Komponenten"
date: 2026-06-23
tags:
  - software_engineering
  - analysis
  - design
  - draft
source: "software_engineering_kapitel_11"
---

# [[Use-Case-Komponenten]]

- **Kernkonzept:** Use-Case-Komponenten sind eigenständige, modularisierte Bausteine einer Softwarearchitektur, die jeweils einen spezifischen Anwendungsfall (Use Case) und die damit verbundenen Akteure kapseln. Sie trennen fachliche Logik, Datenhaltung und Benutzerschnittstelle nach dem MVC-Muster und ermöglichen eine klare Zuordnung von Verantwortlichkeiten.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der unübersichtlichen und schwer wartbaren Codebasis in komplexen Softwaresystemen, indem es die Implementierung nach fachlichen Anwendungsfällen strukturiert. Es fördert die Wiederverwendbarkeit, Testbarkeit und Skalierbarkeit, da Änderungen an einem Use Case isoliert vorgenommen werden können, ohne andere Systemteile zu beeinflussen. Zudem erleichtert es die Zusammenarbeit im Team durch klare Schnittstellen und Verantwortungsbereiche.
- **Abgrenzung & Grenzen:** Use-Case-Komponenten sollten nicht eingesetzt werden, wenn das System sehr klein oder trivial ist, da der Overhead der Modularisierung den Nutzen übersteigt. Alternativen wie monolithische Architekturen oder funktionale Zerlegung können hier effizienter sein. Im Gegensatz zu rein technischen Schichten (z. B. Datenzugriffsschicht) fokussieren Use-Case-Komponenten auf fachliche Abläufe und nicht auf technische Details. Sie unterscheiden sich auch von Microservices, da sie innerhalb eines Systems agieren und keine verteilte Architektur voraussetzen.
- **Beispiel / Code:** ```java
// Beispiel: Use-Case-Komponente für 'Mitglieder verwalten' nach MVC
public class ManageMembersUseCase {
    private MemberRepository memberRepository;  // Modell
    private List<MemberView> views;            // Views (Observer)
    
    public ManageMembersUseCase(MemberRepository repository) {
        this.memberRepository = repository;
        this.views = new ArrayList<>();
    }
    
    // Systemoperation: Mitglied hinzufügen
    public void addMember(Member member) {
        memberRepository.save(member);
        notifyViews();  // Observer-Pattern: Views aktualisieren
    }
    
    // Observer-Mechanismus
    public void registerView(MemberView view) {
        views.add(view);
    }
    
    private void notifyViews() {
        for (MemberView view : views) {
            view.update(memberRepository.findAll());
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d2
- **Vorgänger / Parent:** [[MVC-Strukturen]]
- **Folgezettel / Unterzettel:**
  - [[Systemoperationen]]
  - [[Mockups]]
  - [[Schnittstellendefinition]]
- **Querverweise:**
  - [[Use-Case-Analyse]]
  - [[Domain-Driven_Design]]
