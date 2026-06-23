---
id: 064bd7a2-7a67-4e29-8787-c859c5612e14
title: "Sprint Retrospective"
date: 2026-06-23
tags:
  - software_engineering
  - sprint_retrospective
  - scrum
  - draft
source: "software_engineering_kapitel_07"
---

# [[Sprint Retrospective]]

- **Kernkonzept:** Die Sprint Retrospective ist ein zentrales Ereignis im Scrum-Framework, bei dem das Entwicklungsteam nach Abschluss eines Sprints gemeinsam reflektiert, um Prozessverbesserungen zu identifizieren und umzusetzen. Ziel ist es, die Zusammenarbeit, Effizienz und Qualität kontinuierlich zu optimieren.
- **Nutzen & Zweck:** Die Sprint Retrospective existiert, um systematisch aus Erfahrungen zu lernen und adaptive Anpassungen im Entwicklungsprozess vorzunehmen. Sie löst das Problem, dass Teams ohne strukturierte Reflexion ineffiziente Arbeitsweisen oder wiederkehrende Hindernisse übersehen, was zu stagnierender Produktivität oder sinkender Teamzufriedenheit führt. Durch die regelmäßige Analyse von Erfolgen und Misserfolgen wird eine Kultur der kontinuierlichen Verbesserung (Kaizen) gefördert.
- **Abgrenzung & Grenzen:** Die Sprint Retrospective sollte nicht genutzt werden, wenn das Team keine ehrliche Feedbackkultur lebt oder keine Bereitschaft zur Veränderung besteht, da sie sonst zur leeren Routine verkommt. Sie unterscheidet sich von klassischen Projekt-Retrospektiven durch ihren iterativen Charakter und Fokus auf den Scrum-Prozess selbst, nicht auf das Produkt oder langfristige Projektziele. Alternativen wie informelle Teamgespräche oder externe Audits ersetzen sie nicht, da sie spezifisch auf die Selbstorganisation und Eigenverantwortung des Scrum-Teams abzielt.
- **Beispiel / Code:** ```java
// Beispiel für eine strukturierte Retrospective mit drei Fragen (Mad/Sad/Glad)
public class SprintRetrospective {
    public static void main(String[] args) {
        List<String> feedback = Arrays.asList(
            "Mad: Build-Pipeline war instabil (3x fehlgeschlagen)",
            "Sad: Daily Scrums wurden oft zu lang (über 15 Minuten)",
            "Glad: Pair Programming hat die Codequalität verbessert"
        );
        
        // Maßnahmen ableiten
        List<String> actionItems = deriveImprovements(feedback);
        System.out.println("Umzusetzende Maßnahmen: " + actionItems);
    }
    
    private static List<String> deriveImprovements(List<String> feedback) {
        return feedback.stream()
            .filter(item -> item.startsWith("Mad") || item.startsWith("Sad"))
            .map(item -> "- [ ] " + item.split(":")[1].trim() + " beheben")
            .collect(Collectors.toList());
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 9b4
- **Vorgänger / Parent:** [[Scrum-Events]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Scrum-Events]]
  - [[Scrum]]
