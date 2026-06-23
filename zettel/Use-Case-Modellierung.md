---
id: 52e1097b-2e82-4d19-91bb-0b80e5430070
title: "Use-Case-Modellierung"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - anforderungen
  - draft
source: "software_engineering_kapitel_06"
---

# [[Use-Case-Modellierung]]

- **Kernkonzept:** Use-Case-Modellierung ist eine Methode zur strukturierten Erfassung und Beschreibung von Anforderungen an ein Softwaresystem aus der Perspektive der Anwender. Sie stellt zentrale Abläufe (Geschäftsvorfälle) in Form von Szenarien dar und setzt diese zueinander in Beziehung, um die Funktionalität des Systems zu definieren.
- **Nutzen & Zweck:** Die Use-Case-Modellierung dient dazu, die Anforderungen eines Auftraggebers systematisch zu erfassen, zu strukturieren und für alle Projektbeteiligten verständlich zu dokumentieren. Sie löst das Problem, dass komplexe Systemanforderungen oft unklar, unvollständig oder widersprüchlich sind, indem sie die Interaktionen zwischen Akteuren und System in nachvollziehbaren Einheiten abbildet. Dadurch wird die Kommunikation zwischen Entwicklern, Auftraggebern und anderen Stakeholdern verbessert und die Grundlage für die weitere Analyse und das Design geschaffen.
- **Abgrenzung & Grenzen:** Use-Case-Modellierung sollte nicht eingesetzt werden, wenn die Anforderungen bereits vollständig und detailliert in anderer Form (z. B. durch formale Spezifikationen) vorliegen oder wenn es sich um sehr einfache Systeme mit minimaler Nutzerinteraktion handelt. Sie unterscheidet sich von rein textuellen Anforderungsdokumenten (z. B. Lastenheften) durch ihre visuelle und szenarienbasierte Darstellung, die zwar die Verständlichkeit erhöht, aber weniger präzise für technische Details ist. Alternativen wie User Stories (im agilen Kontext) sind flexibler, aber weniger strukturiert und eignen sich eher für iterative Entwicklungsprozesse mit häufigen Änderungen.
- **Beispiel / Code:** ```java
// Beispiel: Use-Case-Beschreibung in strukturierter Form (UML-ähnlich)
@UseCase(name = "Mitglied anlegen", actor = "Vereinsmitarbeiter")
public class CreateMemberUseCase {
    @Precondition
    public boolean isAuthorized(User user) {
        return user.hasRole("ADMIN") || user.hasRole("MITARBEITER");
    }
    
    @MainSuccessScenario
    public Member execute(MemberData data) {
        Member member = new Member(data);
        memberRepository.save(member);
        notificationService.sendWelcomeEmail(member);
        return member;
    }
    
    @AlternativeScenario(name = "E-Mail-Adresse bereits vorhanden")
    public void handleDuplicateEmail(MemberData data) {
        throw new BusinessException("E-Mail-Adresse bereits registriert.");
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a4
- **Vorgänger / Parent:** [[Requirements-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Analyse-Use-Case-Modell]]
  - [[Akteure_identifizieren]]
  - [[Szenarien_beschreiben]]
- **Querverweise:** keine
