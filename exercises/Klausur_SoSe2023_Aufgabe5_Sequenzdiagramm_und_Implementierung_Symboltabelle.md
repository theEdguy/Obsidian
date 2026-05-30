---
id: 32c1d236-2949-479d-b5e6-b4d47b4fef46
title: "Klausur_SoSe2023_Aufgabe5_Sequenzdiagramm_und_Implementierung_Symboltabelle"
date: 2026-05-30
tags:
  - software_engineering
  - sose2023
  - klausur_sose_2023
  - sequenzdiagramm
  - symboltabelle
  - java_implementierung
  - datenstrukturen
  - uml
  - fehlerbehandlung
  - exercise
  - draft
source: "SWE 2023 mit Loesung.pdf"
---

# [[Klausur_SoSe2023_Aufgabe5_Sequenzdiagramm_und_Implementierung_Symboltabelle]]

- **Aufgabenstellung:** 
  - **a:**
  Spezifizieren Sie mittels eines [[Sequenzdiagramm|Sequenzdiagramms]] die Operation `update`, die einen in der Symboltabelle hinterlegten Wert durch einen neuen Wert überschreibt und den alten Wert zurückliefert. Dabei müssen folgende Bedingungen erfüllt sein:
  - Es dürfen keine neuen Einträge entstehen.
  - Bestehende Einträge dürfen nicht gelöscht oder auf `null` gesetzt werden.
  - Der neue Wert darf nicht `null` sein.
  - Es dürfen nur Einträge geändert werden, die nicht `null` sind.
  - Bei Regelverstößen darf die Symboltabelle nicht verändert werden und es muss `null` zurückgeliefert werden.
  
  Hinweis: Alle bereits implementierten Operationen können genutzt werden.
  - **b:** Implementieren Sie die Operation `update` gemäß Ihrer Spezifikation aus Teilaufgabe a) in Java-Pseudocode. Nutzen Sie die gegebene Klassenstruktur (`SymTab` und `Store`).
- **Lösungsweg / Musterlösung:** 
  - **a:**
  Das [[Sequenzdiagramm]] für die `update`-Operation sollte folgende Schritte abbilden:
  
  1. **Aufruf von `update(key, newVal)`** durch den Akteur (z. B. `Client`).
  2. **Prüfung von `newVal`**: Falls `newVal == null`, wird sofort `null` zurückgegeben.
  3. **Aufruf von `getValue(key)`** auf der `SymTab`-Instanz, um den alten Wert (`oldValue`) zu ermitteln.
  4. **Prüfung von `oldValue`**: Falls `oldValue == null`, wird `null` zurückgegeben.
  5. **Aufruf von `delete(key)`** auf dem `Store`-Objekt, um den alten Wert zu entfernen.
  6. **Aufruf von `set(key, newVal)`** auf dem `Store`-Objekt, um den neuen Wert zu setzen.
  7. **Rückgabe von `oldValue`** an den Akteur.
  
  Falls eine der Bedingungen verletzt wird (z. B. `newVal == null` oder `oldValue == null`), wird der Ablauf abgebrochen und `null` zurückgegeben, ohne die Symboltabelle zu verändern.
  
  **Hinweis**: Das Sequenzdiagramm sollte die Interaktionen zwischen `Client`, `SymTab` und `Store` klar darstellen, inklusive der Bedingungsprüfungen und Rückgabewerte.
  - **b:**
  Die Implementierung der `update`-Methode in Java-Pseudocode:
  
  ```java
  public Value update(Integer key, Value newVal) {
      if (newVal == null) {
          return null;
      }
      Value oldValue = this.getValue(key);
      if (oldValue == null) {
          return null;
      }
      this.store.delete(key);
      this.store.set(key, newVal);
      return oldValue;
  }
  ```
  
  **Erläuterung**:
  - Die Methode prüft zunächst, ob `newVal` `null` ist. Falls ja, wird `null` zurückgegeben.
  - Anschließend wird der alte Wert (`oldValue`) über `getValue(key)` abgerufen.
  - Falls `oldValue` `null` ist, wird `null` zurückgegeben.
  - Andernfalls wird der alte Wert gelöscht (`delete(key)`) und der neue Wert gesetzt (`set(key, newVal)`).
  - Schließlich wird der alte Wert zurückgegeben.
  
  **Hinweis**: Die gegebene Lösung in der Aufgabenstellung ist fehlerhaft, da sie `oldValue` auch dann zurückgibt, wenn `newVal == null` ist. Die korrigierte Version oben stellt sicher, dass die Symboltabelle nur bei gültigen Eingaben verändert wird.
- **Theoretischer Bezug:** 
  - [[Sequenzdiagramm|Sequenzdiagramme]] zur Modellierung von Interaktionen zwischen Objekten.
  - [[Kontrollfluss|Kontrollflüsse]] und Bedingungsprüfungen in [[UML_Diagramme|UML-Diagrammen]].
  - [[Kapselung|Kapselung]] und [[Datenintegrität]] in der objektorientierten Programmierung.
  - [[Fehlerbehandlung|Fehlerbehandlung]] durch Rückgabewerte (`null`) statt Exceptions.
  - [[Symboltabelle]] als Beispiel für eine [[Datenstruktur]] mit beschränkter Kapazität.
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung von `null`-Prüfungen: Es muss sowohl `newVal` als auch `oldValue` auf `null` geprüft werden, um die Anforderungen zu erfüllen.
  - Falsche Annahme, dass `delete(key)` oder `set(key, newVal)` immer erfolgreich sind. Die Methoden könnten `false` zurückgeben, was hier jedoch ignoriert wird, da die Vorbedingungen (`newVal != null` und `oldValue != null`) dies verhindern.
  - Unklare Rückgabewerte: Die Methode muss `null` zurückgeben, wenn die Symboltabelle nicht verändert wird, und den alten Wert nur bei erfolgreicher Aktualisierung.
  - Vergessen der Vorbedingungen aus Teilaufgabe a) in der Implementierung, z. B. dass keine neuen Einträge entstehen dürfen.
  - Fehlerhafte Nutzung der `Store`-Methoden: `set(key, newVal)` gibt `false` zurück, wenn der alte Wert nicht `null` war oder `newVal == null` ist. Dies wird in der Lösung ignoriert, da die Vorbedingungen dies ausschließen.
