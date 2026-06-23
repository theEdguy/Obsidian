---
id: d005cdcb-9b47-4889-8730-f62ab263d311
title: "Management-Prinzip"
date: 2026-06-23
tags:
  - software_engineering
  - designprinzip
  - verantwortung
  - draft
source: "software_engineering_kapitel_13"
---

# [[Management-Prinzip]]

- **Kernkonzept:** Das Management-Prinzip ist ein Designprinzip im objektorientierten Software-Engineering, das die Verantwortlichkeit für die Organisation und Verwaltung eines Systems einer zentralen Klasse zuweist. Diese Klasse repräsentiert entweder das gesamte System, die Organisation, einen Akteur der realen Welt oder einen spezifischen Use Case und koordiniert die Interaktionen zwischen Komponenten.
- **Nutzen & Zweck:** Das Management-Prinzip löst das Problem der unklaren Verantwortungsverteilung in komplexen Softwaresystemen. Es schafft eine klare Struktur, indem es die Steuerung und Koordination von Abläufen einer dedizierten Klasse zuweist. Dadurch wird die Wartbarkeit verbessert, die Übersichtlichkeit erhöht und die Kopplung zwischen Komponenten reduziert, da Abhängigkeiten zentral verwaltet werden. Zudem erleichtert es die Nachverfolgbarkeit von Use Cases und Systemoperationen.
- **Abgrenzung & Grenzen:** Das Management-Prinzip sollte nicht angewendet werden, wenn das System sehr klein oder trivial ist, da der Overhead einer zentralen Steuerungsklasse dann unnötig ist. Es unterscheidet sich von verteilten Ansätzen wie Microservices oder rein funktionaler Programmierung, bei denen Verantwortlichkeiten dezentral organisiert sind. Bei hochgradig parallelen oder verteilten Systemen kann das Prinzip zu Engpässen führen, da die zentrale Instanz zum Flaschenhals werden kann. Alternativen wie das Fassade-Muster oder Mediator-Muster bieten ähnliche, aber flexiblere Lösungen für spezifischere Szenarien.
- **Beispiel / Code:** ```java
// Beispiel für eine zentrale Management-Klasse nach dem Management-Prinzip
public interface MemberManagement {
    void addMember(Member member);
    void removeMember(String memberId);
    Member findMember(String memberId);
}

@ApplicationScope
@Component
public class ManageMembers implements MemberManagement {
    @Autowired
    private MemberRepository memberRepository;
    
    @Autowired
    private NotificationService notificationService;
    
    @Override
    public void addMember(Member member) {
        memberRepository.save(member);
        notificationService.sendWelcomeEmail(member);
    }
    
    @Override
    public void removeMember(String memberId) {
        Member member = memberRepository.findById(memberId).orElseThrow();
        memberRepository.delete(member);
        notificationService.sendFarewellEmail(member);
    }
    
    @Override
    public Member findMember(String memberId) {
        return memberRepository.findById(memberId).orElseThrow();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a5
- **Vorgänger / Parent:** [[Objektorientierte_Analyse_und_Design]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
