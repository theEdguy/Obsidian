---
id: 045e796e-1c7e-478b-a4c9-6152600dba72
title: "Facade"
date: 2026-06-23
tags:
  - software_engineering
  - facade
  - design_pattern
  - draft
source: "software_engineering_kapitel_07"
---

# [[Facade]]

- **Kernkonzept:** Das Facade-Muster ist ein strukturelles Design-Pattern, das eine vereinfachte Schnittstelle zu einem komplexen Subsystem bereitstellt. Es kapselt die Komplexität hinter einer einheitlichen Fassade und bietet eine klare, leicht nutzbare API für den Client.
- **Nutzen & Zweck:** Das Facade-Muster existiert, um die Nutzung komplexer Systeme oder Bibliotheken zu vereinfachen, indem es die Interaktion mit vielen Klassen und Methoden auf eine einzige Schnittstelle reduziert. Es löst das Problem der hohen Kopplung zwischen Client-Code und Subsystemen, verbessert die Wartbarkeit und fördert die Trennung von Verantwortlichkeiten. Zudem schützt es den Client vor Änderungen im Subsystem, da nur die Fassade angepasst werden muss.
- **Abgrenzung & Grenzen:** Das Facade-Muster sollte nicht genutzt werden, wenn das Subsystem einfach strukturiert ist oder nur wenige Interaktionen erfordert, da der zusätzliche Abstraktionslayer dann unnötigen Overhead erzeugt. Es unterscheidet sich von Adapter-Mustern, die bestehende Schnittstellen anpassen, während Facade eine neue, vereinfachte Schnittstelle schafft. Zudem ist es keine Lösung für funktionale Erweiterungen des Subsystems, sondern dient ausschließlich der Vereinfachung der Nutzung. Bei stark variierenden Client-Anforderungen kann eine Fassade zu unflexibel sein.
- **Beispiel / Code:** ```java
// Komplexes Subsystem
class CPU {
    public void start() { System.out.println("CPU gestartet"); }
    public void execute() { System.out.println("CPU führt Befehle aus"); }
}

class Memory {
    public void load() { System.out.println("Daten in Speicher geladen"); }
}

class HardDrive {
    public void read() { System.out.println("Daten von Festplatte gelesen"); }
}

// Facade
class ComputerFacade {
    private CPU cpu;
    private Memory memory;
    private HardDrive hardDrive;

    public ComputerFacade() {
        this.cpu = new CPU();
        this.memory = new Memory();
        this.hardDrive = new HardDrive();
    }

    public void startComputer() {
        cpu.start();
        memory.load();
        hardDrive.read();
        cpu.execute();
    }
}

// Client-Code
public class Client {
    public static void main(String[] args) {
        ComputerFacade computer = new ComputerFacade();
        computer.startComputer();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7b3
- **Vorgänger / Parent:** [[Strukturmuster]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Strukturmuster]]
  - [[Design_Pattern]]
