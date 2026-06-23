---
id: 93d79e63-4102-4570-b226-7fd2ff9c3a69
title: "Refactoring"
date: 2026-06-24
tags:
  - software_engineering
  - code-qualität
  - wartung
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Refactoring]]

- **Kernkonzept:** [[Refactoring]] bezeichnet die systematische [[Überarbeitung]] und [[Verbesserung]] der [[Code]]-Struktur und des [[Design|Designs]], ohne dessen äußeres [[Verhalten]] zu verändern. Ziel ist die Steigerung der [[Lesbarkeit]], [[Wartbarkeit]], [[Erweiterbarkeit]] und [[Kohäsion]] durch gezielte [[Transformation|Transformationen]], um [[Technische_Schuld|technische Schulden]] zu reduzieren und die langfristige [[Entwicklungsfähigkeit]] von [[Softwareprojekt|Softwareprojekten]] zu sichern. Es handelt sich um eine kontinuierliche [[Qualitätsmaßnahme]] im [[Softwareentwicklungsprozess]], die strukturelle Probleme wie [[Code-Duplikation]], [[Hohe_Kopplung]], unklare [[Abstraktion|Abstraktionen]] oder übermäßige [[Komplexität]] löst.
- **Nutzen & Zweck:** [[Refactoring]] existiert, um [[Technische_Schuld|technische Schulden]] in [[Softwareprojekt|Softwareprojekten]] zu reduzieren und die langfristige [[Entwicklungsgeschwindigkeit]] sowie [[Codequalität]] nachhaltig zu erhöhen. Es behebt konkrete Probleme wie unübersichtlichen, schwer verständlichen oder schwer erweiterbaren [[Code]], der durch iterative [[Änderung|Änderungen]], [[Zeitdruck]] oder mangelnde Pflege entstanden ist. Durch die Optimierung der [[Codequalität]] wird die [[Fehleranfälligkeit]] verringert, zukünftige [[Anforderung|Anforderungen]] lassen sich schneller umsetzen, und die Zusammenarbeit im [[Entwicklungsteam|Team]] wird erleichtert. Besonders in [[Agile_Entwicklung|agilen Entwicklungsprozessen]] ist [[Refactoring]] ein zentraler Bestandteil, um auf sich ändernde [[Anforderung|Anforderungen]] flexibel zu reagieren. Zudem fördert es die [[Robustheit]] der [[Codebasis]], beseitigt fehleranfällige [[Struktur|Strukturen]] und steigert die Effizienz bei zukünftigen [[Anpassung|Anpassungen]] oder [[Erweiterung|Erweiterungen]]. Es dient als Grundlage für [[Clean_Code]] und [[Continuous_Integration]] und ermöglicht [[Inkrementelle_Verbesserung|inkrementelle Verbesserungen]] ohne vollständige [[Neuentwicklung]]. Langfristig spart es Entwicklungszeit und Kosten, indem es die [[Wartbarkeit]] und [[Kohäsion]] des [[Code|Codes]] verbessert.
- **Abgrenzung & Grenzen:** [[Refactoring]] sollte nicht eingesetzt werden, wenn der [[Code]] bereits stabil, verständlich und wartbar ist oder wenn dringende funktionale [[Anforderung|Anforderungen]] Vorrang haben. Es unterscheidet sich von einer vollständigen [[Neuentwicklung]] (Rewriting), da es schrittweise und risikoarm erfolgt, sowie von [[Performance-Optimierung|Performance-Optimierungen]], die gezielt das [[Laufzeitverhalten]] verbessern. Ohne automatisierte [[Test|Tests]], die die [[Verhaltenskonformität]] sicherstellen, ist [[Refactoring]] ungeeignet, da das Risiko von [[Regression|Regressionen]] steigt. Zudem sollte es nicht in kritischen [[Projektphase|Projektphasen]] mit engen [[Deadline|Deadlines]] durchgeführt werden, da es Zeit und Ressourcen bindet, ohne direkt neue [[Funktionalität|Funktionalitäten]] hinzuzufügen. Es ist weder eine [[Fehlerbehebung]] (Debugging) noch eine [[Neuentwicklung]], auch wenn indirekte Verbesserungen in diesen Bereichen möglich sind. Bei extrem engem Zeitplan, fehlenden [[Test|Tests]] oder bei [[Prototyp|Prototypen]] und [[Einweg-Code]] sollte [[Refactoring]] vermieden werden, da es sonst neue [[Fehler]] einführen kann. Es ist keine [[Inkrementelle_Verbesserung|inkrementelle Verbesserung]] im Sinne von [[Bugfixing]], sondern fokussiert sich auf die [[Design|Design]]-Qualität und strukturelle [[Optimierung]] des [[Code|Codes]].
- **Beispiel / Code:** ```java
// Beispiel 1: Extraktion einer gemeinsamen [[Schnittstelle|Schnittstelle]] zur Reduktion von [[Code-Duplikation]]
// Vor Refactoring: Duplizierter Code mit spezifischer Logik
void encryptFileDES(String input, String output) {
    // DES-spezifische Logik + Dateiverarbeitung
}

void encryptFileAES(String input, String output) {
    // AES-spezifische Logik + Dateiverarbeitung
}

// Nach Refactoring: Gemeinsame [[Schnittstelle|Schnittstellen]]-Abstraktion
interface Cipher {
    void encrypt(String input, String output);
}

class DES implements Cipher { /* DES-Logik */ }
class AES implements Cipher { /* AES-Logik */ }

// Beispiel 2: Eliminierung von [[Code-Duplikation]] und Verbesserung der [[Kohäsion]]
// Vor Refactoring: Duplizierte Schleifen und hartcodierte Werte
public double berechneGesamtpreis(List<Produkt> produkte) {
    double summe = 0;
    for (Produkt p : produkte) {
        summe += p.getPreis() * 1.19; // MwSt. hartcodiert
    }
    return summe;
}

public double berechneNettoPreis(List<Produkt> produkte) {
    double summe = 0;
    for (Produkt p : produkte) {
        summe += p.getPreis(); // Duplizierung der Schleife
    }
    return summe;
}

// Nach Refactoring: Wiederverwendbare Methode mit klarer Trennung
private static final double MEHRWERTSTEUER_SATZ = 1.19;

private double summierePreise(List<Produkt> produkte, boolean mitMwSt) {
    double summe = 0;
    for (Produkt p : produkte) {
        summe += p.getPreis() * (mitMwSt ? MEHRWERTSTEUER_SATZ : 1.0);
    }
    return summe;
}

public double berechneGesamtpreis(List<Produkt> produkte) {
    return summierePreise(produkte, true);
}

public double berechneNettoPreis(List<Produkt> produkte) {
    return summierePreise(produkte, false);
}

// Beispiel 3: Aufteilung von Methoden zur Verbesserung der [[Lesbarkeit]] und [[Wartbarkeit]]
// Vor Refactoring: Unübersichtliche Methode mit doppelter Logik
public double calculateTotalPrice(double price, int quantity, boolean isPremium) {
    double total = price * quantity;
    if (isPremium) {
        total = total * 0.9;
    }
    if (quantity > 10) {
        total = total * 0.95;
    }
    return total;
}

// Nach Refactoring: Aufgeteilte Methoden mit klarer Verantwortung
public double calculateTotalPrice(double price, int quantity, boolean isPremium) {
    double total = price * quantity;
    total = applyPremiumDiscount(total, isPremium);
    total = applyBulkDiscount(total, quantity);
    return total;
}

private double applyPremiumDiscount(double total, boolean isPremium) {
    return isPremium ? total * 0.9 : total;
}

private double applyBulkDiscount(double total, int quantity) {
    return quantity > 10 ? total * 0.95 : total;
}

// Beispiel 4: Extract Method zur Verbesserung der [[Lesbarkeit]] und [[Wartbarkeit]]
// Vor Refactoring: Unstrukturierte Methode
public void printReport() {
    System.out.println("Header");
    for (String item : items) {
        System.out.println(item);
    }
    System.out.println("Footer");
}

// Nach Refactoring: Aufgeteilte Methoden mit klarer Verantwortung
public void printReport() {
    printHeader();
    printItems();
    printFooter();
}

private void printHeader() {
    System.out.println("Header");
}

private void printItems() {
    for (String item : items) {
        System.out.println(item);
    }
}

private void printFooter() {
    System.out.println("Footer");
}
```
