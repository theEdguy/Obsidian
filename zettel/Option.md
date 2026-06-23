---
id: cb9d2f43-91c7-4c71-a1dc-48ad41d662cd
title: "Option"
date: 2026-06-23
tags:
  - software_engineering
  - uml-fragment
  - kontrollfluss
  - draft
source: "software_engineering_kapitel_13"
---

# [[Option]]

- **Kernkonzept:** Das UML-Fragment 'Option' (opt) ist ein Kontrollfluss-Konstrukt in Interaktionsdiagrammen, das einen optionalen Ablauf innerhalb einer Sequenz darstellt. Es wird verwendet, um eine Nachricht oder eine Gruppe von Nachrichten nur dann auszuführen, wenn eine bestimmte Bedingung erfüllt ist.
- **Nutzen & Zweck:** Das 'Option'-Fragment existiert, um bedingte Abläufe in Interaktionsdiagrammen präzise abzubilden, ohne den Hauptfluss zu unterbrechen. Es löst das Problem, alternative oder optionale Pfade in der Systemlogik darzustellen, die nur unter bestimmten Voraussetzungen durchlaufen werden, und erhöht so die Klarheit und Nachvollziehbarkeit des dynamischen Verhaltens von Objekten.
- **Abgrenzung & Grenzen:** Das 'Option'-Fragment sollte nicht genutzt werden, wenn der Ablauf zwingend erforderlich ist oder keine Bedingung vorliegt, da es ausschließlich für optionale Pfade gedacht ist. Im Gegensatz zum 'Alternative'-Fragment (alt), das mehrere exklusive Pfade abbildet, repräsentiert 'Option' nur einen einzigen, bedingten Pfad. Für iterative Abläufe ist das 'Loop'-Fragment die bessere Wahl.
- **Beispiel / Code:** ```java
// Beispiel in einem Sequenzdiagramm (UML-Notation):
opt [userIsAdmin]
    adminPanel.displaySettings();
    userManagement.updatePermissions();
end
```

// Entsprechende Java-Implementierung:
if (userIsAdmin) {
    adminPanel.displaySettings();
    userManagement.updatePermissions();
}

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d1c2
- **Vorgänger / Parent:** [[Nachrichtenfragment]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
