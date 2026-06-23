---
id: ccaef194-6e53-412f-b880-2942a3a21f47
title: "Controller-Entwurf"
date: 2026-06-23
tags:
  - software_engineering
  - design
  - implementation
  - draft
source: "software_engineering_kapitel_11"
---

# [[Controller-Entwurf]]

- **Kernkonzept:** Der Controller-Entwurf im Model-View-Controller (MVC)-Pattern ist verantwortlich für die Verarbeitung von Benutzereingaben, deren Interpretation und die Abbildung auf entsprechende Systemoperationen des Modells. Er fungiert als Vermittler zwischen View und Modell, um die Geschäftslogik auszulösen und den Datenfluss zu steuern.
- **Nutzen & Zweck:** Der Controller löst das Problem der Trennung von Benutzeroberfläche und Geschäftslogik, indem er die Eingaben des Nutzers entkoppelt verarbeitet und die Kommunikation zwischen View und Modell koordiniert. Dies ermöglicht eine klare Strukturierung der Software, verbessert die Wartbarkeit und erleichtert die Wiederverwendung von Komponenten. Zudem unterstützt er die Umsetzung des Observer-Patterns, um Änderungen im Modell an die Views zu propagieren.
- **Abgrenzung & Grenzen:** Der Controller sollte nicht genutzt werden, wenn die Anwendung keine interaktiven Benutzereingaben verarbeitet oder wenn eine direkte Kopplung zwischen View und Modell ausreicht (z. B. bei einfachen Datenanzeigen ohne Logik). Alternativen wie das MVP-Pattern (Model-View-Presenter) oder MVVM (Model-View-ViewModel) können besser geeignet sein, wenn eine stärkere Entkopplung oder datenbindungsorientierte Ansätze benötigt werden. Zudem ist der Controller nicht für die Darstellung oder Speicherung von Daten zuständig, was klar von den Verantwortlichkeiten des Modells und der View abgegrenzt ist.
- **Beispiel / Code:** ```java
public class MemberController {
    private MemberModel model;
    private MemberView view;

    public MemberController(MemberModel model, MemberView view) {
        this.model = model;
        this.view = view;
        this.view.addController(this); // View kennt ihren Controller
    }

    public void handleAddMember(String name, String email) {
        try {
            model.addMember(name, email); // Aufruf der Modell-Logik
            view.update(); // Aktualisierung der View
        } catch (Exception e) {
            view.showError("Fehler beim Hinzufügen des Mitglieds");
        }
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3
- **Vorgänger / Parent:** [[MVC-Implementierung]]
- **Folgezettel / Unterzettel:**
  - [[Eingabeinterpretation]]
  - [[Systemoperationen]]
  - [[Controller-Fabriken]]
- **Querverweise:**
  - [[Command-Pattern]]
  - [[Front_Controller]]
