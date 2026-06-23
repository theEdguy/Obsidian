---
id: 5bbbf34e-7a73-42ec-bfbe-592b7a2c2889
title: "Zusicherungen"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - modellierung
  - draft
source: "software_engineering_kapitel_03"
---

# [[Zusicherungen]]

- **Kernkonzept:** Zusicherungen (auch Invarianten, Vor- und Nachbedingungen genannt) sind formale Bedingungen, die den Zustand und das Verhalten von Objekten in der objektorientierten Modellierung und Programmierung einschränken und sicherstellen. Sie definieren Regeln, die Objekte einer Klasse stets erfüllen müssen, um korrekt zu funktionieren.
- **Nutzen & Zweck:** Zusicherungen existieren, um die Konsistenz und Korrektheit von Objekten während des gesamten Lebenszyklus zu gewährleisten. Sie lösen das Problem, dass Objekte durch fehlerhafte Operationen oder externe Einflüsse in einen ungültigen Zustand geraten können. Durch Zusicherungen wird sichergestellt, dass Attribute bestimmte Wertebereiche einhalten, Operationen nur unter definierten Bedingungen ausgeführt werden und Beziehungen zwischen Objekten stets gültig bleiben. Dies verbessert die Robustheit, Wartbarkeit und Nachvollziehbarkeit von Software, da Fehler frühzeitig erkannt und dokumentiert werden.
- **Abgrenzung & Grenzen:** Zusicherungen sollten nicht genutzt werden, wenn die Performance kritisch ist, da ihre Überprüfung zur Laufzeit zusätzlichen Overhead verursacht. Sie unterscheiden sich von einfachen Validierungen oder Fehlerbehandlungen, da sie nicht nur Fehler erkennen, sondern auch die logische Integrität des Systems garantieren. Im Gegensatz zu Kommentaren oder informellen Dokumentationen sind Zusicherungen maschinenlesbar und können automatisiert überprüft werden. Allerdings ersetzen sie keine umfassende Teststrategie, da sie nur definierte Bedingungen prüfen, aber keine unerwarteten Fehler abfangen. In dynamischen oder stark veränderlichen Systemen können zu starre Zusicherungen die Flexibilität einschränken.
- **Beispiel / Code:** ```java
class Mitglied {
    private String name;
    private int alter;
    private int leistung;

    // Zusicherung (Invariante): Alter muss zwischen 0 und 120 liegen
    public void setAlter(int alter) {
        assert alter >= 0 && alter <= 120 : "Ungültiges Alter";
        this.alter = alter;
    }

    // Zusicherung (Vorbedingung): Leistung darf nicht negativ sein
    public void setLeistung(int leistung) {
        if (leistung < 0) {
            throw new IllegalArgumentException("Leistung darf nicht negativ sein");
        }
        this.leistung = leistung;
    }

    // Zusicherung (Nachbedingung): Leistungsprognose muss nicht-negativ sein
    public int leistungsprognose(int tage) {
        int prognose = this.leistung * tage;
        assert prognose >= 0 : "Leistungsprognose darf nicht negativ sein";
        return prognose;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d3a
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
