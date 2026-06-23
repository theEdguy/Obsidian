---
id: 62b93f9e-75f7-4964-99ab-a3a6855a3ac9
title: "View"
date: 2026-06-24
tags:
  - software_engineering
  - komponente
  - mvc
  - architekturmuster
  - draft
source: "software_engineering_kapitel_15"
---

# [[View]]

- **Kernkonzept:** Die [[View|View]] ist eine zentrale [[Komponente]] im [[Model-View-Controller|MVC]]-[[Entwurfsmuster]], die für die Darstellung der Daten und die [[Benutzeroberfläche]] verantwortlich ist. Sie visualisiert die vom [[Modell]] bereitgestellten Informationen und leitet [[Benutzer|Benutzereingaben]] an den [[Controller]] weiter, ohne diese selbst zu verarbeiten oder domänenspezifische [[Logik]] zu enthalten.
- **Nutzen & Zweck:** Die [[View|View]] existiert, um die [[Trennung von Verantwortlichkeiten|Trennung von Darstellung und Logik]] in [[Softwareanwendung|Softwareanwendungen]] zu ermöglichen. Sie löst das Problem, dass [[Benutzeroberfläche|Benutzeroberflächen]] oft komplex und häufigen Änderungen unterworfen sind, während die zugrundeliegende [[Geschäftslogik]] stabil bleibt. Durch diese [[Trennung von Verantwortlichkeiten|Trennung]] wird die [[Wartbarkeit]] und [[Erweiterbarkeit]] der Anwendung verbessert, da Änderungen an der Oberfläche keine Auswirkungen auf das [[Modell]] oder die [[Steuerungslogik]] haben. Zudem ermöglicht sie die Wiederverwendung desselben [[Modell|Modells]] mit verschiedenen [[View|Views]] (z. B. für unterschiedliche [[Endgerät|Endgeräte]] oder Anwendungsfälle), was die [[Flexibilität]] und [[Modularität]] des Systems erhöht. Die [[View|View]] trägt damit maßgeblich zur [[Lose_Kopplung|losen Kopplung]] und [[Kohäsion|hohen Kohäsion]] im [[MVC]]-[[Architekturmuster]] bei.
- **Abgrenzung & Grenzen:** Die [[View|View]] sollte nicht genutzt werden, wenn die Anwendung keine [[Benutzeroberfläche]] benötigt (z. B. bei reinen [[Backend]]-Diensten) oder wenn die Darstellung extrem einfach ist und keine [[Trennung von Verantwortlichkeiten|Trennung von Logik und Präsentation]] erfordert. Alternativen wie das [[Model-View-Presenter|MVP]]- oder [[Model-View-ViewModel|MVVM]]-[[Entwurfsmuster]] können besser geeignet sein, wenn eine stärkere [[Entkopplung]] zwischen [[View|View]] und [[Logik]] gewünscht ist oder wenn die [[View|View]] komplexe [[Zustand|Zustände]] verwalten muss. Im Gegensatz zu diesen [[Entwurfsmuster|Mustern]] übernimmt die [[View|View]] im [[MVC]] keine [[Steuerungslogik]], sondern delegiert diese vollständig an den [[Controller]]. Zudem ist die [[View|View]] ungeeignet für Systeme, in denen die [[Präsentation]] eng mit der [[Datenverarbeitung]] verknüpft ist, wie z. B. in [[Echtzeit-System|Echtzeit-Systemen]] mit strengen [[Performance]]-Anforderungen. In solchen Fällen können [[Event-gesteuertes_System|Event-gesteuerte]] oder [[Reaktive_Programmierung|reaktive]] Ansätze vorteilhafter sein.
- **Beispiel / Code:** ```java
// Beispiel einer einfachen View in JavaFX (erweitert)
import javafx.scene.control.Label;
import javafx.scene.control.Button;
import javafx.scene.layout.VBox;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;

public class MemberView extends VBox {
    private Label memberNameLabel;
    private Button editButton;
    
    public MemberView() {
        memberNameLabel = new Label("Name: ");
        editButton = new Button("Bearbeiten");
        this.getChildren().addAll(memberNameLabel, editButton);
    }
    
    public void updateMemberName(String name) {
        memberNameLabel.setText("Name: " + name);
    }
    
    public void setEditAction(EventHandler<ActionEvent> handler) {
        editButton.setOnAction(handler);
    }
}

// Beispiel für eine View in Java Swing (alternativ)
import javax.swing.*;
import java.awt.event.ActionListener;

public class MemberView {
    private JFrame frame;
    private JTextField nameField;
    private JButton saveButton;
    
    public MemberView() {
        frame = new JFrame("Mitgliederverwaltung");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(300, 200);
        
        nameField = new JTextField(20);
        saveButton = new JButton("Speichern");
        
        JPanel panel = new JPanel();
        panel.add(new JLabel("Name:"));
        panel.add(nameField);
        panel.add(saveButton);
        
        frame.add(panel);
    }
    
    public void show() {
        frame.setVisible(true);
    }
    
    public String getName() {
        return nameField.getText();
    }
    
    public void addSaveListener(ActionListener listener) {
        saveButton.addActionListener(listener);
    }
}
```
