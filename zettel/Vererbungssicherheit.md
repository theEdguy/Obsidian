---
id: f7ef137c-9b9d-4e94-a27e-74229077ce0f
title: "Vererbungssicherheit"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - design
  - draft
source: "software_engineering_kapitel_04"
---

# [[Vererbungssicherheit]]

- **Kernkonzept:** Vererbungssicherheit bezeichnet die Gewährleistung, dass Subklassen die Eigenschaften und Verhaltensweisen ihrer Oberklassen korrekt erweitern oder überschreiben, ohne deren Semantik zu verletzen. Dies sichert die Einhaltung des Substitutionsprinzips (Liskov Substitution Principle), wonach Instanzen von Unterklassen überall dort einsetzbar sein müssen, wo Instanzen der Oberklasse erwartet werden.
- **Nutzen & Zweck:** Vererbungssicherheit existiert, um Designfehler in objektorientierten Systemen zu vermeiden, die durch unsachgemäße Vererbungshierarchien entstehen. Sie löst das konkrete Problem, dass Subklassen die Konsistenz und Integrität der Oberklasse untergraben können, indem sie deren Invarianten brechen oder unerwartetes Verhalten einführen. Dies führt zu robusteren, wartbaren und fehlerfreien Softwaresystemen, da die Austauschbarkeit von Objekten innerhalb der Vererbungshierarchie garantiert wird.
- **Abgrenzung & Grenzen:** Vererbungssicherheit sollte nicht genutzt werden, wenn die Beziehung zwischen Klassen keine echte 'Ist-ein'-Beziehung darstellt oder wenn die Subklasse die Invarianten der Oberklasse nicht einhalten kann. Alternativen wie Komposition oder Delegation sind vorzuziehen, wenn die Vererbung zu starren oder unnatürlichen Hierarchien führt. Beispielsweise ist die Vererbung von 'Quadrat' von 'Rechteck' problematisch, da ein Quadrat nicht alle Operationen eines Rechtecks (z. B. unabhängiges Strecken der Seiten) unterstützen kann, ohne seine Invarianten zu verletzen.
- **Beispiel / Code:** ```java
// Problem: Vererbung von Quadrat von Rechteck verletzt das Substitutionsprinzip
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
        // Verletzung der Rechteck-Invariante: Seiten müssen unabhängig änderbar sein
        super.stretch(i, i); // Beide Seiten werden gleich verändert
    }
}

// Lösung: Komposition statt Vererbung
class RechteckSicher {
    private int a, b;
    
    public RechteckSicher(int a, int b) {
        this.a = a;
        this.b = b;
    }
    
    public boolean istQuadrat() {
        return a == b;
    }
    
    public void stretch(int i, int j) {
        this.a += i;
        this.b += j;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b2
- **Vorgänger / Parent:** [[Vererbungsbeispiel]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
