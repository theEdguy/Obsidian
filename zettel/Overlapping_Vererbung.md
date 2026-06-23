---
id: 8abff012-a7b2-4e69-a149-74a96ffb01a9
title: "Overlapping_Vererbung"
date: 2026-06-23
tags:
  - software_engineering
  - oop
  - vererbung
  - modellierung
  - uml
  - draft
source: "software_engineering_kapitel_04"
---

# [[Overlapping_Vererbung]]

- **Kernkonzept:** [[Overlapping_Vererbung]] beschreibt eine [[Generalisierung|Generalisierungsbeziehung]] in der [[Objektorientierte_Programmierung|objektorientierten Programmierung]] und [[UML]], bei der [[Instanz|Instanzen]] einer [[Unterklasse]] gleichzeitig [[Instanz|Instanzen]] mehrerer anderer [[Unterklasse|Unterklassen]] sein können. Dies ermöglicht die Modellierung von [[Mehrfachvererbung]] und überlappenden [[Kategorie|Kategorien]] in [[Domänenmodellierung|Domänenmodellen]].
- **Nutzen & Zweck:** [[Overlapping_Vererbung]] dient der flexiblen Abbildung von [[Entität|Entitäten]], die [[Eigenschaft|Eigenschaften]] oder [[Rolle|Rollen]] mehrerer spezialisierter [[Klasse|Klassen]] gleichzeitig annehmen können. Dies löst das Problem starrer Zuordnungen zu genau einer [[Unterklasse]] und ermöglicht die Modellierung von [[Mehrfachrolle|Mehrfachrollen]] oder hybriden [[Entität|Entitäten]] in [[System|Systemen]]. Besonders nützlich ist dies in [[Domänenmodellierung|Domänenmodellen]] mit überlappenden [[Kategorie|Kategorien]], z. B. bei [[Trainer|Trainern]], die gleichzeitig mehreren [[Team|Teams]] angehören oder bei [[Produkt|Produkten]] mit multiplen [[Klassifikation|Klassifikationen]].
- **Abgrenzung & Grenzen:** [[Overlapping_Vererbung]] sollte nicht eingesetzt werden, wenn [[Objekt|Objekte]] eindeutig einer einzigen [[Unterklasse]] zugeordnet werden müssen, da dies zu unklaren [[Verantwortlichkeit|Verantwortlichkeiten]] und erhöhter [[Komplexität]] führen kann. Im Gegensatz zur [[Disjoint_Vererbung]], bei der sich [[Unterklasse|Unterklassen]] gegenseitig ausschließen, eignet sich [[Overlapping_Vererbung]] nur für Fälle, in denen [[Mehrfachzugehörigkeit|Mehrfachzugehörigkeiten]] explizit erwünscht sind. Bei einfachen [[Hierarchie|Hierarchien]] oder klar getrennten [[Kategorie|Kategorien]] ist [[Disjoint_Vererbung]] oder eine [[Komposition]] vorzuziehen. Zudem kann [[Overlapping_Vererbung]] das [[Diamond_Problem]] verstärken, wenn nicht sorgfältig durch [[Entwurfsmuster|Muster]] wie [[Schnittstelle|Schnittstellen]] oder [[Mixin]] gelöst wird.
- **Beispiel / Code:** ```java
// Beispiel für Overlapping-Vererbung in UML (konzeptionell)
// In UML wird dies mit {overlapping} am Generalisierungspfeil gekennzeichnet.

// Oberklasse
class Team {
    private String name;
    private List<Spieler> mitglieder;
    
    public Team(String name) {
        this.name = name;
    }
    
    public void hinzufuegenSpieler(Spieler spieler) {
        mitglieder.add(spieler);
    }
}

// Unterklassen mit überlappender Vererbung
class HerrenTeam extends Team {
    private int ligaStufe;
    
    public HerrenTeam(String name, int ligaStufe) {
        super(name);
        this.ligaStufe = ligaStufe;
    }
}

class LigaTeam extends Team {
    private String ligaName;
    
    public LigaTeam(String name, String ligaName) {
        super(name);
        this.ligaName = ligaName;
    }
}

// Unterklasse, die Eigenschaften beider Oberklassen kombiniert (Overlapping)
public class HerrenLigaTeam extends HerrenTeam, LigaTeam {
    public HerrenLigaTeam(String name, int ligaStufe, String ligaName) {
        super(name, ligaStufe); // Java unterstützt keine echte Mehrfachvererbung,
        this.ligaName = ligaName; // daher hier nur konzeptionell dargestellt.
    }
    
    // Kombination spezifischer Methoden und Attribute
}

// Praktische Umsetzung in Java (ohne Mehrfachvererbung) mittels Schnittstellen
interface IHerrenTeam {
    int getLigaStufe();
}

interface ILigaTeam {
    String getLigaName();
}

public class HerrenLigaTeamImpl extends Team implements IHerrenTeam, ILigaTeam {
    private int ligaStufe;
    private String ligaName;
    
    public HerrenLigaTeamImpl(String name, int ligaStufe, String ligaName) {
        super(name);
        this.ligaStufe = ligaStufe;
        this.ligaName = ligaName;
    }
    
    @Override
    public int getLigaStufe() {
        return ligaStufe;
    }
    
    @Override
    public String getLigaName() {
        return ligaName;
    }
}
```

---

## 🔗 Stellordnung & Verbindungen
- **Stellordnung ID:** 1c3
- **Vorgänger / Parent:** [[Vererbungssemantik]]
- **Folgezettel / Unterzettel:** keine
- **Querverweise:** keine
