---
id: 1dbb2688-05bc-4d0e-b0c3-8f9c4426ca6f
title: "Use_Case"
date: 2026-05-30
tags:
  - software_engineering
  - analyse
  - anforderung
  - anforderungserhebung
  - requirements_engineering
  - uml
  - draft
source: "SWE Slides (Folien 151-165)"
---

# [[Use_Case]]

- **Kernkonzept:** Ein [[Use_Case|Use Case]] beschreibt eine [[Interaktion]] zwischen einem oder mehreren [[Akteur|Akteuren]] und einem [[System]] oder [[Softwaresystem]], um ein bestimmtes [[Ziel]] aus Sicht des [[Endbenutzer|Endbenutzers]] oder [[Nutzer|Nutzers]] zu erreichen. Er strukturiert [[Geschäftsvorfall|Geschäftsvorfälle]] aus [[Nutzer|Nutzersicht]], umfasst [[Ablauf|Abläufe]], [[Vorbedingung|Vorbedingungen]] und [[Nachbedingung|Nachbedingungen]] und dient als Brücke zwischen [[Stakeholder|Stakeholdern]] und [[Entwickler|Entwicklern]] in der [[Anforderungsanalyse]] und [[Anforderungserhebung]].
- **Nutzen & Zweck:** Ein [[Use_Case|Use Case]] löst das Problem unklarer oder unvollständiger [[Anforderung|Anforderungen]], indem er die [[Funktionalität]] aus der Perspektive des [[Akteur|Akteurs]] formalisiert und in [[szenariobasierte_Beschreibung|szenariobasierte Beschreibungen]] überführt. Dadurch wird das [[Problemverständnis]] für [[Stakeholder|Stakeholder]] und [[Entwicklungsteam|Entwicklungsteams]] verbessert, die [[Kommunikation]] zwischen [[Projektbeteiligte|Beteiligten]] gefördert und [[Missverständnisse]] vermieden. Er macht [[Anforderung|Anforderungen]] greifbar und verständlich, unterstützt die Identifikation von [[Schnittstelle|Schnittstellen]] und [[Abhängigkeit|Abhängigkeiten]] und bildet die Grundlage für [[Testfall|Testfälle]], [[Analysemodell|Analysemodelle]], [[Design]] und [[Systemdesign]]. Zudem dient er als Referenz für die [[Geschäftsprozessmodellierung]] und verbindet [[Anforderungsanalyse]] mit [[Systemdesign]].
- **Abgrenzung & Grenzen:** Ein [[Use_Case|Use Case]] ist kein Ersatz für detaillierte [[Anforderung|Anforderungen]], [[Technische_Spezifikation|technische Spezifikationen]] oder [[Datenmodell|Datenmodelle]]. Er eignet sich nicht für [[Projekt|Projekte]] mit rein technischen oder internen [[Anforderung|Anforderungen]], die keine [[Akteur|Akteure]] involvieren, oder für nicht-funktionale [[Anforderung|Anforderungen]] wie [[Performance]] oder [[Sicherheit]]. Bei zu vielen [[Use_Case|Use Cases]] kann die Übersichtlichkeit leiden, und er sollte nicht mit [[Einzelschritt|Einzelschritt]]-Beschreibungen (z. B. "[[Button_klicken]]") oder [[technisches_Detail|technischen Details]] (z. B. "[[Datenbankabfrage]]") verwechselt werden. Im Vergleich zu [[User_Story|User Stories]] zeichnet er sich durch eine formale Struktur und höhere [[Detaillierung]] aus, was ihn weniger agil, aber präziser macht. In technischen [[System|Systemen]] wird er oft durch [[User_Story|User Stories]] ergänzt.
- **Beispiel / Code:** ```plaintext
// Beispiel 1: Benutzeranmeldung
Use Case: Benutzer anmelden
Akteur: [[Benutzer]]
Vorbedingung: [[Benutzer]] ist registriert
Hauptszenario:
1. [[Benutzer]] gibt Benutzername und Passwort ein.
2. [[System]] validiert die Eingaben.
3. [[System]] gewährt Zugriff.
Nachbedingung: [[Benutzer]] ist authentifiziert
Alternativszenario:
2a. Eingaben sind ungültig → [[System]] zeigt Fehlermeldung an.

// Beispiel 2: Geld abheben
Use Case: Geld abheben
Akteur: [[Bankkunde]]
Vorbedingung: [[Bankkunde]] ist authentifiziert
Hauptszenario:
1. [[Bankkunde]] wählt „Geld abheben“ aus.
2. [[System]] fragt nach Betrag.
3. [[Bankkunde]] gibt Betrag ein.
4. [[System]] prüft Kontostand.
5. [[System]] gibt Geld aus.
6. [[System]] aktualisiert Kontostand.
Nachbedingung: Kontostand ist aktualisiert
Alternativszenario:
4a. Kontostand ist unzureichend.
    4a1. [[System]] zeigt Fehlermeldung an.

// Beispiel 3: Mitglieder verwalten
Name: [[Mitglieder_verwalten]]
Akteure: [[Vereinsmanager]], [[Mail_Client]]
Beschreibung: Der [[Vereinsmanager]] kann [[Mitglied|Mitglieder]] anlegen, bearbeiten oder löschen. Bei [[Abteilungswechsel]] werden [[Abteilungsleiter]] und [[Mitglied]] per Mail informiert.
Vorbedingung: [[Vereinsmanager]] ist authentifiziert
Nachbedingung: [[Mitglied|Mitgliederdaten]] sind aktualisiert, [[Mail_Client]] hat Benachrichtigung versendet
```
