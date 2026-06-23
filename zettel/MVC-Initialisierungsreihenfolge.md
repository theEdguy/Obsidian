---
id: 2a72dcac-6a10-4bc4-80e2-2d1ffce0aafd
title: "Initialisierungsreihenfolge"
date: 2026-06-23
tags:
  - software_engineering
  - process
  - architecture
  - draft
source: "software_engineering_kapitel_11"
---

# [[Initialisierungsreihenfolge]]

- **Kernkonzept:** Die Initialisierungsreihenfolge im Model-View-Controller (MVC)-Pattern definiert die sequentielle Erzeugung und Verknüpfung der Komponenten Modell, Views und Controller, um eine korrekte Funktionsweise der Anwendung sicherzustellen. Sie legt fest, in welcher Abfolge Abhängigkeiten aufgelöst und Beobachtermechanismen registriert werden.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der zyklischen Abhängigkeiten und inkonsistenten Zustände während der Systeminitialisierung. Durch eine definierte Reihenfolge wird gewährleistet, dass alle Komponenten vollständig initialisiert und korrekt miteinander verbunden sind, bevor Benutzerinteraktionen verarbeitet werden. Dies verhindert Laufzeitfehler durch fehlende Referenzen oder unvollständige Registrierungen im Observer-Pattern.
- **Abgrenzung & Grenzen:** Die Initialisierungsreihenfolge sollte nicht genutzt werden, wenn Komponenten unabhängig voneinander arbeiten können oder keine Abhängigkeiten bestehen. Alternativen wie Lazy Initialization oder Dependency Injection können flexibler sein, wenn Komponenten dynamisch zur Laufzeit geladen werden. Bei einfachen Anwendungen mit wenigen Komponenten ist eine explizite Reihenfolge oft unnötig und erhöht die Komplexität.
- **Beispiel / Code:** ```java
// Schrittweise Initialisierung im MVC-Pattern
public class MVCDemo {
    public static void main(String[] args) {
        // 1. Modell initialisieren
        Model model = new Model();
        
        // 2. Views erstellen und beim Modell registrieren
        View view1 = new View(model);
        View view2 = new View(model);
        
        // 3. Controller erstellen (je View einen Controller)
        Controller controller1 = new Controller(model, view1);
        Controller controller2 = new Controller(model, view2);
        
        // 4. Hauptschleife starten
        view1.display();
        view2.display();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c5
- **Vorgänger / Parent:** [[MVC-Implementierung]]
- **Folgezettel / Unterzettel:**
  - [[Modell-Erzeugung]]
  - [[View-Registrierung]]
  - [[Controller-Kopplung]]
- **Querverweise:**
  - [[Systemstart]]
  - [[Dependency_Injection]]
