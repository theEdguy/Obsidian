---
id: b0f5e032-6062-41cd-b1e9-3ed61acae37f
title: "Methodische Durchgängigkeit"
date: 2026-06-23
tags:
  - software_engineering
  - prozess
  - draft
source: "software_engineering_kapitel_03"
---

# [[Methodische Durchgängigkeit]]

- **Kernkonzept:** Methodische Durchgängigkeit bezeichnet die konsistente und nahtlose Übertragung von Analyseergebnissen (Problemraum) in die Implementierung (Lösungsraum) durch einheitliche Konzepte, Modelle und Notationen, insbesondere in der objektorientierten Softwareentwicklung.
- **Nutzen & Zweck:** Dieses Konzept löst das Problem der Brüche zwischen Anforderungen, Design und Implementierung, indem es eine durchgängige Modellierung ermöglicht. Es verbessert die Kommunikation zwischen Stakeholdern, reduziert Missverständnisse und erhöht die Qualität und Konsistenz des Softwareprodukts. Durch die einheitliche Darstellung von Objekten, Beziehungen und Modellen wird sichergestellt, dass die reale Welt (Problemraum) präzise im Code (Lösungsraum) abgebildet wird.
- **Abgrenzung & Grenzen:** Methodische Durchgängigkeit sollte nicht genutzt werden, wenn das Projekt stark explorativ oder unklar in den Anforderungen ist, da starre Modelle die Flexibilität einschränken können. Alternativen wie prototypische Entwicklung oder agile Methoden ohne strikte Modellbindung eignen sich besser für hochdynamische oder innovative Vorhaben. Zudem ist das Konzept weniger sinnvoll bei kleinen Projekten mit geringer Komplexität, da der Aufwand für durchgängige Modellierung den Nutzen übersteigen kann.
- **Beispiel / Code:** ```java
// Analyse/Design: UML-Klasse 'Mitglied' mit Attributen und Operation
// -------------------------------------------------------------
// | Mitglied                                               |
// |--------------------------------------------------------|
// | name: Text                                             |
// | adresse: Text                                          |
// | alter: Datum                                           |
// | leistung: Punkte                                       |
// |--------------------------------------------------------|
// | +leistungsprognose(Datum): Punkte                       |
// -------------------------------------------------------------

// Implementierung: Entsprechende Java-Klasse
class Mitglied {
    private String name;
    private String adresse;
    private Date alter;
    private int leistung;
    
    public int leistungsprognose(Date datum) {
        // Berechnung basierend auf historischen Daten
        return this.leistung * 2; // Beispielhafte Logik
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 4
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Problemraum]]
  - [[Lösungsraum]]
  - [[Kommunikation_zwischen_Entwicklern_und_Anwendern]]
- **Querverweise:** keine
