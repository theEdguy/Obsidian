---
id: e8a5af64-d5bf-44d8-a8d8-9b4cd3918990
title: "Modell-Trennung"
date: 2026-06-23
tags:
  - software_engineering
  - design_principle
  - architecture
  - draft
source: "software_engineering_kapitel_11"
---

# [[Modell-Trennung]]

- **Kernkonzept:** Modell-Trennung bezeichnet das Prinzip, die Kernlogik (Modell) einer Anwendung strikt von der Benutzeroberfläche (View) und der Steuerung (Controller) zu separieren, um eine klare Aufgabenteilung und Unabhängigkeit der Komponenten zu gewährleisten.
- **Nutzen & Zweck:** Dieses Konzept existiert, um die Wartbarkeit, Testbarkeit und Erweiterbarkeit von Software zu verbessern. Durch die Trennung der Verantwortlichkeiten können Änderungen an einer Komponente (z. B. der Oberfläche) vorgenommen werden, ohne die Kernlogik oder Steuerung zu beeinflussen. Es löst das Problem enger Kopplung, das zu schwer wartbaren und fehleranfälligen Systemen führt, und ermöglicht parallele Entwicklung durch verschiedene Teams.
- **Abgrenzung & Grenzen:** Modell-Trennung sollte nicht genutzt werden, wenn die Anwendung sehr klein oder einfach ist, da der Overhead der Trennung den Nutzen übersteigen kann. Alternativen wie das MVP- (Model-View-Presenter) oder MVVM-Muster (Model-View-ViewModel) eignen sich besser für komplexe Oberflächenlogik oder datengetriebene Anwendungen, da sie zusätzliche Abstraktionsschichten für die Steuerung bieten. MVC ist weniger geeignet, wenn die Anwendung stark zustandsbehaftet ist oder eine direkte Interaktion zwischen View und Modell erfordert.
- **Beispiel / Code:** ```java
// Modell: Enthält die Kernlogik und Daten, unabhängig von der Oberfläche
public class MitgliedModel {
    private List<Mitglied> mitglieder;

    public void addMitglied(Mitglied mitglied) {
        mitglieder.add(mitglied);
        notifyObservers(); // Benachrichtigt Views über Änderungen
    }

    public List<Mitglied> getMitglieder() {
        return mitglieder;
    }
}

// View: Stellt die Daten dar und leitet Benutzereingaben an den Controller weiter
public class MitgliedView {
    public void showMitglieder(List<Mitglied> mitglieder) {
        // Aktualisiert die Anzeige
    }
}

// Controller: Verarbeitet Benutzereingaben und aktualisiert Modell/View
public class MitgliedController {
    private MitgliedModel model;
    private MitgliedView view;

    public void handleAddMitglied(Mitglied mitglied) {
        model.addMitglied(mitglied);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c2
- **Vorgänger / Parent:** [[MVC-Implementierung]]
- **Folgezettel / Unterzettel:**
  - [[Kernfunktionalität]]
  - [[Datenhaltung]]
  - [[Service-Routinen]]
- **Querverweise:**
  - [[Separation_of_Concerns]]
  - [[Domain_Model]]
