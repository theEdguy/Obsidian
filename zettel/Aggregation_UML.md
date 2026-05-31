---
aliases:
- Aggregation_(UML)
date: 2026-05-30
id: 5ab09695-72e6-43ee-9555-d90c8cb69c74
source: Klausur_Referenz
tags:
- software_engineering
- uml
- entwurfsmuster
- objektorientierung
- klassendiagramm
- softwaremodellierung
- draft
title: Aggregation_UML
---

# [[Aggregation_UML]]

- **Kernkonzept:** Die [[Aggregation]] in [[UML]] ist eine spezielle Form der [[Assoziation]], die eine "Ganzes-Teil"-Beziehung zwischen [[Klassen]] modelliert. Sie drückt aus, dass ein Objekt (das Aggregat) aus anderen Objekten (den Teilen) zusammengesetzt ist, wobei die Teile unabhängig vom Aggregat existieren können. Die Aggregation wird durch eine leere Raute am Ende der Assoziationslinie beim Aggregat dargestellt. Im Gegensatz zur [[Komposition_UML]] impliziert die Aggregation keine Lebenszyklusabhängigkeit: Die Zerstörung des Aggregats führt nicht zwangsläufig zur Zerstörung der Teile.
- **Nutzen & Zweck:** Die Aggregation dient der Modellierung von hierarchischen Strukturen, bei denen Teile logisch oder physisch zu einem Ganzen gehören, aber eigenständig existieren können. Typische Anwendungsfälle sind:
- Abbildung von Container-Beziehungen (z. B. ein `Team` besteht aus `Mitgliedern`, die auch ohne das Team existieren können).
- Delegation von Verantwortung: Das Aggregat nimmt Anfragen entgegen und leitet sie an seine Teile weiter (z. B. ein `Team` delegiert Aufgaben an seine `Mitglieder`).
- Förderung der [[Wiederverwendbarkeit]] und [[Modularität]], da Teile in verschiedenen Aggregaten verwendet werden können.
- Unterstützung des [[Single_Responsibility_Principle]], indem Verantwortlichkeiten auf Teile verteilt werden.
- **Abgrenzung & Grenzen:** 1. **Abgrenzung zur Komposition**: Die [[Komposition_UML]] ist eine stärkere Form der Aggregation, bei der die Teile nicht unabhängig vom Ganzen existieren können (Lebenszyklusabhängigkeit). Bei der Aggregation ist dies nicht der Fall.
2. **Semantische Unschärfe**: UML definiert die Aggregation als rein konzeptionelles Konstrukt ohne strikte semantische Regeln. Die tatsächliche Implementierung (z. B. in Code) hängt vom Kontext ab und kann variieren.
3. **Verwechslungsgefahr mit Assoziation**: Eine einfache [[Assoziation]] kann ähnliche Beziehungen ausdrücken, ohne die "Ganzes-Teil"-Semantik explizit zu betonen. Die Aggregation sollte nur verwendet werden, wenn diese Semantik relevant ist.
4. **Keine Standard-Implementierung**: In vielen Programmiersprachen (z. B. Java) gibt es kein direktes Sprachkonstrukt für Aggregation. Sie wird typischerweise durch Referenzen oder Collections implementiert, wobei die Lebenszyklusverwaltung manuell erfolgen muss.
5. **Vererbung von Aggregationen**: Wie im Kontext gezeigt, werden Aggregationen bei der [[Vererbung]] weitergegeben (z. B. `LigaTeam` erbt die Aggregation von `Team`). Dies kann zu unerwarteten Effekten führen, wenn die Semantik der abgeleiteten Klasse nicht zur Aggregation passt.
- **Beispiel / Code:** {'uml_diagramm': '```mermaid\nclassDiagram\n    class Team {\n        -mitglieder: Mitglied[]\n        +aufgabeDelegieren()\n    }\n    class Mitglied {\n        +aufgabeAusfuehren()\n    }\n    Team "1" o-- "0..*" Mitglied : Aggregation\n```', 'java_implementation': 'public class Mitglied {\n    public void aufgabeAusfuehren() {\n        System.out.println("Aufgabe wird ausgeführt.");\n    }\n}\n\npublic class Team {\n    private List<Mitglied> mitglieder;\n\n    public Team(List<Mitglied> mitglieder) {\n        this.mitglieder = new ArrayList<>(mitglieder); // Teile existieren unabhängig\n    }\n\n    public void aufgabeDelegieren() {\n        for (Mitglied mitglied : mitglieder) {\n            mitglied.aufgabeAusfuehren(); // Delegation an Teile\n        }\n    }\n}\n\n// Verwendung:\nList<Mitglied> mitglieder = new ArrayList<>();\nmitglieder.add(new Mitglied());\nTeam team = new Team(mitglieder); // Aggregation\nteam.aufgabeDelegieren();\n// Die Mitglieder existieren weiter, auch wenn das Team gelöscht wird.\n'}
