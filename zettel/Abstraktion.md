---
id: ea348f5d-c45c-42fd-8017-fd8003da134d
title: "Abstraktion"
date: 2026-06-24
tags:
  - software_engineering
  - grundlagen
  - oop
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Abstraktion]]

- **Kernkonzept:** Abstraktion ist ein zentrales [[Prinzip]] der [[objektorientierten_Modellierung|objektorientierten Modellierung]] und des [[Software_Engineering|Software Engineerings]], bei dem komplexe reale Sachverhalte vereinfacht werden, indem nur die für das Problem relevanten [[Eigenschaft|Eigenschaften]] und [[Zusammenhang|Zusammenhänge]] betrachtet werden. Sie reduziert [[Komplexität]] durch Verbergen von [[Implementierungsdetail|Implementierungsdetails]] und Fokus auf [[Schnittstelle|Schnittstellen]] oder [[Verhalten]].
- **Nutzen & Zweck:** Abstraktion existiert, um die [[Komplexität]] realer [[System|Systeme]] beherrschbar zu machen. Sie löst das Problem, dass reale [[Objekt|Objekte]] und Prozesse oft zu viele [[Detail|Details]] aufweisen, die für die Lösung eines spezifischen Problems nicht benötigt werden. Durch gezieltes Weglassen unwichtiger Aspekte entsteht ein klares, fokussiertes [[Modell]], das die Kommunikation zwischen [[Entwickler|Entwicklern]], Anwendern und [[Experte|Experten]] erleichtert. Zudem ermöglicht sie [[Wiederverwendung]], [[Wartbarkeit]] und [[Erweiterbarkeit]] durch klare [[Trennung_von_Belangen|Trennung von Belangen]] und fördert die [[Lose_Kopplung|lose Kopplung]] von [[Komponente|Komponenten]]. Abstraktion ist Grundlage für [[OOP]], [[APIs]] und [[Entwurfsmuster|Entwurfsmuster]] wie das [[Strategie_Pattern|Strategie-Pattern]] oder [[Observer_Pattern|Observer-Pattern]].
- **Abgrenzung & Grenzen:** Abstraktion sollte nicht genutzt werden, wenn eine vollständige und detaillierte Repräsentation der [[Realität]] erforderlich ist, beispielsweise in [[Simulationssystem|Simulationssystemen]], die präzise physikalische oder biologische Prozesse nachbilden müssen. Sie ist kein Ersatz für [[Konkrete_Implementierung|konkrete Implementierungen]], da [[Abstraktion|Abstraktionen]] später realisiert werden müssen. Abstraktion unterscheidet sich von [[Kopplung]] durch ihren Fokus auf [[Lose_Kopplung|lose Kopplung]] und ist nicht sinnvoll bei trivialen [[System|Systemen]], bei denen der Overhead der Abstraktion den Nutzen übersteigt. Alternativen wie detaillierte [[Datenmodell|Datenmodelle]] oder prozedurale Ansätze können sinnvoll sein, wenn Abstraktion zu stark vereinfacht und wichtige [[Zusammenhang|Zusammenhänge]] verloren gehen. Zudem kann übermäßige Abstraktion zu [[Anti-Pattern|Anti-Patterns]] wie [[Over-Engineering]] führen.
- **Beispiel / Code:** ```java
// Abstraktion am Beispiel einer Klasse 'Mitglied', die nur relevante Attribute und Methoden enthält
class Mitglied {
    private String name;
    private String adresse;
    private int alter;
    private int leistung;

    public int leistungsprognose() {
        // Berechnung basierend auf relevanten Attributen
        return this.leistung * 2; // Vereinfachte Logik
    }
}

// Beispiel für Abstraktion durch ein Interface (Schnittstelle)
public interface Logger {
    void log(String message);
}

public class FileLogger implements Logger {
    @Override
    public void log(String message) {
        // Logik zum Schreiben in eine Datei
        System.out.println("Logging to file: " + message);
    }
}

public class ConsoleLogger implements Logger {
    @Override
    public void log(String message) {
        // Logik zum Schreiben auf die Konsole
        System.out.println("Console: " + message);
    }
}
```
