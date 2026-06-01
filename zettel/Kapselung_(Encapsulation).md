---
id: 5ee0bfe1-9aa9-4595-8406-6368b9833bc2
title: "Kapselung (Encapsulation)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - objektorientierung
  - modularität
  - verteilte-systeme
  - software-engineering
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Kapselung (Encapsulation)]]

- **Kernkonzept:** Kapselung bezeichnet das Prinzip, [[Datenstruktur|Datenstrukturen]] und [[Logik]] innerhalb einer [[Komponente]] zu verbergen und den Zugriff nur über definierte [[Schnittstelle|Schnittstellen]] zu erlauben. Dadurch wird die interne [[Implementierung]] vor externen [[Manipulation|Manipulationen]] geschützt.
- **Nutzen & Zweck:** Kapselung löst das Problem der [[Komplexität]]sbeherrschung in [[Verteilte Systeme|verteilten Systemen]], indem sie [[Modularität]] fördert, [[Fehler]] lokalisiert und [[Wartbarkeit]] verbessert. Sie ermöglicht [[Änderung|Änderungen]] der internen [[Logik]] ohne Auswirkungen auf andere [[Komponente|Komponenten]].
- **Abgrenzung & Grenzen:** Kapselung sollte nicht genutzt werden, wenn maximale [[Performance]] oder direkte [[Hardware]]-Zugriffe erforderlich sind, da [[Abstraktion]] Overhead verursacht. Alternativen wie [[Datenorientierte Architektur|datenorientierte Architekturen]] verzichten auf strikte Kapselung zugunsten von [[Flexibilität]] und [[Skalierbarkeit]].
- **Beispiel / Code:** Objektbasierte Kapselung in Python:
```python
class Bankkonto:
    def __init__(self, kontostand=0):
        self.__kontostand = kontostand  # Privates Attribut

    def einzahlen(self, betrag):
        if betrag > 0:
            self.__kontostand += betrag

    def abheben(self, betrag):
        if 0 < betrag <= self.__kontostand:
            self.__kontostand -= betrag
        else:
            raise ValueError("Ungültiger Betrag")

    def get_kontostand(self):
        return self.__kontostand
```
Der Zugriff auf `__kontostand` ist nur über Methoden möglich, die [[Validierung]] erzwingen.
