---
id: 56cf4df5-7f4b-494b-a9aa-ef8ac36fff39
title: "Klausur_WiSe2023_2024_Aufgabe1_Use_Case_Modellierung_Mitfahr_App"
date: 2026-05-30
tags:
  - software_engineering
  - wise2023_2024
  - klausur_ws2023_2024
  - use_case_diagramm
  - anforderungsanalyse
  - modellierung
  - vererbung
  - extend_include_beziehungen
  - exercise
  - draft
source: "SWE 2023-2024 mit Loesung.pdf"
---

# [[Klausur_WiSe2023_2024_Aufgabe1_Use_Case_Modellierung_Mitfahr_App]]

- **Aufgabenstellung:** 
  - **a:** (3 Punkte) Zur Modellierung der Abhängigkeiten zwischen Use Cases nutzt man typischerweise Extend- und Include-Beziehungen. Doch wann nutzt man eine Vererbungsbeziehung? Erläutern Sie den Einsatzzweck.
  - **b:**
  (12 Punkte) Skizzieren Sie den folgenden Sachverhalt aus Sicht des App-Entwicklungsteams mithilfe eines Use-Case-Diagramms:
  
  Mit einer neuen Mitfahr-App soll europaweit eine sichere Plattform für Individualreisende geschaffen werden. Jeder Nutzer muss sich zunächst registrieren. Die Registrierung umfasst persönliche Daten (Name, Anschrift, E-Mail etc.) sowie eine Online-Identitätsprüfung über einen Drittanbieter, dessen API bereits verfügbar ist.
  
  Die Vereinbarung einer Mitfahrgelegenheit erfolgt in mehreren Schritten:
  - Nutzer können Mitfahranfragen (Ausgangsort, Zielort, Zeitfenster) erstellen, die mit bestehenden Mitfahrangeboten abgeglichen werden. Bei Übereinstimmung kann die Mitfahrgelegenheit direkt gebucht werden.
  - Analog können Nutzer Mitfahrangebote erstellen, die mit Mitfahrgesuchen abgeglichen werden. Bei Übereinstimmung kann ein Gesuch direkt angenommen werden.
  - Alternativ können Nutzer durch vorhandene Angebote und Gesuche stöbern und spontan entscheiden, eine Mitfahrgelegenheit anzubieten oder wahrzunehmen.
  
  Nach der Annahme eines Angebots oder Gesuchs wird die Gegenseite per E-Mail informiert und erhält die notwendigen Daten. Die Gegenseite muss die Annahme in der App bestätigen. Erst nach gegenseitiger Bestätigung gilt die Mitfahrt als vereinbart.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  Eine Vererbungsbeziehung zwischen Use Cases wird genutzt, wenn ein Use Case eine **spezialisierte Variante** eines anderen Use Cases darstellt und diese Spezialisierung nicht durch [[Extend_Beziehung|Extend]]- oder [[Include_Beziehung|Include]]-Beziehungen abgebildet werden kann. Dies ist insbesondere dann der Fall, wenn:
  - Der spezialisierte Use Case **alle Eigenschaften und Funktionalitäten** des allgemeinen Use Cases erbt und diese **erweitert oder überschreibt**.
  - Die Beziehung eine **is-a**-Semantik aufweist (z. B. 'Premium-Buchung' ist eine Art von 'Buchung').
  - Die Spezialisierung **eigenständig** ist und nicht nur eine optionale Erweiterung oder eine zwingend erforderliche Teilfunktion darstellt.
  
  Beispiel: Ein Use Case 'Bezahlung mit Kreditkarte' könnte von einem allgemeinen Use Case 'Bezahlung' erben, wenn er spezifische Schritte für die Kreditkartenabwicklung hinzufügt.
  - **b:**
  Das Use-Case-Diagramm für die Mitfahr-App sollte folgende Akteure und Use Cases enthalten:
  
  **Akteure:**
  - `Nutzer` (generischer Akteur, der sowohl Mitfahrer als auch Anbieter sein kann)
  - `Drittanbieter` (externer Akteur für die Identitätsprüfung)
  
  **Use Cases:**
  1. `Registrieren` (inkl. `Persönliche Daten eingeben` und `Identitätsprüfung durchführen`)
     - `Identitätsprüfung durchführen` <<include>> `Drittanbieter-API nutzen` (mit Akteur `Drittanbieter`)
  2. `Mitfahranfrage erstellen` (inkl. `Ausgangsort/Zielort/Zeitfenster angeben`)
     - <<include>> `Angebote abgleichen`
     - <<extend>> `Mitfahrgelegenheit buchen` (bei Übereinstimmung)
  3. `Mitfahrangebot erstellen` (inkl. `Strecke und Zeitfenster angeben`)
     - <<include>> `Gesuche abgleichen`
     - <<extend>> `Mitfahrgesuch annehmen` (bei Übereinstimmung)
  4. `Angebote/Gesuche durchstöbern`
     - <<extend>> `Mitfahrgelegenheit buchen` (spontan)
     - <<extend>> `Mitfahrgesuch annehmen` (spontan)
  5. `Annahme bestätigen` (nach Benachrichtigung per E-Mail)
  
  **Beziehungen:**
  - `Nutzer` interagiert mit allen Use Cases außer `Drittanbieter-API nutzen`.
  - `Mitfahrgelegenheit buchen` und `Mitfahrgesuch annehmen` führen zu `Annahme bestätigen`.
  - `Annahme bestätigen` muss von beiden Seiten (Anbieter und Mitfahrer) durchgeführt werden, bevor die Mitfahrt als vereinbart gilt.
  
  **Hinweis:**
  - Die Use Cases `Angebote abgleichen` und `Gesuche abgleichen` sind interne Funktionen und werden nicht als separate Use Cases dargestellt, sondern als Teil von `Mitfahranfrage erstellen` bzw. `Mitfahrangebot erstellen`.
  - Die E-Mail-Benachrichtigung ist ein impliziter Schritt und wird nicht als separater Use Case modelliert.
