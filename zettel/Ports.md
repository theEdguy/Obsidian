---
id: 99aa551f-1544-4aae-b64b-a1e381dbc5f9
title: "Ports"
date: 2026-06-23
tags:
  - software_engineering
  - schnittstelle
  - interaktion
  - draft
source: "software_engineering_kapitel_10"
---

# [[Ports]]

- **Kernkonzept:** Ein Port ist ein dedizierter Interaktionspunkt einer Komponente mit ihrer Umgebung, der durch die Menge der bereitgestellten und benötigten Schnittstellen (Interfaces) beschrieben wird. Er definiert klar, wie eine Komponente mit anderen Komponenten kommunizieren kann, ohne deren interne Implementierung offenzulegen.
- **Nutzen & Zweck:** Ports existieren, um die Kommunikation zwischen Komponenten in einem Softwaresystem klar und standardisiert zu gestalten. Sie lösen das Problem der unkontrollierten Abhängigkeiten, indem sie explizite Schnittstellen definieren, die sowohl die angebotenen als auch die benötigten Dienste einer Komponente kapseln. Dadurch wird die Wiederverwendbarkeit, Austauschbarkeit und Wartbarkeit von Komponenten verbessert, da Änderungen an der internen Implementierung keine Auswirkungen auf die Nutzung durch andere Komponenten haben.
- **Abgrenzung & Grenzen:** Ports sollten nicht genutzt werden, wenn die Kommunikation zwischen Komponenten trivial oder stark gekoppelt ist, da der Overhead der Schnittstellendefinition in solchen Fällen unnötig ist. Alternativen wie direkte Methodenaufrufe oder einfache Nachrichtenübermittlung können hier effizienter sein. Zudem unterscheiden sich Ports von klassischen Schnittstellen (Interfaces) dadurch, dass sie nicht nur die angebotenen Dienste beschreiben, sondern auch die benötigten Dienste einer Komponente explizit machen. Sie sind somit spezifischer und kontextabhängiger als allgemeine Interfaces.
- **Beispiel / Code:** ```java
// Beispiel für eine Komponente mit Ports in UML-ähnlicher Notation (Java-Interface)
public interface MitgliedVerwaltungPort {
    // Bereitgestellte Schnittstelle (provided interface)
    Mitglied getMitgliedById(String id);
    void speichereMitglied(Mitglied mitglied);

    // Benötigte Schnittstelle (required interface)
    void setDatenbankPort(DatenbankPort datenbank);
}

public interface DatenbankPort {
    Mitglied ladeMitglied(String id);
    void persistMitglied(Mitglied mitglied);
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1a1
- **Vorgänger / Parent:** [[Komponenten]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
