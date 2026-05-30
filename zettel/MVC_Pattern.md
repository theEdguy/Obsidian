---
id: 8fd98765-6ee8-4230-a616-c547d76c486b
title: "MVC_Pattern"
date: 2026-05-30
tags:
  - software_engineering
  - architekturmuster
  - design_pattern
  - draft
source: "SWE Slides (Folien 1-15)"
---

# [[MVC_Pattern]]

- **Kernkonzept:** Ein [[Architekturmuster]], das die [[Anwendung]] in drei [[Komponente|Komponenten]] unterteilt: [[Model]] (Daten und [[Logik]]), [[View]] (Darstellung) und [[Controller]] (Steuerung).
- **Nutzen & Zweck:** Fördert [[Trennung_der_Belange|Trennung der Belange]] und [[Wiederverwendbarkeit]], indem [[Daten]], [[Darstellung]] und [[Steuerung]] entkoppelt werden. Erleichtert [[Wartung]] und [[Erweiterung]].
- **Abgrenzung & Grenzen:** Kann zu [[Überkomplexität]] führen, wenn die [[Anwendung]] sehr einfach ist. Erfordert [[Disziplin]], um die [[Trennung_der_Belange|Trennung der Belange]] konsequent umzusetzen. Nicht ideal für [[Echtzeit-Systeme]].
- **Beispiel / Code:** ```java
// Beispiel für [[MVC_Pattern]]-Struktur
class Model {
    private String daten;
    
    String getDaten() {
        return daten;
    }
}

class View {
    void anzeigen(String daten) {
        System.out.println("Anzeige: " + daten);
    }
}

class Controller {
    private Model model;
    private View view;
    
    void aktualisieren() {
        view.anzeigen(model.getDaten());
    }
}
```
