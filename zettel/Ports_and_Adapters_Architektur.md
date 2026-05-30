---
id: cacd146f-eb7a-448a-a9f5-5b9b50a478ec
title: "Ports_and_Adapters_Architektur"
date: 2026-05-30
tags:
  - software_engineering
  - softwarearchitektur
  - design_pattern
  - entkopplung
  - draft
source: "SWE Slides (Folien 316-330)"
---

# [[Ports_and_Adapters_Architektur]]

- **Kernkonzept:** Die [[Ports_and_Adapters_Architektur]] (auch Hexagonale Architektur) trennt die [[Kernlogik]] eines [[Systems]] von externen [[Abhängigkeit|Abhängigkeiten]] durch definierte [[Schnittstelle|Schnittstellen]] (Ports) und deren Implementierungen (Adapter).
- **Nutzen & Zweck:** Sie löst das Problem der engen Kopplung zwischen [[Kernlogik]] und externen [[System|Systemen]] (z. B. Datenbanken, APIs) und ermöglicht die einfache Austauschbarkeit von [[Abhängigkeit|Abhängigkeiten]] ohne Änderung der [[Kernlogik]].
- **Abgrenzung & Grenzen:** Nicht sinnvoll für kleine [[System|Systeme]] mit geringer [[Komplexität]] oder wenn die [[Abhängigkeit|Abhängigkeiten]] statisch und unveränderlich sind. Alternativ kann eine [[Schichtenarchitektur]] verwendet werden.
- **Beispiel / Code:** ```java
// Port (Schnittstelle)
public interface MemberRepository {
    void save(Member member);
    Member findById(String id);
}

// Adapter (Implementierung)
public class DatabaseMemberRepository implements MemberRepository {
    @Override
    public void save(Member member) {
        // Datenbank-Logik
    }
}
```
