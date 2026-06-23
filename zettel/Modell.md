---
id: b500f63f-bc08-482f-bc29-38021891112f
title: "Modell"
date: 2026-06-24
tags:
  - software_engineering
  - modellierung
  - abstraktion
  - uml
  - komponente
  - mvc
  - architekturmuster
  - draft
source: "software_engineering_kapitel_15"
---

# [[Modell]]

- **Kernkonzept:** Ein [[Modell]] ist ein vereinfachtes [[Abbild]] der [[Realität]], das gezielt von irrelevanten [[Details|Detail]] abstrahiert, um die für ein spezifisches [[Problem]] wesentlichen [[Eigenschaft|Eigenschaften]], [[Struktur|Strukturen]] und [[Zusammenhang|Zusammenhänge]] darzustellen. Im Kontext des [[Model-View-Controller|MVC]]-Architekturmusters repräsentiert das [[Modell]] die zentrale [[Komponente]], die [[Daten]], [[Geschäftslogik]] und domänenspezifische [[Regel|Regeln]] kapselt, den [[Zustand]] der Anwendung verwaltet und von der [[Präsentation]] und [[Steuerung]] getrennt ist.
- **Nutzen & Zweck:** Ein [[Modell]] existiert, um die [[Komplexität]] realer [[System|Systeme]] beherrschbar zu machen, indem es eine fokussierte, standardisierte und kommunizierbare Sicht auf die relevanten Aspekte schafft. Es löst das Problem der Überforderung durch zu viele [[Details|Detail]] und der Mehrdeutigkeit in der [[Analyse]] und im [[Design]], ermöglicht eine klare Grundlage für die [[Softwareentwicklung]] und fördert die methodische Durchgängigkeit zwischen [[Problemraum]] und [[Lösungsraum]]. Durch die Verwendung von [[Notation|Notationen]] wie [[UML]] wird die Präzision erhöht und die [[Zusammenarbeit]] zwischen [[Entwickler|Entwicklern]], [[Anwender|Anwendern]] und [[Fachexperte|Fachexperten]] verbessert. Im [[Model-View-Controller|MVC]]-Kontext trennt das [[Modell]] die [[Geschäftslogik]] von der [[Präsentation]] und [[Steuerung]], was die [[Wartbarkeit]], [[Erweiterbarkeit]], [[Testbarkeit]] und [[Wiederverwendung]] des [[Code|Codes]] erhöht. Es unterstützt die [[Dokumentation]] von [[Systemanforderung|Systemanforderungen]], ermöglicht frühzeitige [[Fehlererkennung]] durch formale [[Werkzeug|Werkzeuge]] und fördert [[Lose_Kopplung]] sowie [[Kohäsion]] innerhalb der [[Architektur]]. Zudem wird durch die zentrale Kapselung von [[Daten]] und [[Logik]] die Konsistenz der Anwendung sichergestellt und die Anpassung an sich ändernde Anforderungen erleichtert.
- **Abgrenzung & Grenzen:** Ein [[Modell]] sollte nicht genutzt werden, wenn eine vollständige Abbildung der [[Realität]] erforderlich ist, da es bewusst [[Details|Detail]] ausblendet, oder wenn es keine zusätzliche Klarheit schafft und die [[Komplexität]] unnötig erhöht – beispielsweise bei trivialen [[System|Systemen]] mit minimaler Interaktion. Es eignet sich nicht für [[Problem|Probleme]], die keine strukturierte [[Abstraktion]] zulassen oder bei denen die Relevanz von [[Eigenschaft|Eigenschaften]] nicht klar definiert werden kann. Alternativen wie direkte [[Implementierung|Implementierungen]], informelle [[Skizze|Skizzen]] oder textuelle Beschreibungen können in frühen Phasen oder für einfache [[Anwendung|Anwendungen]] sinnvoller sein, bergen jedoch das Risiko von Inkonsistenzen, mangelnder Nachvollziehbarkeit und fehlender formaler Präzision. Im Gegensatz zu [[Modell|Modellen]] bieten sie keine systematische Grundlage für [[Analyse]], [[Design]], [[Wiederverwendung]] oder [[Werkzeugunterstützung]]. Zudem ist ein [[Modell]] keine einsatzbereite Lösung, sondern eine Vorstufe zur [[Implementierung]], die erst durch weitere Schritte wie [[Refactoring]] oder [[Codegenerierung]] in ausführbaren [[Code]] überführt wird. Im [[Model-View-Controller|MVC]]-Kontext sollte das [[Modell]] nicht verwendet werden, wenn die Anwendung keine komplexe [[Geschäftslogik]] oder Datenverarbeitung erfordert, da der Overhead der Trennung in solchen Fällen unnötig ist. Es unterscheidet sich von reinen Datenhaltungsmodellen wie [[Data_Transfer_Object|DTOs]] oder [[Active_Record]] dadurch, dass es nicht nur [[Daten]] speichert, sondern auch die zugehörige [[Logik]] zur Verarbeitung und [[Validierung]] enthält. Bei Echtzeitanwendungen mit extrem niedriger Latenz kann die zusätzliche Abstraktionsebene des [[Modell|Modells]] Performance-Nachteile mit sich bringen. Alternativen wie das [[Transaction_Script_Pattern]] können in einfachen Szenarien effizienter sein, bieten jedoch weniger Flexibilität bei wachsenden Anforderungen.
- **Beispiel / Code:** ```java
// UML-Klassendiagramm als Modell (textuelle Repräsentation)
class Mitglied {
    // Attribute (Struktur) mit Sichtbarkeitsmodifikatoren und Constraints
    - name: String
    # adresse: Anschrift
    - alter: Date
    ~ leistung: Integer = 1 {leistung > 0 && leistung < 1441}
    
    // Operation (Verhalten) mit Parameter und Rückgabetyp
    + leistungsprognose(datum: Date): Integer
}

// Beispiel für ein Instanzdiagramm (M0-Ebene):
// Objekt: aMitglied:Verein::Mitglied
//   name = 'Thomas Fuchß'
//   adresse = ('76131 Karlsruhe', 'Musterstraße 1')
//   leistung = 1051

// Java-Implementierung basierend auf dem Modell
class Mitglied {
    private String name;
    protected Anschrift adresse;
    private Date alter;
    int leistung = 1; // Paketsichtbarkeit
    
    public Mitglied(String name, Anschrift adresse, Date alter, int leistung) {
        this.name = name;
        this.adresse = adresse;
        this.alter = alter;
        if (leistung > 0 && leistung < 1441) {
            this.leistung = leistung;
        } else {
            throw new IllegalArgumentException("Leistung muss zwischen 1 und 1440 liegen.");
        }
    }
    
    public int leistungsprognose(Date datum) {
        // Berechnung basierend auf Attributen und Geschäftsregel
        return this.leistung * (datum.getYear() + 1900);
    }
}

// MVC-Modell: Kapselung von Daten, Geschäftslogik und Regeln
public class MitgliedModel {
    private String name;
    private String email;
    private LocalDate beitrittsdatum;
    private List<Mitgliedschaft> mitgliedschaften;
    
    public MitgliedModel(String name, String email, LocalDate beitrittsdatum) {
        this.name = name;
        this.email = email;
        this.beitrittsdatum = beitrittsdatum;
        this.mitgliedschaften = new ArrayList<>();
    }
    
    // Geschäftslogik zur Validierung
    public boolean istEmailGueltig() {
        return email != null && email.contains("@");
    }
    
    // Geschäftslogik zur Datenverarbeitung
    public int berechneMitgliedsdauer() {
        return (int) ChronoUnit.YEARS.between(beitrittsdatum, LocalDate.now());
    }
    
    // Geschäftslogik zur Verwaltung von Mitgliedschaften
    public void addMitgliedschaft(Mitgliedschaft mitgliedschaft) {
        mitgliedschaften.add(mitgliedschaft);
    }
    
    public List<Mitgliedschaft> getMitgliedschaften() {
        return new ArrayList<>(mitgliedschaften);
    }
    
    // Getter und Setter
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
    
    public String getEmail() {
        return email;
    }
    
    public void setEmail(String email) {
        this.email = email;
    }
}

// Das Modell abstrahiert von irrelevanten Details wie z. B. der Haarfarbe des Mitglieds
// und konzentriert sich auf die für das [[System]] wesentlichen [[Eigenschaft|Eigenschaften]].
// Durch die Verwendung von [[UML]]-Notationen wie Sichtbarkeitsmodifikatoren (-, #, ~, +)
// und Constraints {leistung > 0 && leistung < 1441} wird die Präzision erhöht.
// Im [[Model-View-Controller|MVC]]-Kontext kapselt das [[Modell]] die [[Geschäftslogik]]
// und [[Daten]], ermöglicht [[Lose_Kopplung]] zwischen den [[Komponente|Komponenten]]
// und fördert die [[Wiederverwendung]] sowie [[Testbarkeit]] des [[Code|Codes]].
// Die Trennung von [[Präsentation]] und [[Steuerung]] wird durch die zentrale Rolle des
// [[Modell|Modells]] im [[Architekturmuster]] sichergestellt, was die [[Wartbarkeit]]
// und [[Erweiterbarkeit]] der Anwendung verbessert.
```
