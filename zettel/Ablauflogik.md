---
id: 1fe6e48f-d820-48c9-9c98-b4e91023270b
title: "Ablauflogik"
date: 2026-05-30
tags:
  - software_engineering
  - architektur
  - design
  - draft
source: "SWE Slides (Folien 196-210)"
---

# [[Ablauflogik]]

- **Kernkonzept:** [[Ablauflogik]] beschreibt die Steuerung und Koordination von [[Prozess|Prozessen]] und [[Operation|Operationen]] in einem System. Sie kann explizit (z. B. durch [[Zustandsmaschine|Zustandsmaschinen]]) oder implizit (z. B. durch [[Event-gesteuertes_System|Event-gesteuerte Systeme]]) implementiert werden.
- **Nutzen & Zweck:** Sie definiert, wie das System auf [[Ereignis|Ereignisse]] reagiert und [[Prozess|Prozesse]] steuert. Die [[Ablauflogik]] ist essenziell für die korrekte Ausführung von [[Anwendungsfall|Anwendungsfällen]] und die [[Konsistenz]] des Systems.
- **Abgrenzung & Grenzen:** Kein Ersatz für [[Datenmodellierung]] oder [[Algorithmen|Algorithmen]]. [[Ablauflogik]] konzentriert sich auf die Steuerung, nicht auf die Daten oder Berechnungen. Im Gegensatz zu [[Geschäftslogik]] ist sie technischer und architekturbezogen.
- **Beispiel / Code:** ```java
// Beispiel für explizite Ablauflogik (Zustandsmaschine)
public enum BestellStatus {
    ERSTELLT, BEZAHLT, VERSANDT, STORNIERT;
}

public class Bestellung {
    private BestellStatus status;
    
    public void bezahlen() {
        if (status == BestellStatus.ERSTELLT) {
            status = BestellStatus.BEZAHLT;
        }
    }
}
```
