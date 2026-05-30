---
id: daf56c70-acd6-47c2-9630-d3e33ff99b98
title: "Abwärtskompatibilität"
date: 2026-05-30
tags:
  - software_engineering
  - versionierung
  - integration
  - draft
source: "SWE Slides (Folien 361-375)"
---

# [[Abwärtskompatibilität]]

- **Kernkonzept:** [[Abwärtskompatibilität]] bezeichnet die Fähigkeit eines [[Systems]] oder einer [[Komponente]], mit älteren [[Version|Versionen]] von [[Schnittstelle|Schnittstellen]], [[Datenformat|Datenformaten]] oder [[Protokoll|Protokollen]] zu arbeiten, ohne deren [[Funktionalität]] zu beeinträchtigen.
- **Nutzen & Zweck:** Ermöglicht die schrittweise Migration von [[System|Systemen]] oder [[Komponente|Komponenten]], ohne bestehende [[Client|Clients]] zu brechen. Reduziert den Aufwand für [[Wartung]] und [[Integration]].
- **Abgrenzung & Grenzen:** Kann zu [[Komplexität]] führen, wenn zu viele [[Version|Versionen]] unterstützt werden müssen. Nicht immer möglich, wenn grundlegende [[Schnittstelle|Schnittstellen]]-Änderungen erforderlich sind.
- **Beispiel / Code:** ```java
// Beispiel für Abwärtskompatibilität
interface Cipher {
    // Alte Methode
    void encrypt_file(String input, String output);
    
    // Neue Methode mit zusätzlicher Funktionalität
    default void encrypt_dir(String inputDir, String outputDir) {
        // Standardimplementierung für ältere Clients
    }
}
```
