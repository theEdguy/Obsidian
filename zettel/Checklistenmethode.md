---
id: 10fac9db-eb5c-46bd-8fc9-8ad4fde3f85c
title: "Checklistenmethode"
date: 2026-06-23
tags:
  - software_engineering
  - analyse
  - draft
source: "software_engineering_kapitel_09"
---

# [[Checklistenmethode]]

- **Kernkonzept:** Die Checklistenmethode ist eine systematische Strategie zur Identifikation von Objekten (Konzepten) in der Problemdomäne durch Abgleich mit vordefinierten Kategorien wie Dinge, Rollen, Prozesse oder Ereignisse. Sie dient als strukturierte Grundlage für die Erstellung eines Analyse-Objektmodells.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der unstrukturierten oder unvollständigen Erfassung von Domänenobjekten während der Analysephase. Es stellt sicher, dass zentrale Konzepte der Problemdomäne nicht übersehen werden, indem es eine reproduzierbare und nachvollziehbare Vorgehensweise zur Objektidentifikation bietet. Dadurch wird die Konsistenz und Vollständigkeit des Analyse-Objektmodells verbessert.
- **Abgrenzung & Grenzen:** Die Checklistenmethode sollte nicht isoliert angewendet werden, da sie allein keine kontextspezifischen oder impliziten Konzepte aus Use-Case-Beschreibungen erfasst. Sie unterscheidet sich von der Substantivmethode, die auf sprachliche Analyse setzt, und sollte mit dieser kombiniert werden. Nicht geeignet ist sie für Domänen mit hochgradig abstrakten oder dynamischen Konzepten, die sich nicht in vordefinierte Kategorien einordnen lassen.
- **Beispiel / Code:** ```java
// Beispiel einer Checklisten-Kategorie für eine Vereinsverwaltung
public enum KonzeptKategorie {
    DING,          // z.B. Mitgliedskarte, Vereinsausweis
    ROLLE,         // z.B. Vereinsmanager, Abteilungsleiter
    PROZESS,       // z.B. Mitgliedschaftsantrag, Beitragszahlung
    EREIGNIS,      // z.B. Mitgliederversammlung, Austritt
    ORGANISATION,  // z.B. Abteilung, Vorstand
    INTERAKTION    // z.B. Benachrichtigung, Authentifizierung
}

// Anwendung der Checkliste zur Identifikation von Konzepten
List<String> identifiziereKonzepte(UseCase useCase) {
    List<String> konzepte = new ArrayList<>();
    for (KonzeptKategorie kategorie : KonzeptKategorie.values()) {
        konzepte.addAll(extrahiereKonzepteNachKategorie(useCase, kategorie));
    }
    return konzepte;
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2a1a
- **Vorgänger / Parent:** [[Klassenkandidat]]
- **Folgezettel / Unterzettel:**
  - [[Kategorie_Ding]]
  - [[Kategorie_Rolle]]
  - [[Kategorie_Prozess]]
- **Querverweise:**
  - [[Problemdomäne]]
  - [[Fachkonzept]]
