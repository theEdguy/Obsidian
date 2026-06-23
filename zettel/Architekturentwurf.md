---
id: 054b65c0-15c7-4565-ac8a-b929e9b4267b
title: "Architekturentwurf"
date: 2026-06-23
tags:
  - software_engineering
  - design
  - draft
source: "software_engineering_kapitel_09"
---

# [[Architekturentwurf]]

- **Kernkonzept:** Der Architekturentwurf im Software-Engineering definiert die grundlegende Struktur eines Softwaresystems, einschließlich seiner Komponenten, Konnektoren, Module und deren Wechselwirkungen. Er dient als Blaupause für die Implementierung und legt technische sowie organisatorische Rahmenbedingungen fest.
- **Nutzen & Zweck:** Der Architekturentwurf löst das Problem der Komplexitätsbewältigung in Softwareprojekten, indem er frühzeitig eine klare, skalierbare und wartbare Systemstruktur schafft. Er ermöglicht die Identifikation zentraler Schnittstellen, die Verteilung von Verantwortlichkeiten und die Abstimmung mit funktionalen sowie nicht-funktionalen Anforderungen, wodurch Risiken reduziert und die Zusammenarbeit im Team verbessert werden.
- **Abgrenzung & Grenzen:** Der Architekturentwurf sollte nicht in frühen Projektphasen übermäßig detailliert ausgearbeitet werden, wenn Anforderungen noch unklar oder volatil sind. Er unterscheidet sich von der Analysephase, die sich auf die Problemdomäne konzentriert, sowie vom detaillierten Design, das Implementierungsdetails einzelner Komponenten festlegt. Alternativen wie ad-hoc-Entwicklung oder prototypische Ansätze eignen sich nur für kleine, kurzlebige Projekte ohne langfristige Wartungsanforderungen.
- **Beispiel / Code:** ```java
// Beispiel: Schichtenarchitektur (Layered Architecture) mit klaren Verantwortlichkeiten
public class MitgliedService {
    private MitgliedRepository mitgliedRepository;
    private EmailService emailService;

    public void abteilungVerlassen(Mitglied mitglied, Abteilung abteilung) {
        // Geschäftslogik: Mitglied aus Abteilung entfernen
        mitgliedRepository.entferneAusAbteilung(mitglied, abteilung);
        
        // Benachrichtigung bei Statusänderung
        if (mitglied.getAbteilungen().isEmpty()) {
            mitglied.setStatus(MitgliedStatus.PASSIV);
            emailService.sendeBenachrichtigung(mitglied, "Ihr Status wurde auf 'passiv' gesetzt.");
        }
    }
}

// Schnittstelle zur Datenhaltung (Repository-Pattern)
public interface MitgliedRepository {
    void entferneAusAbteilung(Mitglied mitglied, Abteilung abteilung);
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 6
- **Vorgänger / Parent:** keine
- **Folgezettel / Unterzettel:**
  - [[Systemarchitektur]]
  - [[Komponentenmodell]]
  - [[Schnittstellendesign]]
- **Querverweise:**
  - [[Systemdesign]]
  - [[Software-Architektur]]
