---
id: 51084afe-92f8-407b-aac1-ef092d39191c
title: "Mockup"
date: 2026-06-23
tags:
  - software_engineering
  - design_tool
  - prototyping
  - design
  - ui
  - draft
source: "software_engineering_kapitel_11"
---

# [[Mockup]]

- **Kernkonzept:** Ein [[Mockup|Mockup]] ist ein vereinfachter, oft visueller [[Prototyp]] einer [[Benutzeroberfläche]] oder [[System]]-Interaktion, der im [[Design]]-Prozess erstellt wird, um [[Anforderung|Anforderungen]] zu veranschaulichen, [[Design]]-Entscheidungen zu evaluieren und frühzeitig Feedback von [[Stakeholder|Stakeholdern]] einzuholen. Es skizziert Layout, Navigation und Interaktionselemente ohne funktionale [[Logik]] oder dynamische Interaktivität.
- **Nutzen & Zweck:** Mockups lösen das Problem unklarer [[Anforderung|Anforderungen]] und [[Missverständnis|Missverständnisse]] in der frühen [[Softwareentwicklung]]-Phase, indem sie eine greifbare Diskussionsgrundlage für das [[User_Interface|User Interface]] schaffen. Sie ermöglichen es, [[Design]]-Entscheidungen kostengünstig zu validieren, Feedback zu sammeln und [[Iteration|Iterationen]] durchzuführen, bevor aufwendige [[Implementierung]] beginnt. Dadurch reduzieren sie spätere Nacharbeiten, verbessern die [[Usability]] und fördern die [[Kommunikation]] zwischen [[Entwickler|Entwicklern]], [[Designer|Designern]] und [[Stakeholder|Stakeholdern]].
- **Abgrenzung & Grenzen:** Mockups sind kein Ersatz für funktionsfähige [[Prototyp|Prototypen]] oder detaillierte [[Spezifikation|Spezifikationen]], da sie keine [[Logik]] oder dynamische Interaktionen abbilden. Sie unterscheiden sich von [[Wireframe|Wireframes]] durch einen höheren Detailgrad (z. B. Farben, Typografie, visuelle Hierarchie) und von [[Prototyp|Prototypen]] durch das Fehlen von Interaktivität. Für komplexe [[System|Systeme]] mit vielen Zuständen oder Echtzeit-Daten sind Mockups allein oft unzureichend, da sie keine [[Zustandsübergang|Zustandsübergänge]] oder [[Datenfluss|Datenflüsse]] darstellen können. Zudem eignen sie sich nicht für die Validierung von [[Performance]]- oder [[Skalierbarkeit]]-Anforderungen.
- **Beispiel / Code:** ```markdown
# Beispiel für ein Mockup (textuell)
[Bildschirm: Mitglieder verwalten]
- Liste aller Mitglieder (Tabelle mit Spalten: Name, E-Mail, Rolle)
- Schaltflächen: "[[Hinzufügen|Hinzufügen]]", "[[Löschen|Löschen]]", "[[Bearbeiten|Bearbeiten]]"
- Suchfeld mit Filteroptionen (z. B. nach Rolle)
- Visuelle Hervorhebung aktiver/ausgewählter Mitglieder
```

```java
// Beispiel: Einfaches Mockup als Java-Swing-Skizze (ohne Logik)
import javax.swing.*;

public class MemberManagementMockup {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Mitglieder verwalten - Mockup");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(600, 400);
        
        JPanel panel = new JPanel();
        panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS));
        
        // Suchfeld
        panel.add(new JLabel("Suche:"));
        panel.add(new JTextField(20));
        
        // Mitgliederliste
        panel.add(new JLabel("Mitgliederliste:"));
        String[] members = {"Max Mustermann (Admin)", "Anna Schmidt (Mitglied)"};
        JList<String> memberList = new JList<>(members);
        panel.add(new JScrollPane(memberList));
        
        // Schaltflächen
        JPanel buttonPanel = new JPanel();
        buttonPanel.add(new JButton("Hinzufügen"));
        buttonPanel.add(new JButton("Bearbeiten"));
        buttonPanel.add(new JButton("Löschen"));
        panel.add(buttonPanel);
        
        frame.add(panel);
        frame.setVisible(true);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d2b
- **Vorgänger / Parent:** [[Use-Case-Komponenten]]
- **Folgezettel / Unterzettel:**
  - [[UI-Entwurf]]
  - [[Benutzerführung]]
- **Querverweise:**
  - [[Prototyping]]
  - [[UI-Design]]
