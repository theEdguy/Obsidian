---
id: a43547da-db62-41a5-8be1-6c73846cc631
title: "Command"
date: 2026-06-23
tags:
  - software_engineering
  - command
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[Command]]

- **Kernkonzept:** Das Command-Design-Pattern kapselt eine Aktion oder Anfrage als eigenständiges Objekt, das alle Informationen zur Ausführung der Aktion enthält. Dadurch lassen sich Aktionen parametrisieren, in Warteschlangen einreihen oder rückgängig machen.
- **Nutzen & Zweck:** Das Command-Pattern löst das Problem, Aktionen oder Operationen flexibel zu verwalten, ohne die aufrufenden Klassen mit den Details der Ausführung zu belasten. Es ermöglicht die Entkopplung von Objekten, die eine Aktion auslösen, von denen, die sie ausführen. Dadurch können Aktionen dynamisch zusammengestellt, protokolliert, rückgängig gemacht oder in Warteschlangen verwaltet werden, was besonders in Systemen mit komplexen Benutzerinteraktionen oder undo/redo-Funktionalität nützlich ist.
- **Abgrenzung & Grenzen:** Das Command-Pattern sollte nicht eingesetzt werden, wenn die auszuführenden Aktionen trivial sind oder keine Notwendigkeit für Parametrisierung, Warteschlangen oder Rückgängigmachung besteht, da der zusätzliche Overhead durch die Kapselung der Aktionen in Objekten unnötig ist. Alternativen wie direkte Methodenaufrufe oder das Strategy-Pattern können in solchen Fällen effizienter sein. Zudem ist das Pattern weniger geeignet, wenn die Aktionen stark voneinander abhängen oder eine feste Ausführungsreihenfolge erfordern, die nicht durch die Command-Objekte abgebildet werden kann.
- **Beispiel / Code:** ```java
// Command-Interface
public interface Command {
    void execute();
    void undo();
}

// Konkrete Command-Klasse
public class LightOnCommand implements Command {
    private Light light;

    public LightOnCommand(Light light) {
        this.light = light;
    }

    @Override
    public void execute() {
        light.turnOn();
    }

    @Override
    public void undo() {
        light.turnOff();
    }
}

// Receiver-Klasse
public class Light {
    public void turnOn() {
        System.out.println("Licht ist an.");
    }

    public void turnOff() {
        System.out.println("Licht ist aus.");
    }
}

// Invoker-Klasse
public class RemoteControl {
    private Command command;

    public void setCommand(Command command) {
        this.command = command;
    }

    public void pressButton() {
        command.execute();
    }

    public void pressUndo() {
        command.undo();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7c3
- **Vorgänger / Parent:** [[Verhaltensmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Verhaltensmuster]]
  - [[Design_Pattern]]
