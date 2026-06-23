---
id: 33e280cf-0145-4a4e-8088-8b10fd5cbe77
title: "Package-Struktur"
date: 2026-06-23
tags:
  - software_engineering
  - organisation
  - modularität
  - draft
source: "software_engineering_kapitel_10"
---

# [[Package-Struktur]]

- **Kernkonzept:** Die Package-Struktur ist ein Organisationsprinzip in der Softwareentwicklung, das Klassen und andere Elemente in logische, hierarchische Namensräume (Packages) gruppiert, um die Übersichtlichkeit und Modularität eines Systems zu erhöhen. Sie bildet eine baumartige Struktur ohne zyklische Abhängigkeiten und ermöglicht eine klare Trennung von Schnittstellen und Implementierungen.
- **Nutzen & Zweck:** Die Package-Struktur löst das Problem der Unübersichtlichkeit und starken Kopplung in großen Softwareprojekten. Sie ermöglicht eine systematische Gliederung des Codes, reduziert Abhängigkeiten zwischen Komponenten und erleichtert die Wartbarkeit sowie die Wiederverwendung von Code. Durch die klare Trennung von Schnittstellen und Implementierungen wird die Kapselung gestärkt und die Zusammenarbeit in Teams vereinfacht.
- **Abgrenzung & Grenzen:** Eine Package-Struktur sollte nicht genutzt werden, wenn das Projekt sehr klein ist und keine komplexen Abhängigkeiten aufweist, da der Overhead der Organisation dann unnötig ist. Alternativ können flache Namensräume oder einfache Verzeichnisstrukturen ausreichen. Zudem ist die Package-Struktur nicht geeignet, um dynamische Laufzeitabhängigkeiten oder verteilte Systeme direkt abzubilden – hier sind zusätzliche Konzepte wie Verteilungsdiagramme oder Dependency-Injection erforderlich. Zyklische Abhängigkeiten zwischen Packages sind strikt zu vermeiden, was in stark vernetzten Systemen zu Herausforderungen führen kann.
- **Beispiel / Code:** ```java
// Beispiel für eine Package-Struktur mit Trennung von Schnittstelle und Implementierung
// Package: com.myapp.member.port.include
package com.myapp.member.port.include;

public interface MemberRepository {
    void saveMember(Member member);
    Member findMemberById(String id);
}

// Package: com.myapp.member.impl
package com.myapp.member.impl;

import com.myapp.member.port.include.MemberRepository;

public class MemberRepositoryImpl implements MemberRepository {
    @Override
    public void saveMember(Member member) {
        // Implementierung der Persistenzlogik
    }
    
    @Override
    public Member findMemberById(String id) {
        // Implementierung der Suchlogik
        return null;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1a3
- **Vorgänger / Parent:** [[Komponenten]]
- **Folgezettel / Unterzettel:**
  - [[Abhängigkeiten]]
  - [[Sichtbarkeit]]
- **Querverweise:** keine
