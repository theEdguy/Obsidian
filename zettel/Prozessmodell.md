---
id: efdab769-dafb-4020-9f74-ea68de1102d8
title: "Prozessmodelle"
date: 2026-06-24
tags:
  - software_engineering
  - projektmanagement
  - vorgehensmodell
  - draft
source: "SWE Slides – Kapitel 2: Entwicklungsprozesse gestern und heute"
---

# [[Prozessmodelle]]

- **Kernkonzept:** [[Prozessmodelle]] im [[Software_Engineering]] definieren strukturierte [[Vorgehensweise|Vorgehensweisen]] und [[Rahmenwerk|Rahmenwerke]], um die [[Entwicklung]], [[Wartung]] und [[Evolution]] von [[Software]] systematisch zu planen, zu steuern und zu kontrollieren. Sie legen [[Phase|Phasen]], [[Aktivität|Aktivitäten]], [[Rolle|Rollen]] und [[Artefakt|Artefakte]] fest, um [[Komplexität]] in Projekten beherrschbar zu machen, [[Risiko|Risiken]] zu reduzieren und reproduzierbare Ergebnisse zu ermöglichen. Ein [[Prozessmodell]] gibt dabei die zu erbringenden [[Aufgabe|Aufgaben]] und deren zeitliche [[Ablauf|Abfolge]] vor, um ein [[Projektziel]] effizient zu erreichen.
- **Nutzen & Zweck:** [[Prozessmodelle]] reduzieren [[Komplexität]] und [[Unsicherheit]] in der [[Software-Entwicklung]], indem sie klare [[Ablauf|Abläufe]], [[Verantwortlichkeit|Verantwortlichkeiten]] und [[Qualitätsstandard|Qualitätsstandards]] vorgeben. Sie lösen konkrete Probleme wie unklare [[Anforderung|Anforderungen]], ineffiziente [[Kommunikation]], unvorhersehbare Projektverläufe oder mangelnde [[Wiederholbarkeit]] von Erfolgen, indem sie [[Transparenz]], [[Vorhersagbarkeit]] und kontinuierliche [[Verbesserung]] ermöglichen. Zudem unterstützen sie die [[Skalierung]] von Projekten, die Einhaltung von Zeit-, Budget- und Qualitätsvorgaben sowie die systematische [[Projektplanung]]. Als Grundlage für [[Projektmanagement]] und [[Qualitätssicherung]] schaffen sie Klarheit über [[Meilenstein|Meilensteine]], [[Aufgabe|Aufgaben]] und [[Verantwortlichkeit|Verantwortlichkeiten]], wodurch [[Risiko|Risiken]] minimiert und die Effizienz gesteigert wird.
- **Abgrenzung & Grenzen:** [[Prozessmodelle]] sollten nicht eingesetzt werden, wenn Projekte sehr klein, experimentell oder hochgradig innovativ sind, da starre [[Struktur|Strukturen]] [[Kreativität]] und [[Flexibilität]] einschränken können. Sie unterscheiden sich von [[Ad-hoc_Entwicklung|Ad-hoc-Entwicklungsansätzen]] durch ihre [[Formalisierung]] und von [[Agile_Entwicklung|agilen Methoden]] durch ihren Grad an [[Vorabplanung]]. Während klassische Modelle wie das [[Wasserfallmodell]] oder das [[V-Modell]] sequenzielle [[Phase|Phasen]] vorgeben und weniger [[Anpassungsfähigkeit]] bieten, setzen iterative oder agile Modelle wie [[Scrum]] oder [[Rational_Unified_Process|RUP]] auf inkrementelle Entwicklung und kontinuierliche Anpassung. Die Wahl des passenden [[Prozessmodell|Modells]] hängt von Faktoren wie Projektgröße, [[Team|Teamstruktur]], Technologie und Anforderungen an [[Flexibilität]] ab. [[Prozessmodelle]] sind zudem ungeeignet, wenn [[Team|Teams]] keine [[Disziplin]] oder [[Erfahrung]] in ihrer Anwendung haben, da sie sonst zu bürokratischem [[Overhead]] führen. Sie sind kein Ersatz für [[Anpassungsfähigkeit]], sondern bieten ein [[Rahmenwerk]], das systematische [[Planung]] ermöglicht, ohne explorative [[Prototyp|Prototypen]] oder experimentelle Ansätze zu behindern.
- **Beispiel / Code:** ```java
// Beispiel für ein einfaches iteratives Prozessmodell (vereinfacht als Java-Klasse)
public class IterativerEntwicklungsprozess {
    private List<String> phasen = List.of("Anforderungsanalyse", "Design", "Implementierung", "Test", "Evaluation");
    private int aktuelleIteration = 1;
    
    public void starteIteration() {
        System.out.println("Starte Iteration " + aktuelleIteration + ":");
        for (String phase : phasen) {
            System.out.println("  - Phase: " + phase + " durchführen");
            // Feedback einholen und Anpassungen vornehmen
            if (phase.equals("Evaluation")) {
                System.out.println("  - Feedback auswerten und nächste Iteration planen");
                aktuelleIteration++;
            }
        }
    }
}

// Beispiel für ein iteratives Prozessmodell als Ablauf
```text
Iteration 1: [[Anforderungsanalyse]] & Architektur-Entwurf
Iteration 2: Kernfunktionalität implementieren
Iteration 3: Erweiterte [[Feature|Features]] & [[Test|Tests]]

// Klassisches Wasserfallmodell (sequenziell)
1. [[Anforderungsanalyse]]
2. Systemdesign
3. Implementierung
4. Test
5. Wartung
```
