---
id: 10a35777-22f3-4645-9bbc-3599d8a45e02
title: "Complete_Vererbung"
date: 2026-06-23
tags:
  - software_engineering
  - oop
  - vererbung
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_04"
---

# [[Complete_Vererbung]]

- **Kernkonzept:** [[Complete_Vererbung]] beschreibt eine [[Vererbungsbeziehung|Vererbungsbeziehung]] in der [[Objektorientierte_Programmierung|objektorientierten Programmierung]] und [[UML]], bei der alle möglichen [[Unterklasse|Unterklassen]] einer [[Oberklasse]] explizit modelliert sind und keine [[Instanz|Instanzen]] außerhalb dieser [[Unterklasse|Unterklassen]] existieren. Im Gegensatz dazu kennzeichnet [[Incomplete_Vererbung]] eine [[Generalisierung]], bei der nicht alle möglichen [[Spezialisierung|Spezialisierungen]] der [[Oberklasse]] bekannt oder modelliert sind, sodass zukünftige Erweiterungen möglich bleiben.
- **Nutzen & Zweck:** [[Complete_Vererbung]] stellt sicher, dass alle [[Variante|Varianten]] einer [[Oberklasse]] bekannt und modelliert sind, was die [[Vollständigkeit]] und [[Konsistenz]] des [[Modell]]s erhöht. Dies ist besonders nützlich für geschlossene [[Kategorie|Kategorien]] oder [[Enumeration|Enumerationen]], bei denen keine spätere Erweiterung vorgesehen ist. Der Ansatz löst das Problem unvollständiger oder erweiterbarer [[Vererbungshierarchie|Hierarchien]], indem er klare [[Modellierungsregel|Modellierungsregeln]] schafft und unerwünschte Lücken oder Erweiterungen verhindert. [[Incomplete_Vererbung]] hingegen fördert [[Flexibilität]] und [[Erweiterbarkeit]], indem sie offenlässt, ob zukünftig weitere [[Unterklasse|Unterklassen]] hinzugefügt werden können, ohne das [[Modell]] grundlegend zu ändern. Dies verbessert die [[Wartbarkeit]] und [[Anpassungsfähigkeit]] von [[Klassendiagramm|Klassendiagrammen]], insbesondere in frühen Phasen der [[Analyse]] oder bei sich ändernden Anforderungen.
- **Abgrenzung & Grenzen:** [[Complete_Vererbung]] sollte nicht genutzt werden, wenn die [[Vererbungshierarchie]] dynamisch erweiterbar sein muss oder wenn nicht alle möglichen [[Spezialisierung|Spezialisierungen]] zum Zeitpunkt der [[Modellierung]] bekannt sind. Im Gegensatz zur [[Incomplete_Vererbung]], die [[Erweiterbarkeit]] und [[Flexibilität]] fördert, ist [[Complete_Vererbung]] starr und schließt zukünftige [[Unterklasse|Unterklassen]] aus. Sie ist ungeeignet, wenn die [[Oberklasse]] direkte [[Instanz|Instanzen]] besitzen soll, die nicht durch [[Unterklasse|Unterklassen]] repräsentiert werden. [[Incomplete_Vererbung]] sollte vermieden werden, wenn die [[Hierarchie]] vollständig und abgeschlossen sein muss, da dies zu Missverständnissen führen kann. Die Wahl zwischen beiden Ansätzen hängt von den Anforderungen an die [[Modellierung]], die zukünftige [[Wartbarkeit]] und die Notwendigkeit einer geschlossenen oder offenen [[Hierarchie]] ab. Zudem ist [[Incomplete_Vererbung]] nicht mit [[Disjunkte_Vererbung|disjunkten]] oder [[Überlappende_Vererbung|überlappenden]] [[Vererbungsbeziehung|Vererbungsbeziehungen]] zu verwechseln, da diese sich auf die Überschneidung von [[Instanz|Instanzen]] beziehen, nicht auf die [[Vollständigkeit]] der [[Hierarchie]].
- **Beispiel / Code:** ```java
// Beispiel für Complete_Vererbung in Java: Alle Vereinsmanager sind entweder Vorstand oder Abteilungsleiter
public abstract class Vereinsmanager {}
public class Vorstand extends Vereinsmanager {}
public class Abteilungsleiter extends Vereinsmanager {}

// Beispiel für Incomplete_Vererbung: Weitere Mitgliedstypen können später hinzugefügt werden
public abstract class Mitglied {}
public class Junior extends Mitglied {}
public class Dame extends Mitglied {}
```

```uml
// UML-Beispiel für Complete_Vererbung mit {complete}-Constraint
class Oberklasse {
    {abstract}
}

class Unterklasse1 {
    -- Spezialisierung 1
}

class Unterklasse2 {
    -- Spezialisierung 2
}

Oberklasse <|-- Unterklasse1
Oberklasse <|-- Unterklasse2
{complete}

// UML-Beispiel für Incomplete_Vererbung mit {incomplete}-Constraint
class Verein {
  // Oberklasse mit gemeinsamen Attributen/Operationen
}

class Jugendteam {
  // Spezialisierung
}

class Seniorteam {
  // Spezialisierung
}

Verein <|-- Jugendteam
Verein <|-- Seniorteam
{incomplete}
```

*Erklärung:* In den Beispielen sind bei [[Complete_Vererbung]] alle [[Instanz|Instanzen]] der [[Oberklasse]] (`Vereinsmanager` bzw. `Oberklasse`) ausschließlich durch die definierten [[Unterklasse|Unterklassen]] (`Vorstand`, `Abteilungsleiter` bzw. `Unterklasse1`, `Unterklasse2`) abgedeckt. Bei [[Incomplete_Vererbung]] (`Verein`) können später weitere [[Unterklasse|Unterklassen]] (z. B. `Damenteam`) hinzugefügt werden, ohne das [[Modell]] zu brechen.

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c5
- **Vorgänger / Parent:** [[Vererbungssemantik]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
