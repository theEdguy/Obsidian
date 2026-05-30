---
id: a55faba3-db9e-4e66-a956-8e383aeda803
title: "Wasserfallmodell"
date: 2026-05-30
tags:
  - software_engineering
  - vorgehensmodell
  - klassische_methodik
  - prozessmodell
  - softwareentwicklung
  - klassische_methoden
  - draft
source: "SWE Slides (Folien 31-45)"
---

# [[Wasserfallmodell]]

- **Kernkonzept:** Das [[Wasserfallmodell]] ist ein [[sequenzielles_Prozessmodell|sequenzielles Prozessmodell]] für die [[Software-Entwicklung|Software-Entwicklung]], bei dem [[Phase|Phasen]] wie [[Anforderungsanalyse|Anforderungsanalyse]], [[Systemdesign|Systemdesign]], [[Implementierung]], [[Testen|Test]] und [[Betrieb]] starr nacheinander durchlaufen werden und erst nach vollständiger Abarbeitung einer [[Phase]] in die nächste übergegangen wird. Es zählt zu den [[klassische_Methodik|klassischen Methodiken]] und bietet eine lineare Struktur mit klaren [[Meilenstein|Meilensteinen]] und [[Dokumentation|Dokumentationsvorgaben]].
- **Nutzen & Zweck:** Das [[Wasserfallmodell]] eignet sich besonders für [[Projekt|Projekte]] mit stabilen [[Anforderung|Anforderungen]], klaren [[Zielsetzung|Zielsetzungen]] und geringem Risiko von Änderungen. Es bietet [[Planungssicherheit]] durch seine sequenzielle Struktur und ermöglicht eine einfache [[Projektplanung]] sowie [[Ressourcenallokation]]. Durch die frühzeitige Festlegung von [[Spezifikation|Spezifikationen]] (z. B. im [[Lastenheft]] und [[Pflichtenheft]]) wird die [[Kommunikation]] zwischen [[Stakeholder|Stakeholdern]] und [[Entwicklungsteam|Entwicklungsteams]] strukturiert. Zudem ist es für [[Projekt|Projekte]] mit regulatorischen Vorgaben oder hohen [[Qualitätssicherung|Qualitätsanforderungen]] geeignet, da jede [[Phase]] durch formale [[Dokumentation]] und [[Abnahmekriterium|Abnahmekriterien]] abgesichert wird.
- **Abgrenzung & Grenzen:** Das [[Wasserfallmodell]] ist ungeeignet für [[Projekt|Projekte]] mit unklaren, sich ändernden oder komplexen [[Anforderung|Anforderungen]], da Rückkopplungen nur im Fehlerfall vorgesehen sind und spätere [[Änderungsanforderung|Änderungsanforderungen]] hohe Kosten verursachen. Im Vergleich zu [[agile_Methodik|agilen Methoden]] wie [[Scrum]] oder [[Extreme_Programming]] fehlt die Flexibilität für iterative Anpassungen und kontinuierliche [[Feedbackschleife|Feedbackschleifen]]. Die starre [[Spezifikation|Spezifikation]] kann zu [[Nutzloser_Code|nutzlosem Code]] führen, wenn [[Anforderung|Anforderungen]] nicht vollständig verstanden oder falsch umgesetzt werden. Zudem besteht das Risiko von [[Projektverzögerung|Projektverzögerungen]], wenn [[Phase|Phasen]] länger als geplant dauern oder [[Abhängigkeit|Abhängigkeiten]] zwischen [[Aufgabe|Aufgaben]] nicht berücksichtigt werden. Für dynamische [[Projekt|Projekte]] mit hohem Innovationsgrad oder unsicheren [[Marktanforderung|Marktanforderungen]] sind [[inkrementelles_Modell|inkrementelle Modelle]] oder [[hybrides_Prozessmodell|hybride Ansätze]] besser geeignet.
- **Beispiel / Code:** ```plaintext
Phasen des Wasserfallmodells mit typischen Dokumenten und Aktivitäten:

1. [[Anforderungsanalyse]]
   - Dokument: [[Lastenheft]] (Anforderungen des Kunden)
   - Aktivitäten: [[Stakeholder-Analyse]], [[Anforderungserhebung]], [[Risikoanalyse]]

2. [[Systemdesign]]
   - Dokument: [[Pflichtenheft]] (technische Umsetzung)
   - Aktivitäten: [[Architekturentwurf]], [[Schnittstellendefinition]], [[Datenmodellierung]]

3. [[Implementierung]]
   - Dokument: Quellcode, [[Code-Dokumentation]]
   - Aktivitäten: Programmierung, [[Modultest]], [[Code-Review]]

4. [[Testen]]
   - Dokument: [[Testprotokoll]], [[Fehlerbericht]]
   - Aktivitäten: [[Integrationstest]], [[Systemtest]], [[Abnahmetest]]

5. [[Betrieb]] und [[Wartung]]
   - Dokument: [[Betriebshandbuch]], [[Wartungsprotokoll]]
   - Aktivitäten: Deployment, Fehlerbehebung, [[Release-Management]]
```
