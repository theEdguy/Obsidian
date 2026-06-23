---
id: a021e876-fab1-41bc-871f-d11034fceea8
title: "Objektkomposition vs. Vererbung"
date: 2026-06-23
tags:
  - software_engineering
  - design
  - objektorientierung
  - vererbung
  - draft
source: "software_engineering_kapitel_14"
---

# [[Objektkomposition vs. Vererbung]]

- **Kernkonzept:** Objektkomposition und Vererbung sind zwei zentrale Mechanismen der objektorientierten Programmierung, um Beziehungen zwischen Klassen herzustellen. Während Vererbung eine 'Ist-ein'-Beziehung durch Ableitung von einer Basisklasse schafft, ermöglicht Komposition eine 'Hat-ein'-Beziehung durch Einbettung von Objekten anderer Klassen.
- **Nutzen & Zweck:** Das Konzept löst das Problem der starren Kopplung und mangelnden Flexibilität, die durch tiefe Vererbungshierarchien entstehen kann. Objektkomposition fördert die Wiederverwendbarkeit und Austauschbarkeit von Komponenten zur Laufzeit, indem sie die Implementierung hinter Schnittstellen versteckt. Dies ermöglicht eine dynamischere Anpassung von Software an sich ändernde Anforderungen, ohne bestehende Klassenstrukturen zu verändern.
- **Abgrenzung & Grenzen:** Vererbung sollte nicht genutzt werden, wenn die Beziehung zwischen Klassen zur Laufzeit änderbar sein muss oder wenn die abgeleitete Klasse nur einen Teil der Funktionalität der Basisklasse benötigt. Komposition ist ungeeignet, wenn eine strikte 'Ist-ein'-Beziehung erforderlich ist oder wenn die Performance kritisch ist, da indirekte Aufrufe über Schnittstellen Overhead verursachen können. Zudem kann übermäßige Komposition zu unübersichtlichen Objektgraphen führen, die schwer zu warten sind.
- **Beispiel / Code:** ```java
// Beispiel für Vererbung (starre Beziehung zur Compile-Zeit)
class Fahrzeug {
    void fahren() { System.out.println("Fahrzeug bewegt sich"); }
}

class Auto extends Fahrzeug {
    @Override
    void fahren() { System.out.println("Auto fährt"); }
}

// Beispiel für Komposition (flexible Beziehung zur Laufzeit)
interface Antrieb {
    void bewegen();
}

class ElektroAntrieb implements Antrieb {
    public void bewegen() { System.out.println("Elektromotor läuft"); }
}

class FahrzeugMitKomposition {
    private Antrieb antrieb;
    
    public FahrzeugMitKomposition(Antrieb antrieb) {
        this.antrieb = antrieb;
    }
    
    void fahren() {
        antrieb.bewegen();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1b
- **Vorgänger / Parent:** [[Software_Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Vorteile_der_Objektkomposition]]
  - [[Nachteile_der_Vererbung]]
  - [[Flexibilität_durch_Komposition]]
- **Querverweise:**
  - [[Schnittstellendesign]]
  - [[Polymorphie]]
