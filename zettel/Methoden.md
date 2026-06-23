---
id: 07eb0b28-63b9-4eeb-aeef-3ec6d81e93ef
title: "Methoden"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - programmierung
  - draft
source: "software_engineering_kapitel_03"
---

# [[Methoden]]

- **Kernkonzept:** Methoden sind definierte Operationen innerhalb einer Klasse in der objektorientierten Programmierung, die das Verhalten von Objekten beschreiben und steuern. Sie kapseln Funktionalitäten, die auf den Attributen der Klasse operieren oder mit anderen Objekten interagieren.
- **Nutzen & Zweck:** Methoden existieren, um die Wiederverwendbarkeit von Code zu erhöhen, die Komplexität durch Modularisierung zu reduzieren und die Kapselung von Daten zu gewährleisten. Sie lösen das Problem, dass Funktionalitäten direkt mit den Daten verknüpft werden müssen, um eine klare und wartbare Struktur in der Softwareentwicklung zu schaffen. Durch Methoden wird die Kommunikation zwischen Objekten standardisiert und die Logik zentralisiert.
- **Abgrenzung & Grenzen:** Methoden sollten nicht genutzt werden, wenn die Funktionalität trivial ist oder keine Wiederverwendung oder Kapselung erforderlich ist, da dies unnötige Komplexität schafft. Alternativ können prozedurale Ansätze oder funktionale Programmierung in solchen Fällen effizienter sein. Methoden unterscheiden sich von freien Funktionen dadurch, dass sie immer an eine Klasse oder ein Objekt gebunden sind und auf deren Zustand zugreifen können.
- **Beispiel / Code:** ```java
class Mitglied {
    private String name;
    private int leistung;

    // Methode zur Berechnung der Leistungsprognose
    public int leistungsprognose(int zusatzPunkte) {
        return this.leistung + zusatzPunkte;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1d2
- **Vorgänger / Parent:** [[Objektorientierung_als_durchgängiges_Stilmittel]]
- **Folgezettel / Unterzettel:**
  - [[Operationen]]
  - [[Polymorphie]]
- **Querverweise:** keine
