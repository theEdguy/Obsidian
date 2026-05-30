---
id: e0f9d705-6cc5-4986-a1a2-f322cd3606d2
title: "Zustandsmaschine"
date: 2026-05-30
tags:
  - software_engineering
  - verhaltensmodellierung
  - systemdesign
  - design_pattern
  - verhaltensmuster
  - draft
source: "SWE Slides (Folien 376-388)"
---

# [[Zustandsmaschine]]

- **Kernkonzept:** Eine [[Zustandsmaschine]] modelliert das [[Verhalten]] eines [[Systems]] durch definierte [[Zustand|Zustände]] und [[Transition|Transitionen]], die durch [[Event|Events]] oder [[Ereignis|Ereignisse]] ausgelöst werden. Sie wird verwendet, um komplexe [[Logik]] in [[GUI|GUIs]], [[Prozesssteuerung|Prozesssteuerungen]] oder anderen [[Systemen]] strukturiert abzubilden und die [[Nachvollziehbarkeit]] zu erhöhen.
- **Nutzen & Zweck:** Die [[Zustandsmaschine]] löst das [[Problem]] der unübersichtlichen [[Steuerungslogik]] in [[Systemen]] mit vielen [[Zustand|Zuständen]] und [[Transition|Transitionen]], indem sie eine klare Struktur schafft. Dadurch wird die [[Kohäsion]] erhöht, die [[Komplexität]] reduziert und die [[Wartbarkeit]] verbessert. Besonders nützlich ist sie in [[Event-gesteuerten_Systemen|Event-gesteuerten Systemen]] oder bei der Modellierung von [[Ablauf|Abläufen]] in [[GUI|GUIs]] und [[Prozesssteuerung|Prozesssteuerungen]].
- **Abgrenzung & Grenzen:** Die [[Zustandsmaschine]] ist nicht geeignet für [[Systeme]] mit wenigen oder einfachen [[Zustand|Zuständen]], da der [[Overhead]] der Implementierung den Nutzen übersteigt. Ebenso ungeeignet ist sie für [[Systeme]], bei denen [[Zustand|Zustände]] dynamisch erzeugt oder zerstört werden. In solchen Fällen können Alternativen wie [[Regelbasierte_Systeme]], [[Event-gesteuerte_Programmierung]] oder [[Entwurfsmuster|Muster]] wie das [[Observer_Pattern]] flexibler sein. Zudem sollte sie nicht für lineare [[Ablauf|Abläufe]] verwendet werden, da dies die [[Wartbarkeit]] beeinträchtigen kann.
- **Beispiel / Code:** ```java
// Beispiel 1: Zustandsmaschine für ein Studienmodul
public enum State {
    MODUL_OFFEN, LABOR_TEIL_1, LABOR_TEIL_2, VORLESUNG_BESUCHT, PRUEFUNG_BESTANDEN;
}

public class ModulZustandsmaschine {
    private State currentState;

    public void transition(Event event) {
        switch (currentState) {
            case MODUL_OFFEN:
                if (event == Event.LABOR_TEIL_1_BEGINNEN) currentState = State.LABOR_TEIL_1;
                break;
            case LABOR_TEIL_1:
                if (event == Event.LABOR_TEIL_1_ABGESCHLOSSEN) currentState = State.LABOR_TEIL_2;
                break;
            // Weitere Transitionen...
        }
    }
}

// Beispiel 2: Einfache Zustandsmaschine für eine GUI
public enum State {
    LOGIN, DASHBOARD, MEMBER_MANAGEMENT
}

public class StateMachineImpl {
    private State currentState;
    
    public void setState(State state) {
        this.currentState = state;
    }
    
    public void handleEvent(Event event) {
        // Logik zur Zustandsänderung basierend auf Events
    }
}
```
