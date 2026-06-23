---
id: bc168fe9-63f6-439b-b134-9b392274aecf
title: "Säulen der Objektorientierung"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - geschichte
  - draft
source: "software_engineering_kapitel_03"
---

# [[Säulen der Objektorientierung]]

- **Kernkonzept:** Die Säulen der Objektorientierung bilden die drei grundlegenden Prinzipien, auf denen objektorientierte Softwareentwicklung basiert: Natürliche Modellierung, Sharing (gemeinsame Nutzung von Eigenschaften) und Abstrakte Datentypen (Kapselung von Zustand und Verhalten). Diese Säulen definieren die Art und Weise, wie Objekte entworfen, strukturiert und miteinander interagieren.
- **Nutzen & Zweck:** Die Säulen der Objektorientierung existieren, um eine systematische und intuitive Abbildung realer Probleme in Software zu ermöglichen. Sie lösen das Problem der Komplexitätsbewältigung, indem sie eine klare Trennung zwischen Daten und Funktionen vermeiden und stattdessen eine ganzheitliche Sicht auf Objekte fördern. Dadurch wird die Wiederverwendbarkeit, Wartbarkeit und Verständlichkeit von Software verbessert, insbesondere bei großen und langlebigen Systemen.
- **Abgrenzung & Grenzen:** Diese Prinzipien sollten nicht genutzt werden, wenn die Problemstellung stark funktional oder prozedural geprägt ist, z. B. bei mathematischen Algorithmen oder reinen Datenverarbeitungsaufgaben ohne Zustandsverwaltung. Alternativen wie funktionale Programmierung oder prozedurale Ansätze können hier effizienter sein. Zudem ist Objektorientierung weniger geeignet für Systeme mit extrem hohen Performance-Anforderungen, bei denen die Abstraktionsebenen zu Overhead führen. Die Säulen unterscheiden sich von anderen Paradigmen durch ihre Betonung auf Kapselung, Vererbung und Polymorphie statt auf sequentielle Abläufe oder unveränderliche Daten.
- **Beispiel / Code:** ```java
// Beispiel für Abstrakte Datentypen (Kapselung) und Sharing (Vererbung)
class Rectangle {
    private int width;
    private int height;
    
    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }
    
    public int getArea() {
        return width * height;
    }
}

// Sharing durch Vererbung
class Square extends Rectangle {
    public Square(int side) {
        super(side, side);
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Natürliche_Modellierung]]
  - [[Sharing]]
  - [[Abstrakte_Datentypen]]
- **Querverweise:** keine
