---
id: a30de357-f8a5-43bb-8be5-238afb7d04a6
title: "Komposition"
date: 2026-06-24
tags:
  - software_engineering
  - architektur
  - modularisierung
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Komposition]]

- **Kernkonzept:** Die [[Komposition]] ist ein zentrales [[Designprinzip]] in der [[Objektorientierung|objektorientierten Programmierung]] und eine spezielle Form der [[Assoziation]] in der [[Modellierung]], die eine starke [[Teil-Ganzes-Beziehung]] mit [[Existenzabhängigkeit]] beschreibt. Sie steht in engem Zusammenhang mit der [[Dekomposition]], bei der ein [[System]] in kleinere, handhabbare [[Komponente|Komponenten]] zerlegt wird, um [[Komplexität]] zu reduzieren und [[Modularisierung]] zu fördern. Beide Konzepte ergänzen sich, indem [[Komposition]] die strukturelle [[Hierarchie]] und [[Verantwortlichkeit]] der [[Teil|Teile]] innerhalb des [[Ganzen]] definiert, während [[Dekomposition]] die initiale Zerlegung des [[Systems]] in [[Modul|Module]] oder [[Subsystem]]e ermöglicht.
- **Nutzen & Zweck:** Die [[Komposition]] fördert [[Lose_Kopplung|lose Kopplung]] und [[Flexibilität]], indem [[Komponente|Komponenten]] zur Laufzeit ausgetauscht werden können, ohne auf [[Vererbung]] zurückzugreifen. Sie löst das Problem der Modellierung von [[Struktur|Strukturen]], bei denen [[Teil|Teile]] ohne das [[Ganze]] nicht sinnvoll existieren können, und stellt die [[Konsistenz]] des [[Systems]] sicher, indem das [[Ganze]] die [[Erzeugung]], [[Verwaltung]] und [[Zerstörung]] seiner [[Teil|Teile]] übernimmt. Besonders nützlich ist sie bei der Strukturierung von [[GUI-Komponente|GUI-Komponenten]], [[Dokumentenstruktur|Dokumentenstrukturen]] oder komplexen [[Systemarchitektur|Systemarchitekturen]], in denen [[Existenzabhängigkeit]] erforderlich ist. Durch die [[Kapselung]] der [[Teil|Teile]] wird zudem die [[Kohäsion]] erhöht und die [[Komplexität]] reduziert. 

Die [[Dekomposition]] ergänzt dies, indem sie die Zerlegung eines [[Software-Systems]] in kleinere [[Modul|Module]] oder [[Komponente|Komponenten]] ermöglicht, um [[Wiederverwendung]], [[Parallelisierung]] und [[Wartbarkeit]] zu verbessern. Sie bildet die Grundlage für [[Modularisierung]] und [[Microservices]] und schafft klare [[Schnittstelle|Schnittstellen]] zwischen den [[Teil|Teilen]] eines [[Systems]]. Beide Konzepte zusammen ermöglichen eine skalierbare und wartbare [[Architektur]], insbesondere in [[Großprojekt|Großprojekten]] oder [[Verteilte_Systeme|verteilten Systemen]].
- **Abgrenzung & Grenzen:** Die [[Komposition]] erfordert mehr [[Boilerplate-Code]] als [[Vererbung]] und kann zu [[Komplexität]] führen, wenn zu viele [[Schicht|Schichten]] entstehen. Sie ist ungeeignet, wenn die [[Teil|Teile]] unabhängig vom [[Ganzen]] existieren oder von mehreren [[Ganzen]] referenziert werden können – in solchen Fällen sollte eine [[Aggregation]] oder eine einfache [[Assoziation]] verwendet werden. Im Gegensatz zur [[Aggregation]], die eine schwächere [[Teil-Ganzes-Beziehung]] darstellt, impliziert [[Komposition]] eine strikte [[Existenzabhängigkeit]] und darf keine [[Zyklische_Abhängigkeit|zyklischen Abhängigkeiten]] enthalten. Zudem ist sie weniger intuitiv für einfache [[Hierarchie|Hierarchien]] und ungeeignet, wenn [[Teil|Teile]] dynamisch zwischen verschiedenen [[Ganzen]] wechseln müssen. Bei [[Entwurfsmuster|Mustern]] wie dem [[Composite_Pattern]] wird [[Komposition]] gezielt eingesetzt, um rekursive [[Struktur|Strukturen]] abzubilden. 

Die [[Dekomposition]] ist kein Ersatz für [[Integration]], da die zerlegten [[Komponente|Komponenten]] später wieder zusammengeführt werden müssen. Sie unterscheidet sich von einer [[Monolithische_Architektur|monolithischen Architektur]] durch ihren Fokus auf [[Trennung_von_Belangen]] und ist nicht sinnvoll bei trivialen [[Systemen]], bei denen der Overhead der [[Modularisierung]] den Nutzen übersteigt. Beide Konzepte – [[Komposition]] und [[Dekomposition]] – müssen sorgfältig abgewogen werden, um eine ausgewogene [[Architektur]] zu schaffen, die weder zu stark fragmentiert noch zu starr gekoppelt ist.
- **Beispiel / Code:** ```java
// Beispiel für [[Komposition]] mit Existenzabhängigkeit der [[Teil|Teile]]
class Motor {
    void starten() {
        System.out.println("Motor startet");
    }
}

class Rad {
    void drehen() {
        System.out.println("Rad dreht sich");
    }
}

class Auto {
    private final Motor motor;
    private final List<Rad> raeder;

    Auto() {
        this.motor = new Motor(); // Motor existiert nur mit dem Auto
        this.raeder = new ArrayList<>();
        for (int i = 0; i < 4; i++) {
            this.raeder.add(new Rad()); // Räder existieren nur mit dem Auto
        }
    }

    void fahren() {
        motor.starten();
        for (Rad rad : raeder) {
            rad.drehen();
        }
        System.out.println("Auto fährt");
    }

    void zerstoereAuto() {
        // Zerstörung des Autos zerstört auch Motor und Räder
        this.raeder.clear();
    }
}

// Beispiel für [[Teil-Ganzes-Beziehung]] mit starker [[Kopplung]] und [[Hierarchie]]
class Verein {
    private final Vorstand vorstand;
    private final List<Team> teams;

    Verein() {
        this.vorstand = new Vorstand(); // Vorstand existiert nur mit dem Verein
        this.teams = new ArrayList<>();
    }

    void teamHinzufuegen(Team team) {
        this.teams.add(team);
    }
}

// Beispiel für [[Dekomposition]] (Modularisierung) mit klaren [[Schnittstelle|Schnittstellen]]
public interface PaymentProcessor {
    void processPayment(double amount);
}

public class CreditCardProcessor implements PaymentProcessor {
    @Override
    public void processPayment(double amount) {
        System.out.println("Zahlung von " + amount + " via Kreditkarte verarbeitet.");
    }
}

public class PayPalProcessor implements PaymentProcessor {
    @Override
    public void processPayment(double amount) {
        System.out.println("Zahlung von " + amount + " via PayPal verarbeitet.");
    }
}

// Integration der [[Komponente|Komponenten]] in ein [[System]]
public class BestellSystem {
    private final PaymentProcessor paymentProcessor;

    public BestellSystem(PaymentProcessor paymentProcessor) {
        this.paymentProcessor = paymentProcessor; // [[Komposition]] mit [[Abhängigkeitsinjektion]]
    }

    public void bezahlen(double betrag) {
        paymentProcessor.processPayment(betrag);
    }
}
```
