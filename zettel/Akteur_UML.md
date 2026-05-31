---
aliases:
- Akteur_(UML)
date: 2026-05-30
id: fcb6e664-862e-4fbd-87d8-925d610a438c
source: Klausur_Referenz
tags:
- software_engineering
- uml
- anforderungsanalyse
- use_case
- softwaremodellierung
- systemdesign
- draft
title: Akteur_UML
---

# [[Akteur_UML]]

- **Kernkonzept:** Ein **Akteur (UML)** ist ein externer Entitätstyp in der [[Use_Case_Analyse]], der mit einem [[System_(Software_Engineering)]] interagiert, um bestimmte Ziele zu erreichen. Akteure repräsentieren Rollen (z. B. Benutzer, externe Systeme oder Hardware) und nicht konkrete Individuen. Sie initiieren oder beteiligen sich an [[Use_Cases]], ohne Teil des modellierten Systems zu sein. Akteure werden in [[UML-Diagramme|UML-Diagrammen]] (insbesondere [[Use_Case_Diagramm]]) als Strichmännchen oder Rechtecke mit dem Stereotyp `<<actor>>` dargestellt.
- **Nutzen & Zweck:** Akteure dienen der strukturierten Erfassung von Anforderungen in der [[Anforderungsanalyse]] und helfen, die Systemgrenzen klar zu definieren. Durch die Identifikation von Akteuren lassen sich:
- **Use Cases** systematisch ableiten (z. B. "Kunde bestellt Produkt").
- **Schnittstellen** zu externen Entitäten (z. B. Zahlungsdienstleister) frühzeitig erkennen.
- **Testfälle** für die [[Verifikation_und_Validierung]] ableiten, indem Akteure als Ausgangspunkt für Szenarien dienen.
- **Stakeholder** und deren Interessen im Entwicklungsprozess berücksichtigen.

Akteure sind essenziell für die Kommunikation zwischen Entwicklern, Designern und Domänenexperten, da sie eine abstrakte, aber präzise Sprache für Systeminteraktionen bieten.
- **Abgrenzung & Grenzen:** - **Keine Systemkomponenten**: Akteure sind *extern* – interne Module (z. B. Datenbanken) werden nicht als Akteure modelliert.
- **Rollen vs. Individuen**: Ein Akteur beschreibt eine *Rolle* (z. B. "Administrator"), nicht eine Person (z. B. "Max Mustermann"). Eine Person kann mehrere Rollen einnehmen.
- **Keine Hierarchie in Use Cases**: Akteure können zwar in [[Vererbung_(UML)|Vererbungsbeziehungen]] stehen (z. B. "Gast" → "Registrierter Nutzer"), aber diese werden selten genutzt, da sie die Komplexität erhöhen.
- **Stolperstein "System als Akteur"**: Externe Systeme (z. B. APIs) *können* Akteure sein, aber nur, wenn sie aktiv mit dem modellierten System interagieren (z. B. eine Wetter-API, die Daten liefert). Passive Datenquellen (z. B. eine CSV-Datei) sind *keine* Akteure.
- **Akteur vs. [[Stakeholder]]**: Nicht alle Stakeholder sind Akteure – nur diejenigen, die direkt mit dem System interagieren (z. B. ist ein Investor ein Stakeholder, aber kein Akteur).
- **Beispiel / Code:** {'uml_diagramm': '```mermaid\nuseCaseDiagram\n    actor Kunde\n    actor Zahlungsdienstleister as "<<actor>> Zahlungsdienstleister"\n    actor "Bank (extern)" as Bank\n\n    Kunde --> (Produkt bestellen)\n    Kunde --> (Zahlung stornieren)\n    (Produkt bestellen) --> Zahlungsdienstleister : <<include>>\n    Zahlungsdienstleister --> Bank : Transaktion durchführen\n```', 'erlaeuterung': 'Im Beispiel interagieren drei Akteure mit dem System:\n1. **Kunde**: Initiiert die Use Cases "Produkt bestellen" und "Zahlung stornieren".\n2. **Zahlungsdienstleister**: Wird vom Use Case "Produkt bestellen" eingebunden (<<include>>-Beziehung) und leitet die Zahlung an die Bank weiter.\n3. **Bank**: Externes System, das Transaktionen verarbeitet. Die Bank ist nur dann ein Akteur, wenn sie aktiv mit dem System kommuniziert (z. B. Bestätigungen sendet).\n\nHinweis: Der Use Case "Zahlung stornieren" hat keine explizite Verbindung zur Bank, da die Stornierung im Beispiel über den Zahlungsdienstleister abgewickelt wird.'}
