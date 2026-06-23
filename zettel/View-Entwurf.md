---
id: 7168612f-69b4-4c9c-b0a5-fee78adbb7dd
title: "View-Entwurf"
date: 2026-06-23
tags:
  - software_engineering
  - design
  - ui
  - draft
source: "software_engineering_kapitel_11"
---

# [[View-Entwurf]]

- **Kernkonzept:** Der View-Entwurf im Model-View-Controller (MVC)-Pattern umfasst die Gestaltung und Implementierung der Benutzeroberfläche, die ausschließlich für die Darstellung von Daten und die Interaktion mit dem Nutzer zuständig ist, ohne Geschäftslogik zu enthalten.
- **Nutzen & Zweck:** Der View-Entwurf existiert, um eine klare Trennung zwischen Präsentation und Logik zu schaffen. Dies ermöglicht eine unabhängige Entwicklung, Wartung und Anpassung der Benutzeroberfläche, ohne die zugrundeliegende Geschäftslogik zu beeinflussen. Zudem fördert es die Wiederverwendbarkeit von Views für verschiedene Anwendungsfälle und erleichtert die Zusammenarbeit zwischen Designern und Entwicklern.
- **Abgrenzung & Grenzen:** Der View-Entwurf sollte nicht genutzt werden, wenn die Anwendung keine komplexe Benutzeroberfläche erfordert oder wenn eine enge Kopplung zwischen Darstellung und Logik aus Performance-Gründen notwendig ist. Alternativen wie das Model-View-ViewModel (MVVM)-Pattern oder direkte UI-Programmierung ohne Pattern können in einfachen Fällen effizienter sein. Im Gegensatz zu diesen Ansätzen trennt MVC jedoch strikt die Verantwortlichkeiten und eignet sich besser für große, skalierbare Anwendungen.
- **Beispiel / Code:** ```java
// Beispiel für eine einfache View-Klasse in Java (Swing)
import javax.swing.*;
import java.awt.*;

public class MemberView extends JFrame implements Observer {
    private JTextArea memberDisplay;
    private JButton updateButton;
    private MemberModel model;

    public MemberView(MemberModel model) {
        this.model = model;
        model.addObserver(this); // Registrierung beim Modell
        
        setTitle("Mitgliederverwaltung");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        
        memberDisplay = new JTextArea();
        updateButton = new JButton("Aktualisieren");
        
        setLayout(new BorderLayout());
        add(new JScrollPane(memberDisplay), BorderLayout.CENTER);
        add(updateButton, BorderLayout.SOUTH);
        
        updateView(); // Initiale Darstellung
    }
    
    @Override
    public void update(Observable o, Object arg) {
        updateView(); // Aktualisiert die View bei Änderungen im Modell
    }
    
    private void updateView() {
        memberDisplay.setText(model.getMemberData()); // Holt Daten vom Modell
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c4
- **Vorgänger / Parent:** [[MVC-Implementierung]]
- **Folgezettel / Unterzettel:**
  - [[Display-Funktion]]
  - [[Update-Funktion]]
  - [[Benutzeroberflächenkomponenten]]
- **Querverweise:**
  - [[UI-Design]]
  - [[Template_Method]]
