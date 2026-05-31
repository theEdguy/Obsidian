---
id: 35eedcdd-9b60-4913-97d0-e95c4cb5368d
title: "Lineare_Suche"
date: 2026-05-31
tags:
  - software_engineering
  - algorithmen
  - datenstrukturen
  - suchverfahren
  - komplexitaetstheorie
  - draft
source: "Klausur_Referenz"
---

# [[Lineare_Suche]]

- **Kernkonzept:** Die **lineare Suche** (auch sequentielle Suche genannt) ist ein einfacher [[Suchalgorithmus]], der ein [[Array]] oder eine [[Liste]] sequenziell durchläuft, um ein gesuchtes Element zu finden. Dabei wird jedes Element der Reihe nach mit dem Suchschlüssel verglichen, bis eine Übereinstimmung gefunden oder das Ende der Datenstruktur erreicht ist. Im Gegensatz zur [[Binäre_Suche]] erfordert die lineare Suche keine sortierte Eingabe.
- **Nutzen & Zweck:** Die lineare Suche wird eingesetzt, wenn:
- Die Daten unsortiert vorliegen oder eine Sortierung nicht möglich/wirtschaftlich ist.
- Die Datenmenge klein ist, da der Algorithmus einfach zu implementieren und zu verstehen ist.
- Dynamische Datenstrukturen (z. B. verkettete Listen) durchsucht werden müssen, bei denen ein wahlfreier Zugriff nicht effizient möglich ist.

Vorteile:
- Einfache Implementierung und geringe Komplexität in der Entwicklung.
- Keine Voraussetzungen an die Daten (z. B. Sortierung).
- Effizient für kleine oder häufig veränderte Datensätze, bei denen der Overhead anderer Algorithmen (z. B. Sortieren für [[Binäre_Suche]]) nicht gerechtfertigt ist.
- **Abgrenzung & Grenzen:** Grenzen und Nachteile:
- **Zeitkomplexität**: Die lineare Suche hat eine durchschnittliche und worst-case-Komplexität von **O(n)**, was sie für große Datensätze ineffizient macht. Algorithmen wie die [[Binäre_Suche]] (O(log n)) oder [[Hashing]] (O(1)) sind hier überlegen.
- **Stolpersteine**:
  - Bei unsortierten Daten ist die lineare Suche oft die einzige Option, aber für wiederholte Suchvorgänge lohnt sich eine vorherige Sortierung oder der Einsatz einer [[Hash-Tabelle]].
  - In verteilten Systemen oder Datenbanken ist die lineare Suche aufgrund der hohen Latenz meist ungeeignet.
  - Die Implementierung muss sicherstellen, dass das Ende der Datenstruktur korrekt erkannt wird (z. B. bei verketteten Listen).
- **Abgrenzung zu anderen Suchverfahren**: Im Gegensatz zur [[Binäre_Suche]] oder [[Interpolationssuche]] skaliert die lineare Suche nicht gut mit wachsender Datenmenge.
- **Beispiel / Code:** {'beschreibung': 'Beispiel einer linearen Suche in Java für ein Array von Ganzzahlen:', 'code': 'public class LineareSuche {\n    /**\n     * Führt eine lineare Suche auf einem Array durch.\n     * @param array Das zu durchsuchende Array.\n     * @param schluessel Der gesuchte Wert.\n     * @return Der Index des gesuchten Elements oder -1, falls nicht gefunden.\n     */\n    public static int suche(int[] array, int schluessel) {\n        for (int i = 0; i < array.length; i++) {\n            if (array[i] == schluessel) {\n                return i; // Element gefunden\n            }\n        }\n        return -1; // Element nicht gefunden\n    }\n\n    public static void main(String[] args) {\n        int[] daten = {4, 2, 7, 1, 9, 3};\n        int gesucht = 7;\n        int ergebnis = suche(daten, gesucht);\n        \n        if (ergebnis != -1) {\n            System.out.println("Element gefunden an Index: " + ergebnis);\n        } else {\n            System.out.println("Element nicht gefunden.");\n        }\n    }\n}', 'uml_beschreibung': 'Ein Sequenzdiagramm für die lineare Suche könnte wie folgt aussehen (textuelle Darstellung in Mermaid-Syntax):\n\n```mermaid\nsequenceDiagram\n    participant Aufrufer\n    participant LineareSuche\n    participant Array\n    \n    Aufrufer->>LineareSuche: suche(array, schluessel)\n    activate LineareSuche\n    \n    loop Für jedes Element im Array\n        LineareSuche->>Array: Vergleich array[i] == schluessel\n        alt Gefunden\n            Array-->>LineareSuche: true\n            LineareSuche-->>Aufrufer: Index i\n            deactivate LineareSuche\n        else Nicht gefunden\n            Array-->>LineareSuche: false\n        end\n    end\n    \n    LineareSuche-->>Aufrufer: -1 (nicht gefunden)\n    deactivate LineareSuche\n```'}
