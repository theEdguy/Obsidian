---
id: ec68ab2c-928a-42cb-96bc-4c760ed79b94
title: "Quadrat-Rechteck-Problem"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - anti-pattern
  - draft
source: "software_engineering_kapitel_04"
---

# [[Quadrat-Rechteck-Problem]]

- **Kernkonzept:** Das Quadrat-Rechteck-Problem beschreibt ein Anti-Pattern in der objektorientierten Programmierung, bei dem eine Vererbungsbeziehung zwischen Quadrat und Rechteck zu semantischen und logischen Widersprüchen führt, da ein Quadrat zwar ein spezielles Rechteck ist, aber nicht alle Operationen eines Rechtecks sinnvoll auf ein Quadrat anwendbar sind (z. B. unabhängiges Verändern von Länge und Breite).
- **Nutzen & Zweck:** Dieses Konzept dient als Warnbeispiel, um die Grenzen der Vererbung in der Objektorientierung aufzuzeigen. Es verdeutlicht, dass eine rein hierarchische 'Ist-ein'-Beziehung (Spezialisierung) nicht immer ausreicht, um reale Domänen korrekt abzubilden. Stattdessen soll es Entwickler dazu anregen, Alternativen wie Komposition oder Schnittstellen zu prüfen, um unerwünschte Seiteneffekte zu vermeiden.
- **Abgrenzung & Grenzen:** Das Quadrat-Rechteck-Problem sollte nicht genutzt werden, wenn die Vererbungshierarchie keine Verletzung des Liskovschen Substitutionsprinzips (LSP) verursacht. Es unterscheidet sich von sinnvollen Vererbungsbeziehungen dadurch, dass die Unterklasse (Quadrat) die Vorbedingungen der Oberklasse (Rechteck) verschärft oder Nachbedingungen abschwächt. Alternativen wie eine gemeinsame Oberklasse mit einer Methode `istQuadrat()` oder die Verwendung von Interfaces sind oft besser geeignet.
- **Beispiel / Code:** ```java
// Problembeispiel: Vererbung führt zu inkonsistentem Verhalten
class Rechteck {
    protected int a, b;
    
    public Rechteck(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    public void stretch(int i, int j) {
        this.a += i;
        this.b += j;
    }
}

class Quadrat extends Rechteck {
    public Quadrat(int seite) {
        super(seite, seite);
    }
    
    @Override
    public void stretch(int i, int j) {
        // Verletzung der Rechteck-Logik: Seiten müssen gleich bleiben!
        this.a += i;
        this.b += i; // j wird ignoriert
    }
}

// Nutzung führt zu unerwartetem Verhalten:
Quadrat q = new Quadrat(3);
q.stretch(1, 2); // Ergebnis: a=4, b=4 (nicht a=4, b=5)
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b1
- **Vorgänger / Parent:** [[Vererbungsbeispiel]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
