---
id: 5710791c-a049-447f-96c0-a74c378787eb
title: "Modellierungsperspektive"
date: 2026-05-30
tags:
  - software_engineering
  - uml
  - softwarearchitektur
  - systemmodellierung
  - entwurfsmuster
  - abstraktion
  - 4+1_sicht_architektur
  - draft
source: "Klausur_Referenz"
---

# [[Modellierungsperspektive]]

- **Kernkonzept:** Die [[Modellierungsperspektive]] bezeichnet die spezifische Sichtweise oder den Fokus, aus dem ein [[Modell]] in der Softwareentwicklung betrachtet und konstruiert wird. Sie definiert, welche Aspekte des Systems (z. B. Struktur, Verhalten, Interaktionen) hervorgehoben und welche Details abstrahiert werden. Unterschiedliche Perspektiven ermöglichen es, komplexe Systeme aus verschiedenen Blickwinkeln zu analysieren, z. B. durch [[Klassendiagramm|Klassendiagramme]] (strukturell), [[Sequenzdiagramm|Sequenzdiagramme]] (verhaltensorientiert) oder [[Komponentendiagramm|Komponentendiagramme]] (architektonisch). Die Wahl der Perspektive hängt vom Ziel der Modellierung ab, etwa der Kommunikation mit Stakeholdern, der Dokumentation oder der Vorbereitung der Implementierung.
- **Nutzen & Zweck:** Die [[Modellierungsperspektive]] dient mehreren zentralen Zwecken im Software-Engineering:

1. **Komplexitätsreduktion**: Durch Fokussierung auf bestimmte Aspekte (z. B. Datenfluss vs. Kontrollfluss) wird die Komplexität des Systems handhabbar.
2. **Zielgruppengerechte Kommunikation**: Unterschiedliche Perspektiven ermöglichen es, Modelle für verschiedene Stakeholder (Entwickler, Architekten, Kunden) verständlich aufzubereiten. Beispiel: Ein [[Use-Case-Diagramm]] für Anforderungen vs. ein [[Zustandsdiagramm]] für die Implementierung.
3. **Konsistenzsicherung**: Durch klare Perspektiven lassen sich Widersprüche zwischen Modellen identifizieren (z. B. zwischen statischer Struktur und dynamischem Verhalten).
4. **Wiederverwendbarkeit**: Perspektiven wie die [[Schichtenarchitektur]] fördern modulare Designs, die leichter anpassbar sind.
5. **Brücke zwischen Analyse und Entwurf**: Perspektiven wie die [[4+1_Sicht_Architektur]] verbinden Anforderungen (z. B. logische Sicht) mit technischen Lösungen (z. B. physische Sicht).
- **Abgrenzung & Grenzen:** Die [[Modellierungsperspektive]] ist abzugrenzen von:

1. **Modellierungssprachen**: Während UML oder SysML die Syntax für Modelle definieren, legt die Perspektive den semantischen Fokus fest (z. B. *was* modelliert wird, nicht *wie*).
2. **Modellierungsebenen**: Perspektiven sind orthogonal zu Abstraktionsebenen (z. B. Analyse vs. Entwurf). Eine strukturelle Perspektive kann sowohl auf Analyse- als auch auf Entwurfsebene eingenommen werden.
3. **Stilistische Entscheidungen**: Die Wahl einer Perspektive ist kein ästhetisches, sondern ein funktionales Kriterium. Beispiel: Ein [[Komponentendiagramm]] ist keine „Alternative“ zu einem [[Klassendiagramm]], sondern dient einem anderen Zweck.

**Typische Stolpersteine**:
- **Überladung von Modellen**: Die Vermischung mehrerer Perspektiven in einem Diagramm (z. B. Struktur *und* Verhalten in einem [[Klassendiagramm]]) führt zu Unübersichtlichkeit.
- **Fehlende Konsistenz**: Widersprüche zwischen Perspektiven (z. B. ein [[Sequenzdiagramm]], das eine nicht existierende Methode aufruft) bleiben oft unentdeckt.
- **Falsche Granularität**: Zu detaillierte Perspektiven in frühen Phasen (z. B. Implementierungsdetails in der Analyse) behindern die Flexibilität.
- **Vernachlässigung nicht-funktionaler Aspekte**: Perspektiven wie Sicherheit oder Performance werden oft erst spät berücksichtigt (vgl. [[Quality_Attributes]]).
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel veranschaulicht zwei unterschiedliche Modellierungsperspektiven für dasselbe System (ein Bestellsystem) anhand von UML-Diagrammen:\n\n1. **Strukturelle Perspektive (Klassendiagramm)**:\n   Fokus auf die statische Struktur der Klassen und ihre Beziehungen.\n   ```mermaid\n   classDiagram\n     class Kunde {\n       -kundenId: String\n       -name: String\n       +bestellen(artikel: Artikel): Bestellung\n     }\n     class Artikel {\n       -artikelId: String\n       -preis: double\n     }\n     class Bestellung {\n       -bestellId: String\n       -datum: Date\n       +berechneGesamtpreis(): double\n     }\n     Kunde "1" -- "0..*" Bestellung : platziert\n     Bestellung "1" -- "1..*" Artikel : enthält\n   ```\n\n2. **Verhaltensperspektive (Sequenzdiagramm)**:\n   Fokus auf die dynamische Interaktion zwischen Objekten bei der Bestellabwicklung.\n   ```mermaid\n   sequenceDiagram\n     participant Kunde\n     participant Bestellung\n     participant Artikel\n     Kunde->>Bestellung: bestellen(artikel)\n     Bestellung->>Artikel: prüfeVerfügbarkeit()\n     Artikel-->>Bestellung: verfügbar\n     Bestellung->>Bestellung: berechneGesamtpreis()\n     Bestellung-->>Kunde: Bestellbestätigung\n   ```\n\n**Hinweis**: Beide Perspektiven ergänzen sich, zeigen aber unterschiedliche Aspekte des Systems. Die strukturelle Perspektive ist Grundlage für die Implementierung, während die verhaltensorientierte Perspektive die Logik der Interaktionen klärt.', 'java_skizze': '// Beispiel für eine strukturelle Perspektive in Java (Klassenentwurf)\npublic class Kunde {\n    private String kundenId;\n    private String name;\n    \n    public Bestellung bestellen(Artikel artikel) {\n        Bestellung bestellung = new Bestellung(this);\n        bestellung.hinzufuegen(artikel);\n        return bestellung;\n    }\n}\n\npublic class Bestellung {\n    private String bestellId;\n    private Date datum;\n    private List<Artikel> artikelListe = new ArrayList<>();\n    \n    public double berechneGesamtpreis() {\n        return artikelListe.stream().mapToDouble(Artikel::getPreis).sum();\n    }\n    \n    public void hinzufuegen(Artikel artikel) {\n        artikelListe.add(artikel);\n    }\n}\n\n// Die verhaltensperspektive würde sich auf die Methodenaufrufe konzentrieren,\n// z. B. durch Logging oder ein Sequenzdiagramm (hier nicht als Code umsetzbar).'}
