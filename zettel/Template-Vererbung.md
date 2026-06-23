---
id: e5bdc644-1a1b-4805-8e17-767c17584b3a
title: "Template-Vererbung"
date: 2026-06-23
tags:
  - software_engineering
  - objektorientierung
  - design
  - draft
source: "software_engineering_kapitel_04"
---

# [[Template-Vererbung]]

- **Kernkonzept:** Template-Vererbung in der objektorientierten Programmierung ermöglicht die Definition von Klassen mit formalen Parametern (Templates), die durch Bindung dieser Parameter zu konkreten Klassen instantiiert werden. Sie erweitert die Wiederverwendbarkeit von Code, indem sie generische Strukturen für eine Familie ähnlicher Klassen bereitstellt.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der Code-Duplikation bei strukturell ähnlichen Klassen, die sich nur in bestimmten Datentypen oder Implementierungsdetails unterscheiden. Durch Templates können Entwickler generische Lösungen entwerfen, die durch Parameterbindung an spezifische Anforderungen angepasst werden, ohne die Grundlogik neu implementieren zu müssen. Es fördert die Typsicherheit und reduziert Wartungsaufwand.
- **Abgrenzung & Grenzen:** Template-Vererbung sollte nicht genutzt werden, wenn die zu modellierenden Klassen keine strukturelle Ähnlichkeit aufweisen oder wenn die Komplexität der generischen Lösung den Nutzen übersteigt. Im Gegensatz zur klassischen Vererbung ("Ist-ein-Beziehung") ermöglicht Template-Vererbung keine direkte Polymorphie zwischen den gebundenen Klassen. Zudem kann übermäßiger Einsatz zu schwer verständlichem Code führen, insbesondere wenn die Template-Parameter nicht intuitiv sind. Alternativen wie Komposition oder einfache Vererbung sind oft besser geeignet, wenn keine generische Struktur benötigt wird.
- **Beispiel / Code:** ```java
// Definition eines generischen Templates in UML-ähnlicher Notation
class Box<T> {
    private T content;
    
    public void setContent(T content) {
        this.content = content;
    }
    
    public T getContent() {
        return content;
    }
}

// Bindung des Templates zu konkreten Klassen
class StringBox extends Box<String> {}
class IntegerBox extends Box<Integer> {}

// Verwendung
StringBox stringBox = new StringBox();
stringBox.setContent("Hallo Welt");
IntegerBox integerBox = new IntegerBox();
integerBox.setContent(42);
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1e1
- **Vorgänger / Parent:** [[Vererbungsgrenzen]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Generics]]
  - [[Parametrisierte_Klassen]]
