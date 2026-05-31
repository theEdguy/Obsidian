---
id: cccdb506-b7b7-4225-b108-0750bc283f0f
title: "Information_Hiding"
date: 2026-05-31
tags:
  - software_engineering
  - objektorientiertes_design
  - entwurfsmuster
  - uml
  - kapselung
  - softwarequalitaet
  - draft
source: "Klausur_Referenz"
---

# [[Information_Hiding]]

- **Kernkonzept:** Information_Hiding (auch bekannt als Datenkapselung) ist ein fundamentales Prinzip des [[Objektorientierten_Designs]], bei dem die internen Details einer [[Klasse]] (z. B. Attribute, Implementierungslogik oder Hilfsmethoden) vor dem Zugriff von außen verborgen werden. Der Zugriff auf die Daten erfolgt ausschließlich über definierte [[Schnittstellen]] (z. B. öffentliche Methoden), um die Integrität der Daten zu wahren und unerwünschte Abhängigkeiten zu vermeiden. Das Prinzip steht in engem Zusammenhang mit dem [[Geheimnisprinzip]] und unterstützt die [[Lose_Kopplung]] sowie die [[Hohe_Kohäsion]] in Softwaresystemen.
- **Nutzen & Zweck:** Information_Hiding dient mehreren zentralen Zwecken:
1. **Kontrolle über Datenzugriff**: Durch die Einschränkung des direkten Zugriffs auf Attribute wird sichergestellt, dass Änderungen nur über validierte Methoden erfolgen (z. B. Setter mit Plausibilitätsprüfungen).
2. **Reduktion von Komplexität**: Externe Komponenten müssen sich nicht mit internen Implementierungsdetails befassen, was die Wartbarkeit und Verständlichkeit des Codes erhöht.
3. **Flexibilität und Änderbarkeit**: Interne Strukturen können modifiziert werden, ohne dass abhängige Klassen angepasst werden müssen (z. B. Umstellung von einer Liste auf ein Array als internes Speichermedium).
4. **Sicherheit**: Sensible Daten oder Algorithmen werden vor unautorisiertem Zugriff geschützt.
5. **Unterstützung von [[Design_by_Contract]]**: Durch die Definition klarer Schnittstellen können Vor- und Nachbedingungen für Methoden präzise spezifiziert werden.
- **Abgrenzung & Grenzen:** Information_Hiding ist **kein** Allheilmittel und hat klare Grenzen:
- **Nicht gleichzusetzen mit [[Abstraktion]]**: Während Abstraktion die *Sichtbarkeit* von Details auf konzeptioneller Ebene reduziert, verbirgt Information_Hiding konkrete *Implementierungsdetails* hinter einer Schnittstelle.
- **Kein Ersatz für schlechten Entwurf**: Das Prinzip kann keine mangelhafte [[Modularisierung]] oder [[Kopplung]] ausgleichen. Beispiel: Eine Klasse mit zu vielen öffentlichen Methoden (sog. "God Class") verletzt das Prinzip, selbst wenn Attribute privat sind.
- **Performance-Overhead**: In seltenen Fällen kann der indirekte Zugriff über Methoden (z. B. Getter/Setter) zu minimalen Performance-Einbußen führen, was jedoch meist vernachlässigbar ist.
- **Stolpersteine**: 
  - **Übermäßige Getter/Setter**: Das bloße Bereitstellen von Gettern und Settern für alle Attribute ohne Validierungslogik untergräbt den Zweck des Prinzips.
  - **Freundklassen (Friend Classes)**: In Sprachen wie C++ können `friend`-Deklarationen das Prinzip aushebeln, wenn sie unkritisch eingesetzt werden.
  - **Reflection-APIs**: In Sprachen wie Java oder C# können Reflection-Mechanismen die Kapselung umgehen, was in sicherheitskritischen Kontexten problematisch sein kann.
- **Beispiel / Code:** {'beschreibung': 'Das folgende Beispiel in Java veranschaulicht Information_Hiding durch die Kapselung eines Kontostands (`balance`) und die Bereitstellung kontrollierter Zugriffsmethoden. Das Klassendiagramm (als Mermaid-Code) zeigt die statischen Abhängigkeiten und die Sichtbarkeitsmodifikatoren.', 'java_code': 'public class BankAccount {\n    // Privates Attribut: von außen nicht direkt zugänglich\n    private double balance;\n    \n    // Öffentliche Schnittstelle zum Einzahlen\n    public void deposit(double amount) {\n        if (amount > 0) {\n            balance += amount;\n        } else {\n            throw new IllegalArgumentException("Betrag muss positiv sein.");\n        }\n    }\n    \n    // Öffentliche Schnittstelle zum Abheben\n    public void withdraw(double amount) {\n        if (amount > 0 && amount <= balance) {\n            balance -= amount;\n        } else {\n            throw new IllegalArgumentException("Ungültiger Betrag oder unzureichende Deckung.");\n        }\n    }\n    \n    // Öffentliche Schnittstelle zum Abfragen des Kontostands\n    public double getBalance() {\n        return balance;\n    }\n}\n\n// Verwendung der Klasse (kein direkter Zugriff auf \'balance\')\nBankAccount account = new BankAccount();\naccount.deposit(1000.0);\naccount.withdraw(200.0);\ndouble currentBalance = account.getBalance(); // 800.0', 'uml_klassendiagramm': '```mermaid\nclassDiagram\n    class BankAccount {\n        -balance: double\n        +deposit(amount: double): void\n        +withdraw(amount: double): void\n        +getBalance(): double\n    }\n```', 'sequenzdiagramm_beschreibung': 'Ein Sequenzdiagramm zur Summenbildung (z. B. für eine `calculateTotal()`-Methode in einer `Order`-Klasse) würde zeigen, wie die `Order`-Klasse intern auf gekapselte `OrderItem`-Objekte zugreift, ohne deren Attribute direkt preiszugeben. Die Kommunikation erfolgt ausschließlich über Methoden wie `getPrice()` oder `getQuantity()`.'}
