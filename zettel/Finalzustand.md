---
id: 18842d7b-ea48-4db8-9586-c3281d4700cb
title: "Finalzustand"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - zustandsmaschine
  - entwurfsmuster
  - softwarearchitektur
  - gui_design
  - draft
source: "Klausur_Referenz"
---

# [[Finalzustand]]

- **Kernkonzept:** Ein **Finalzustand** (auch Endzustand genannt) ist ein spezieller [[Zustand]] in einer [[Zustandsmaschine]] (z. B. in [[UML_Zustandsdiagramm]]), der das reguläre Ende eines Prozesses oder einer Zustandsfolge markiert. Er signalisiert, dass die Zustandsmaschine ihre Ausführung abgeschlossen hat und keine weiteren Übergänge (Transitionen) mehr erfolgen. Im Gegensatz zum [[Startzustand]] oder [[History_State]] besitzt ein Finalzustand keine ausgehenden Transitionen und wird oft durch einen doppelten Kreis dargestellt.
- **Nutzen & Zweck:** Der Finalzustand dient folgenden Zwecken:
1. **Explizite Terminierung**: Er macht das Ende eines Prozesses oder einer Zustandsfolge für Entwickler und Stakeholder sichtbar, was die Nachvollziehbarkeit von [[Zustandsmaschine|Zustandsautomaten]] erhöht.
2. **Modularität**: In hierarchischen Zustandsmaschinen kann ein Finalzustand genutzt werden, um das Ende einer [[Subzustandsmaschine]] zu kennzeichnen und die Kontrolle an die übergeordnete Maschine zurückzugeben.
3. **Fehlervermeidung**: Durch die klare Definition eines Endpunkts werden undefinierte Zustände oder unendliche Schleifen vermieden.
4. **Integration in GUI-Logik**: In [[Model_View_Controller|MVC-Architekturen]] kann ein Finalzustand z. B. das Schließen eines Dialogs oder das Beenden einer Anwendung auslösen (vgl. [[ViewFactory]]).
- **Abgrenzung & Grenzen:** - **Kein implizites Ende**: Ohne Finalzustand muss das Ende einer Zustandsmaschine durch externe Logik (z. B. Bedingungen in Transitionen) definiert werden, was zu weniger wartbarem Code führt.
- **Kein History-State**: Ein Finalzustand speichert keine Historie (vgl. [[History_State]]), sondern beendet die Ausführung.
- **Kein Fehlerzustand**: Ein Finalzustand repräsentiert ein *erfolgreiches* Ende. Fehler oder Abbrüche sollten durch separate [[Fehlerzustand|Fehlerzustände]] modelliert werden.
- **Stolpersteine**: 
  - In komplexen Systemen kann die Verwechslung von Finalzuständen mit regulären Zuständen zu unklaren Terminierungsbedingungen führen.
  - In verteilten Systemen muss sichergestellt werden, dass alle beteiligten Komponenten den Finalzustand korrekt interpretieren (z. B. durch [[Event_Sourcing]] oder [[Saga_Pattern]]).
- **Beispiel / Code:** ```mermaid
stateDiagram-v2
    [*] --> Initialisierung
    Initialisierung --> Verarbeitung: Daten geladen
    Verarbeitung --> Finalzustand: Erfolgreich abgeschlossen
    Finalzustand --> [*]
```

**Java-Code (vereinfacht, z. B. mit State Pattern):**
```java
public interface State {
    void handle(Context context);
}

public class FinalState implements State {
    @Override
    public void handle(Context context) {
        System.out.println("Prozess beendet.");
        // Optional: Rückgabe an übergeordnete Zustandsmaschine
        context.setState(null);
    }
}

public class Context {
    private State state;
    public void setState(State state) { this.state = state; }
    public void execute() { if (state != null) state.handle(this); }
}
```