- **Theoretischer Bezug:** 
  - Die Aufgabe bezieht sich auf [[Use_Case_Diagramm|Use-Case-Diagramme]] und die korrekte Anwendung von [[Vererbung_in_Use_Cases|Vererbungsbeziehungen]] in der [[Anforderungsanalyse]].
  - Die Modellierung der Abhängigkeiten zwischen Use Cases erfordert Kenntnisse über [[Extend_Beziehung|Extend]]- und [[Include_Beziehung|Include]]-Beziehungen sowie deren Abgrenzung zur Vererbung.
  - Die Identitätsprüfung über einen Drittanbieter ist ein Beispiel für die Integration externer [[Schnittstelle|Schnittstellen]] in ein System.
  - Die gegenseitige Bestätigung der Mitfahrt kann als [[Zustandsübergang|Zustandsübergang]] modelliert werden, der jedoch in Use-Case-Diagrammen nicht explizit dargestellt wird.
- **Stolpersteine / Fehlerquellen:** 
  - Verwechslung von [[Extend_Beziehung|Extend]] und [[Include_Beziehung|Include]]: Extend modelliert optionale Erweiterungen, Include zwingend erforderliche Teilfunktionen.
  - Falsche Anwendung von Vererbung: Vererbung sollte nicht für Use Cases genutzt werden, die lediglich optionale oder zwingende Teilfunktionen darstellen (hierfür sind Extend/Include besser geeignet).
  - Übermodellierung: Interne Systemfunktionen (z. B. Abgleich von Angeboten/Gesuchen) oder implizite Schritte (z. B. E-Mail-Benachrichtigung) sollten nicht als separate Use Cases dargestellt werden.
  - Fehlende Akteure: Der `Drittanbieter` als externer Akteur wird oft vergessen, obwohl er für die Identitätsprüfung essenziell ist.
  - Unklare Beziehungen: Die gegenseitige Bestätigung der Mitfahrt muss als sequenzieller Ablauf verstanden werden, der jedoch in Use-Case-Diagrammen nicht als zeitliche Abfolge dargestellt wird.
  - Vermischung von Use Cases und Funktionen: Use Cases sollten nutzerzentriert sein und keine technischen Details (z. B. API-Aufrufe) enthalten, es sei denn, sie sind für das Verständnis der Nutzerinteraktion essenziell.
