---
id: 8f4afd72-4579-4744-a191-7fb0248f4bee
title: "Komponente"
date: 2026-06-01
tags:
  - verteilte_systeme
  - software_engineering
  - architektur
  - design
  - verteilte-systeme
  - modularisierung
  - schnittstellen
  - konnektoren
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Komponente]]

- **Kernkonzept:** Eine [[Komponente]] ist eine modulare, wiederverwendbare Einheit in der [[Systemarchitektur]], die eine dedizierte [[Funktionalität]] kapselt und über eine definierte [[Schnittstelle|Schnittstellen]] mit anderen [[Komponente|Komponenten]] interagiert. In [[Verteiltes_System|verteilten Systemen]] sind [[Komponente|Komponenten]] eigenständige, modularisierte Einheiten, die über [[Konnektor|Konnektoren]] kommunizieren und gemeinsam ein System bilden.
- **Nutzen & Zweck:** [[Komponente|Komponenten]] fördern die [[Modularität]], [[Wiederverwendbarkeit]] und [[Wartbarkeit]] von Systemen, indem sie komplexe Strukturen in beherrschbare Teile zerlegen. Sie ermöglichen die [[Trennung_von_Verantwortlichkeiten|Trennung von Verantwortlichkeiten]] und lösen Probleme der [[Skalierbarkeit]] und [[Wartbarkeit]] in [[Verteiltes_System|verteilten Architekturen]], insbesondere durch klare [[Schnittstelle|Schnittstellen]] und [[Lose_Kopplung|lose Kopplung]].
- **Abgrenzung & Grenzen:** [[Komponente|Komponenten]] sind kein Ersatz für [[Klasse|Klassen]] oder [[Funktion|Funktionen]] auf Code-Ebene, da sie auf der [[Architektur]]-Ebene operieren und größer dimensioniert sind. Im Gegensatz zu [[Modul|Modulen]] besitzen sie oft explizitere [[Schnittstelle|Schnittstellen]]. Sie sind ungeeignet, wenn enge [[Kopplung]] oder direkte Abhängigkeiten erforderlich sind – hier bieten monolithische Architekturen geringere [[Komplexität]], erfordern jedoch zentrale Kontrolle. Während [[Objekt|Objekte]] feingranular und [[Service|Services]] autonom sind, sind [[Komponente|Komponenten]] oft auf spezifische [[Architekturstil|Architekturstile]] wie [[Geschichtete_Architektur|geschichtete]] oder [[Objektbasierte_Architektur|objektbasierte Systeme]] zugeschnitten.
- **Beispiel / Code:** ```java
// Beispiel einer Komponente in Java (Spring Boot)
@Component
public class BestellService {
    public Bestellung erstelleBestellung(Warenkorb warenkorb) {
        // Logik zur Bestellungserstellung
    }
}
```

Geschichtete Architektur (Kommunikationsprotokoll):
```
// Layer N (Anwendungsschicht)
function sendRequest(data) {
  const processedData = processData(data); // Verarbeitungsebene
  const networkPacket = encodePacket(processedData); // Datenebene
  return networkPacket;
}

// Layer N-1 (Transportschicht)
function encodePacket(data) {
  return { header: 'TCP', payload: data };
}
```
