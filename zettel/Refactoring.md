---
id: 555a21d3-ef5e-408f-aa58-5a635a5d3a62
title: "Refactoring"
date: 2026-05-30
tags:
  - software_engineering
  - code_qualitaet
  - wartbarkeit
  - draft
source: "SWE Slides (Folien 361-375)"
---

# [[Refactoring]]

- **Kernkonzept:** [[Refactoring]] bezeichnet die systematische Verbesserung der [[Code]]-Struktur, ohne dessen äußeres [[Verhalten]] zu ändern. Ziel ist die Steigerung der [[Lesbarkeit]], [[Wartbarkeit]] und [[Erweiterbarkeit]].
- **Nutzen & Zweck:** Löst Probleme wie [[Code-Duplikation]], [[Hohe_Kopplung]], schlechte [[Kohäsion]] oder unklare [[Abstraktion|Abstraktionen]]. Ermöglicht die Anpassung von [[Code]] an neue Anforderungen, ohne die [[Funktionalität]] zu beeinträchtigen.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn der [[Code]] bereits stabil und wartbar ist oder wenn keine Tests vorhanden sind, die das [[Verhalten]] validieren. Unterscheidet sich von [[Bugfixing]], da es die [[Funktionalität]] nicht ändert, sondern nur die [[Struktur]].
- **Beispiel / Code:** ```java
// Vor Refactoring: Duplizierter Code
void encryptFileDES(String input, String output) {
    // DES-spezifische Logik + Dateiverarbeitung
}

void encryptFileAES(String input, String output) {
    // AES-spezifische Logik + Dateiverarbeitung
}

// Nach Refactoring: Gemeinsame Abstraktion
interface Cipher {
    void encrypt(String input, String output);
}

class DES implements Cipher { /* DES-Logik */ }
class AES implements Cipher { /* AES-Logik */ }
```
