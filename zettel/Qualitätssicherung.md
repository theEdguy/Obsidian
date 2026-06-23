---
id: 3010b10a-521b-4672-8a7e-ec658d46e444
title: "Qualitätssicherung"
date: 2026-06-23
tags:
  - software_engineering
  - qualität
  - entwicklung
  - draft
source: "software_engineering_kapitel_05"
---

# [[Qualitätssicherung]]

- **Kernkonzept:** Qualitätssicherung im Software-Engineering umfasst systematische Maßnahmen, Prozesse und Methoden, um die Funktionalität, Zuverlässigkeit, Wartbarkeit und Benutzerfreundlichkeit von Softwareprodukten sicherzustellen und kontinuierlich zu verbessern. Sie zielt darauf ab, Fehler frühzeitig zu erkennen und zu beheben, um die Softwarequalität über den gesamten Entwicklungszyklus hinweg zu gewährleisten.
- **Nutzen & Zweck:** Qualitätssicherung existiert, um die Kosten und Risiken von Softwarefehlern zu minimieren, die erst in späteren Phasen des Entwicklungsprozesses oder im Betrieb entdeckt werden. Sie löst das Problem, dass unentdeckte Mängel zu teuren Nacharbeiten, Sicherheitslücken oder unzufriedenen Nutzern führen können. Durch präventive und korrektive Maßnahmen wird sichergestellt, dass die Software den Anforderungen entspricht und langfristig wartbar bleibt. Zudem fördert sie die Transparenz und Nachvollziehbarkeit im Entwicklungsprozess.
- **Abgrenzung & Grenzen:** Qualitätssicherung sollte nicht als einmalige Aktivität oder isolierter Prozessschritt betrachtet werden, sondern als kontinuierlicher Bestandteil des gesamten Entwicklungszyklus. Sie ist keine Alternative zu agilen Methoden oder Testautomatisierung, sondern ergänzt diese. Nicht sinnvoll ist ihr Einsatz, wenn keine klaren Qualitätskriterien oder Anforderungen definiert sind, da dann keine messbaren Ziele vorliegen. Im Gegensatz zu reinen Testverfahren (z. B. Unit-Tests) umfasst Qualitätssicherung auch präventive Maßnahmen wie Code-Reviews, statische Analysen und Prozessoptimierungen.
- **Beispiel / Code:** ```java
// Beispiel für eine statische Code-Analyse mit Checkstyle (Qualitätssicherungs-Tool)
// Konfiguration in checkstyle.xml:
<module name="LineLength">
    <property name="max" value="120"/>
    <property name="severity" value="warning"/>
</module>

// Automatisierte Prüfung im Build-Prozess (z. B. mit Maven):
// <plugin>
//     <groupId>org.apache.maven.plugins</groupId>
//     <artifactId>maven-checkstyle-plugin</artifactId>
//     <version>3.2.0</version>
//     <configuration>
//         <configLocation>checkstyle.xml</configLocation>
//     </configuration>
// </plugin>
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2c
- **Vorgänger / Parent:** [[Software_Engineering]]
- **Folgezettel / Unterzettel:**
  - [[Testen]]
  - [[Code_Reviews]]
  - [[Refactoring]]
- **Querverweise:**
  - [[Software_Engineering]]
