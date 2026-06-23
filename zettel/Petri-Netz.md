---
id: 6fa14e05-6884-465d-a6b7-31c08795013a
title: "Petri-Netz"
date: 2026-06-23
tags:
  - software_engineering
  - modellierung
  - prozess
  - draft
source: "software_engineering_kapitel_08"
---

# [[Petri-Netz]]

- **Kernkonzept:** Ein Petri-Netz ist ein mathematisches Modell zur Beschreibung und Analyse von verteilten Systemen und Prozessen, das aus Stellen, Transitionen und gerichteten Kanten besteht. Es ermöglicht die Darstellung von Nebenläufigkeit, Synchronisation und Konflikten in dynamischen Abläufen.
- **Nutzen & Zweck:** Petri-Netze existieren, um komplexe, parallele und nicht-deterministische Prozesse formal zu modellieren und zu analysieren. Sie lösen das Problem der unklaren Darstellung von Abhängigkeiten, Ressourcenkonflikten und Zustandsübergängen in verteilten Systemen, indem sie eine präzise, grafische und mathematisch fundierte Notation bieten. Dadurch lassen sich Deadlocks, Engpässe oder unerwünschte Systemzustände frühzeitig erkennen und vermeiden.
- **Abgrenzung & Grenzen:** Petri-Netze sollten nicht genutzt werden, wenn der Fokus auf sequenziellen, einfachen Abläufen liegt, da ihr Formalismus dann unnötig komplex wirkt. Im Vergleich zu Aktivitätsdiagrammen der UML sind sie weniger intuitiv für die Modellierung von Geschäftsprozessen mit klaren Verantwortlichkeiten (z. B. Swimlanes). Zudem eignen sie sich weniger für die Darstellung von Datenflüssen oder objektorientierten Strukturen, da sie primär auf Kontrollflüsse und Zustandsübergänge spezialisiert sind. Für rein lineare Abläufe sind Flussdiagramme oder einfache Zustandsautomaten oft ausreichend.
- **Beispiel / Code:** ```java
// Beispiel: Einfaches Petri-Netz in einer Java-ähnlichen Notation (vereinfacht)
class PetriNet {
    private Map<String, Integer> places;  // Stellen mit Token-Anzahl
    private List<Transition> transitions; // Transitionen mit Vor-/Nachbedingungen
    
    public boolean fireTransition(String transitionName) {
        Transition t = findTransition(transitionName);
        if (t.canFire(places)) {  // Prüft, ob alle Vorbedingungen erfüllt sind
            t.fire(places);       // Konsumiert/erzeugt Token
            return true;
        }
        return false;
    }
}

class Transition {
    private Map<String, Integer> inputPlaces;  // Vorbedingungen (Stellen → Token)
    private Map<String, Integer> outputPlaces; // Nachbedingungen (Stellen → Token)
    
    public boolean canFire(Map<String, Integer> places) {
        return inputPlaces.entrySet().stream()
            .allMatch(e -> places.getOrDefault(e.getKey(), 0) >= e.getValue());
    }
    
    public void fire(Map<String, Integer> places) {
        inputPlaces.forEach((place, tokens) ->
            places.put(place, places.get(place) - tokens));
        outputPlaces.forEach((place, tokens) ->
            places.put(place, places.getOrDefault(place, 0) + tokens));
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 7
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Petri-Netz_Semantik]]
- **Querverweise:**
  - [[Aktivitätsdiagramm_Semantik]]
