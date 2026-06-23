---
id: 5c31c8ae-db9b-4597-93c1-04dc35996c45
title: "Verantwortungszuweisung"
date: 2026-06-23
tags:
  - software_engineering
  - designprozess
  - verantwortung
  - draft
source: "software_engineering_kapitel_13"
---

# [[Verantwortungszuweisung]]

- **Kernkonzept:** Verantwortungszuweisung im Software-Design bezeichnet den Prozess, bei dem klar definiert wird, welche Klasse oder welches Objekt für bestimmte Aufgaben oder Informationen zuständig ist. Dies erfolgt nach Prinzipien wie dem Informationsexperten oder der losen Kopplung, um ein modulares und wartbares System zu schaffen.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem unklarer Zuständigkeiten in objektorientierten Systemen, das zu schwer wartbarem, fehleranfälligem Code führt. Durch systematische Zuweisung von Verantwortlichkeiten wird die Struktur des Systems verbessert, die Wiederverwendbarkeit von Komponenten erhöht und die Zusammenarbeit im Team erleichtert. Es unterstützt iterative Entwicklungsprozesse, indem es klare Schnittstellen und Verantwortungsbereiche schafft.
- **Abgrenzung & Grenzen:** Verantwortungszuweisung sollte nicht angewendet werden, wenn das System zu klein oder trivial ist, da der Aufwand den Nutzen übersteigt. Es unterscheidet sich von ad-hoc-Designansätzen, bei denen Verantwortlichkeiten spontan und ohne klare Prinzipien verteilt werden. Zudem ist es weniger geeignet für stark datengetriebene Systeme, bei denen die Logik primär in Datenbankprozeduren oder Skripten abgebildet wird. Alternativen wie funktionale Programmierung oder prozedurale Ansätze verteilen Verantwortlichkeiten anders und sind in bestimmten Kontexten effizienter.
- **Beispiel / Code:** ```java
// Beispiel für Verantwortungszuweisung nach dem Informationsexperten-Prinzip
public interface MemberManagement {
    void addMember(Member member);
    Member findMemberById(String id);
}

// Klasse, die als Informationsexperte für Mitgliederdaten agiert
public class MemberService implements MemberManagement {
    private final MemberRepository repository;

    public MemberService(MemberRepository repository) {
        this.repository = repository;
    }

    @Override
    public void addMember(Member member) {
        // Verantwortung: Validierung und Speicherung der Mitgliederdaten
        if (member == null) {
            throw new IllegalArgumentException("Member darf nicht null sein");
        }
        repository.save(member);
    }

    @Override
    public Member findMemberById(String id) {
        // Verantwortung: Abfrage der Mitgliederdaten
        return repository.findById(id).orElse(null);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1e
- **Vorgänger / Parent:** [[Software-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Systemoperation]]
  - [[Use-Case-Manager]]
- **Querverweise:**
  - [[Objektorientierte_Analyse_und_Design]]
