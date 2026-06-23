---
id: 3e4b0f60-6604-4bca-80f4-f29daee6ef69
title: "Technische Anforderungen"
date: 2026-06-23
tags:
  - software_engineering
  - anforderungen
  - technik
  - draft
source: "software_engineering_kapitel_06"
---

# [[Technische Anforderungen]]

- **Kernkonzept:** Technische Anforderungen sind spezifische Vorgaben zu Programmiersprachen, Plattformen, Hardware, Frameworks oder anderen technischen Aspekten, die die Umsetzung eines Softwareprojekts direkt beeinflussen. Sie definieren die technischen Rahmenbedingungen, innerhalb derer die Lösung entwickelt wird.
- **Nutzen & Zweck:** Technische Anforderungen existieren, um Klarheit über die technischen Voraussetzungen und Einschränkungen eines Projekts zu schaffen. Sie lösen das Problem der Uneinigkeit oder Unklarheit über die zu verwendenden Technologien, verhindern spätere Kompatibilitätsprobleme und stellen sicher, dass alle Projektbeteiligten von denselben technischen Grundlagen ausgehen. Dadurch wird die Planungssicherheit erhöht und das Risiko von Fehlentwicklungen reduziert.
- **Abgrenzung & Grenzen:** Technische Anforderungen sollten nicht mit funktionalen oder nicht-funktionalen Anforderungen verwechselt werden, da sie keine direkten Eigenschaften des Endprodukts beschreiben, sondern die Mittel zu dessen Erstellung festlegen. Sie sind ungeeignet, wenn das Projekt technisch flexibel bleiben soll oder wenn die Wahl der Technologie keine kritische Rolle spielt. Im Gegensatz zu nicht-funktionalen Anforderungen (z. B. Performance) sind technische Anforderungen oft binär (erfüllt/nicht erfüllt) und weniger subjektiv bewertbar.
- **Beispiel / Code:** ```java
// Beispiel für eine technische Anforderung in einem Projekt-Dokument
TechnischeAnforderungen:
- Programmiersprache: Java (Version 17 oder höher)
- Framework: Spring Boot (Version 3.x)
- Datenbank: PostgreSQL (Version 15)
- Build-Tool: Maven
- Deployment: Docker-Container auf Kubernetes-Cluster
- Sicherheitsstandard: TLS 1.3 für alle externen Kommunikationen
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1a3
- **Vorgänger / Parent:** [[Requirements-Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Programmiersprachen]]
  - [[Plattformen]]
  - [[Frameworks]]
  - [[Hardware]]
- **Querverweise:** keine
