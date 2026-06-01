---
id: 6f147f6b-17dc-4704-9747-b63d976bf5af
title: "Benutzerschnittstellen-Ebene (Presentation Layer)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - software-design
  - benutzerschnittstelle
  - schichtenmodell
  - separation-of-concerns
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Benutzerschnittstellen-Ebene (Presentation Layer)]]

- **Kernkonzept:** Die Benutzerschnittstellen-Ebene (Presentation Layer) ist die oberste [[Schicht|Schicht]] in einer [[geschichteten Architektur|geschichteten Architektur]] und dient der Interaktion zwischen [[Benutzer|Benutzern]] und dem [[System]]. Sie kapselt alle Komponenten, die für die Darstellung von [[Daten]] und die Entgegennahme von [[Benutzereingabe|Benutzereingaben]] verantwortlich sind.
- **Nutzen & Zweck:** Dieses Konzept trennt die [[Logik]] der [[Benutzerinteraktion]] von der [[Verarbeitungslogik]] und [[Datenhaltung]], um die [[Wartbarkeit]], [[Skalierbarkeit]] und [[Wiederverwendbarkeit]] von [[Softwarekomponente|Softwarekomponenten]] zu erhöhen. Es löst das Problem der engen Kopplung zwischen [[Frontend]] und [[Backend]] und ermöglicht eine klare [[Aufgabentrennung]] in [[verteilten Systemen]].
- **Abgrenzung & Grenzen:** Die Benutzerschnittstellen-Ebene sollte nicht genutzt werden, wenn keine direkte [[Benutzerinteraktion]] erforderlich ist (z. B. bei reinen [[Backend-Dienst|Backend-Diensten]] oder [[Mikroservice|Mikroservices]] ohne grafische Oberfläche). Alternativen wie [[REST-APIs]] oder [[CLI-Tool|CLI-Tools]] können in solchen Fällen effizienter sein. Zudem ist sie nicht geeignet für Systeme mit extrem niedriger Latenz, da die zusätzliche [[Schicht]] Overhead verursachen kann.
- **Beispiel / Code:** Ein einfaches Beispiel für eine dreischichtige Architektur mit Presentation Layer:

```
// Presentation Layer (Benutzerschnittstelle)
function displaySearchResults(results) {
    const resultsContainer = document.getElementById('results');
    resultsContainer.innerHTML = results.map(result => `<div>${result.title}</div>`).join('');
}

// Verarbeitungsebene (Logik)
function search(query) {
    const processedQuery = query.trim();
    const results = databaseQuery(processedQuery); // Aufruf der Datenebene
    displaySearchResults(results); // Rückgabe an Presentation Layer
}
```

In diesem Beispiel ist die `displaySearchResults`-Funktion Teil der Benutzerschnittstellen-Ebene und kümmert sich ausschließlich um die Darstellung der [[Daten]].
