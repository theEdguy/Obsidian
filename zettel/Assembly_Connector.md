---
id: a676212d-0f65-4eab-8ace-4fae11326e58
title: "Assembly Connector"
date: 2026-06-23
tags:
  - software_engineering
  - verbindung
  - komponenten
  - draft
source: "software_engineering_kapitel_10"
---

# [[Assembly Connector]]

- **Kernkonzept:** Ein Assembly Connector ist ein Verbindungselement in der komponentenbasierten Softwareentwicklung, das zwei oder mehrere Komponenten über deren Schnittstellen miteinander verbindet, um eine funktionale Zusammenarbeit zu ermöglichen. Er stellt sicher, dass eine Komponente die Dienste einer anderen Komponente nutzen kann, indem er die bereitgestellten und benötigten Interfaces verknüpft.
- **Nutzen & Zweck:** Der Assembly Connector existiert, um die lose Kopplung und Wiederverwendbarkeit von Komponenten in einem Softwaresystem zu fördern. Er löst das Problem der direkten Abhängigkeiten zwischen Komponenten, indem er eine standardisierte und flexible Verbindung schafft. Dadurch können Komponenten unabhängig voneinander entwickelt, getestet und ausgetauscht werden, ohne die Gesamtstruktur des Systems zu beeinträchtigen. Dies erleichtert die Modularisierung und Wartbarkeit komplexer Systeme.
- **Abgrenzung & Grenzen:** Ein Assembly Connector sollte nicht genutzt werden, wenn eine enge Kopplung zwischen Komponenten erforderlich ist, beispielsweise bei hochperformanten Systemen, bei denen der Overhead der Schnittstellenkommunikation vermieden werden muss. Er unterscheidet sich von einem Delegation Connector, der externe Schnittstellen mit internen Subkomponenten verbindet, um die Implementierung zu kapseln. Während der Assembly Connector die Zusammenarbeit zwischen eigenständigen Komponenten organisiert, dient der Delegation Connector der internen Strukturierung einer einzelnen Komponente. Zudem ist der Assembly Connector ungeeignet für Szenarien, in denen dynamische oder zur Laufzeit veränderbare Verbindungen benötigt werden.
- **Beispiel / Code:** ```java
// Beispiel für einen Assembly Connector in UML-ähnlicher Notation (Java-ähnlich)
interface MitgliedVerwaltung {
    void hinzufuegenMitglied(Mitglied mitglied);
    Mitglied findeMitglied(String id);
}

interface DatenbankConnector {
    void speichern(Object daten);
    Object laden(String id);
}

// Komponente A: Implementiert MitgliedVerwaltung und benötigt DatenbankConnector
class MitgliedVerwaltungImpl implements MitgliedVerwaltung {
    private DatenbankConnector dbConnector;
    
    // Assembly Connector: Verbindung über Schnittstelle
    public MitgliedVerwaltungImpl(DatenbankConnector dbConnector) {
        this.dbConnector = dbConnector;
    }
    
    @Override
    public void hinzufuegenMitglied(Mitglied mitglied) {
        dbConnector.speichern(mitglied);
    }
    
    @Override
    public Mitglied findeMitglied(String id) {
        return (Mitglied) dbConnector.laden(id);
    }
}

// Komponente B: Implementiert DatenbankConnector
class DatenbankConnectorImpl implements DatenbankConnector {
    @Override
    public void speichern(Object daten) {
        // Logik zum Speichern in der Datenbank
    }
    
    @Override
    public Object laden(String id) {
        // Logik zum Laden aus der Datenbank
        return new Mitglied();
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c1a2a
- **Vorgänger / Parent:** [[Konnektoren]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
