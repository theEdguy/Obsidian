---
id: a7d8a9e9-56b6-4ad8-9f93-0995149008b3
title: "Funktionale Anforderungen"
date: 2026-06-23
tags:
  - software_engineering
  - anforderungen
  - funktional
  - draft
source: "software_engineering_kapitel_07"
---

# [[Funktionale Anforderungen]]

- **Kernkonzept:** Funktionale [[Anforderung|Anforderungen]] definieren die spezifischen [[Funktion|Funktionen]] oder [[Verhalten|Verhaltensweisen]], die ein [[Softwaresystem]] erfüllen muss, um die [[Bedürfnis|Bedürfnisse]] der [[Anwender]] oder [[Stakeholder|Stakeholdern]] zu adressieren. Sie legen fest, WAS das System konkret leisten soll, ohne technische [[Implementierung|Implementierungsdetails]] vorwegzunehmen, und bilden den zentralen Bestandteil des [[Requirements-Engineering|Requirements-Engineerings]].
- **Nutzen & Zweck:** Funktionale [[Anforderung|Anforderungen]] schaffen Klarheit über die erwarteten [[Systemfunktion|Systemfunktionen]] und dienen als Grundlage für die [[Analyse]], das [[Design]] und die [[Implementierung]] eines [[Softwaresystem|Systems]]. Sie lösen das Problem unklarer oder missverständlicher [[Zielvorgabe|Zielvorgaben]], indem sie präzise dokumentieren, welche [[Aufgabe|Aufgaben]] das System übernehmen soll. Dadurch ermöglichen sie eine strukturierte [[Softwareentwicklung]], bei der alle [[Beteiligte|Beteiligten]] – von [[Entwickler|Entwicklern]] bis zu [[Stakeholder|Stakeholdern]] – ein gemeinsames Verständnis der [[Systemziel|Systemziele]] entwickeln. Dies reduziert das Risiko von Fehlinterpretationen, unnötigen [[Funktion|Funktionen]] oder nicht erfüllten Erwartungen und unterstützt die [[Priorisierung]] sowie [[Planung]] von Entwicklungsaufgaben. Zudem bilden sie die Basis für [[Testfall|Testfälle]] und [[Abnahmekriterium|Abnahmekriterien]], um die [[Korrektheit]] der [[Implementierung]] zu überprüfen.
- **Abgrenzung & Grenzen:** Funktionale [[Anforderung|Anforderungen]] sollten nicht mit [[nicht-funktionale_Anforderung|nicht-funktionalen Anforderungen]] verwechselt werden, die [[Qualitätsmerkmal|Qualitätsmerkmale]] wie [[Performance]], [[Sicherheit]] oder [[Benutzerfreundlichkeit]] beschreiben. Während funktionale [[Anforderung|Anforderungen]] objektiv überprüfbar sind (vorhanden oder nicht vorhanden), sind [[nicht-funktionale_Anforderung|nicht-funktionale Anforderungen]] oft subjektiv und nur durch [[Metrik|Metriken]] messbar. Funktionale [[Anforderung|Anforderungen]] eignen sich nicht, um technische [[Lösungsansatz|Lösungsansätze]], [[Implementierung|Implementierungsdetails]] oder [[Plattform|Plattformen]] festzulegen, da diese erst in späteren [[Entwicklungsphase|Entwicklungsphasen]] (z. B. [[Design]]) betrachtet werden. Ebenso sind sie ungeeignet, um [[Systemeigenschaft|komplexe Systemeigenschaften]] wie [[Skalierbarkeit]], [[Wartbarkeit]] oder [[Robustheit]] zu beschreiben, da diese eher den [[nicht-funktionale_Anforderung|nicht-funktionalen Anforderungen]] zuzuordnen sind. Zudem können sie keine prozessualen oder organisatorischen [[Rahmenbedingung|Rahmenbedingungen]] abbilden, die nicht direkt das [[Systemverhalten]] betreffen, wie z. B. [[Projektmanagement]]-Vorgaben oder [[Teamstruktur|Teamstrukturen]].
- **Beispiel / Code:** ```java
// Beispiel 1: Funktionale Anforderung "Mitglied hinzufügen" als Use-Case-Methode
public class Mitgliederverwaltung {
    private List<Mitglied> mitgliederListe;

    /**
     * Fügt ein neues Mitglied zur Mitgliederliste hinzu.
     * @param mitglied Das hinzuzufügende Mitglied
     * @return true, wenn das Mitglied erfolgreich hinzugefügt wurde, sonst false
     */
    public boolean mitgliedHinzufuegen(Mitglied mitglied) {
        if (mitglied != null && !mitgliederListe.contains(mitglied)) {
            mitgliederListe.add(mitglied);
            return true;
        }
        return false;
    }
}

// Beispiel 2: Funktionale Anforderung "Neues Mitglied anlegen" mit Persistenz
public class MitgliedVerwaltung {
    private MitgliedRepository mitgliederRepository;

    /**
     * Legt ein neues Mitglied an und speichert es in der Datenbank.
     * Anforderung F1.1: Das System muss es ermöglichen, ein neues Mitglied anzulegen.
     * @param name Name des Mitglieds
     * @param adresse Adresse des Mitglieds
     * @param abteilung Abteilung des Mitglieds
     * @return Das angelegte Mitglied
     */
    public Mitglied neuesMitgliedAnlegen(String name, String adresse, Abteilung abteilung) {
        Mitglied mitglied = new Mitglied(name, adresse, abteilung);
        mitgliederRepository.save(mitglied);
        return mitglied;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 2a1
- **Vorgänger / Parent:** [[Anforderungsidentifikation]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:**
  - [[Anforderungsanalyse]]
  - [[Use_Case]]
