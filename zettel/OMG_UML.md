---
id: ea52f53f-9cab-4047-b9ab-a7a35d07d423
title: "OMG UML"
date: 2026-06-24
tags:
  - software_engineering
  - standard
  - uml
  - draft
source: "software_engineering_kapitel_15"
---

# [[OMG UML]]

- **Kernkonzept:** OMG UML (Unified Modeling Language) ist ein standardisiertes [[Modellierungssprache|Modellierungsframework]] der [[Object_Management_Group|Object Management Group (OMG)]] zur Spezifikation, Visualisierung, Konstruktion und Dokumentation von [[Software-System|Software-Systemen]], insbesondere im [[Objektorientierung|objektorientierten]] Bereich. Es bietet eine einheitliche Notation für [[Strukturdiagramm|Struktur-]] und [[Verhaltensdiagramm|Verhaltensdiagramme]] wie [[Klassendiagramm|Klassendiagramme]], [[Use-Case-Diagramm|Use-Case-Diagramme]] oder [[Sequenzdiagramm|Sequenzdiagramme]] und ermöglicht die Darstellung von [[Architektur|Architekturen]], [[Schnittstelle|Schnittstellen]] und [[Entwurfsmuster|Entwurfsmustern]].
- **Nutzen & Zweck:** OMG UML löst das Problem der uneinheitlichen und missverständlichen Kommunikation in der [[Softwareentwicklung]] durch eine universelle, grafische [[Modellierungssprache|Sprache]] für die Modellierung von [[Software-System|Systemen]]. Es ermöglicht [[Entwickler|Entwicklern]], [[Architekt|Architekten]] und [[Stakeholder|Stakeholdern]], komplexe [[Software-System|Systeme]] konsistent zu beschreiben, [[Anforderung|Anforderungen]] präzise zu erfassen und [[Designentscheidung|Designentscheidungen]] transparent zu dokumentieren. Dadurch wird die Zusammenarbeit zwischen [[Team|Teams]] verbessert, [[Missverständnis|Missverständnisse]] reduziert, die [[Wartbarkeit]] von Software erhöht und die [[Wiederverwendbarkeit]] von [[Komponente|Komponenten]] gefördert. Zudem dient es als Grundlage für [[Refactoring]], [[Systemanalyse]] und die Planung von [[Software-Projekt|Software-Projekten]] vor der Implementierung.
- **Abgrenzung & Grenzen:** OMG UML sollte nicht genutzt werden, wenn es um die Modellierung nicht-objektorientierter [[Software-System|Systeme]], sehr einfacher Anwendungen oder agiler [[Prototyp|Prototypen]] geht, da der Overhead der Notation den Nutzen übersteigen kann. Es unterscheidet sich von Alternativen wie [[SysML]] (für [[System-Engineering]]) oder [[BPMN]] (für [[Geschäftsprozess|Geschäftsprozesse]]) durch seinen Fokus auf [[Softwareentwicklung]] und [[Objektorientierung|objektorientierte]] Paradigmen. Zudem ist UML keine [[Programmiersprache]] und ersetzt keine [[Implementierung|Implementierungsdetails]] – es dient ausschließlich der abstrakten Beschreibung. Für [[Echtzeitsystem|Echtzeit-]] oder [[Eingebettetes_System|eingebettete Systeme]] können spezifischere Notationen wie [[MARTE]] (ein UML-Profil) geeigneter sein. Bei informellen oder leichtgewichtigen Ansätzen kann UML überdimensioniert wirken, da es einen hohen [[Formalisierungsgrad]] erfordert.
- **Beispiel / Code:** ```java
// Beispiel 1: UML-Klassendiagramm-Notation als Java-Code-Äquivalent (Assoziation & Bidirektionalität)
public class Mitglied {
    private String name;
    private int mitgliedsnummer;
    
    // Assoziation zu Verein (1..* Beziehung)
    private Verein verein;
    
    public Mitglied(String name, int mitgliedsnummer) {
        this.name = name;
        this.mitgliedsnummer = mitgliedsnummer;
    }
    
    public void setVerein(Verein verein) {
        this.verein = verein;
    }
}

public class Verein {
    private String name;
    private List<Mitglied> mitglieder = new ArrayList<>();
    
    public void addMitglied(Mitglied mitglied) {
        mitglieder.add(mitglied);
        mitglied.setVerein(this);
    }
}

// Entspricht einem UML-Klassendiagramm mit:
// - Klassen 'Mitglied' und 'Verein'
// - Attributen (name, mitgliedsnummer)
// - Bidirektionaler Assoziation (1 Verein hat * Mitglieder)


// Beispiel 2: UML-Klassendiagramm-Notation als Java-Code-Äquivalent (Vererbung & Abstraktion)
public abstract class Cipher {
    public abstract void setKey(String key);
    public abstract String encrypt(String data);
    public abstract String decrypt(String data);
}

public class AESCipher extends Cipher {
    @Override
    public void setKey(String key) {
        // Implementierung der Schlüsselgenerierung für AES
    }
    
    @Override
    public String encrypt(String data) {
        // Verschlüsselungslogik
        return "encrypted_data";
    }
    
    @Override
    public String decrypt(String data) {
        // Entschlüsselungslogik
        return "decrypted_data";
    }
}

// Das obige Java-Beispiel entspricht einer UML-Klassenhierarchie mit:
// - Abstrakter Klasse 'Cipher' (kursiv dargestellt in UML)
// - Konkreter Klasse 'AESCipher' mit Implementierung der Methoden
// - Vererbungsbeziehung (durchgezogene Linie mit geschlossener Pfeilspitze)
```
