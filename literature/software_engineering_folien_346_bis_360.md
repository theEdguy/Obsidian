# Lektürenotiz: SWE Vorlesung Folien 346 bis 360
- **QUELLE:** `subjects/software_engineering/slides/SWE.txt` (Slide 346-360)
- **AUTOR/AUTOREN:** Prof. Dr. Thomas Fuchß
- **KEY_INSIGHTS:**
  - Das Entwurfsmuster *Abstrakte Fabrik* (Abstract Factory) ermöglicht die Erzeugung zusammengehöriger Objekte (Produktfamilien) ohne deren konkrete Klassen zu spezifizieren, was die Internationalisierung und Konsistenz der Produkte garantiert.
  - Durch die Verwendung einer abstrakten Fabrik kann der Client-Code unabhängig von den konkreten Implementierungen der Produkte bleiben, was die Flexibilität und Austauschbarkeit von Produktfamilien erhöht.
  - Die abstrakte Fabrik unterstützt verschiedene Varianten der Objekterzeugung, z. B. durch Implementierung in konkreten Fabriken, Delegation an Produktklassen oder Nutzung von Prototypen, um Hierarchien zu vereinfachen.
  - Ein zentraler Vorteil der abstrakten Fabrik ist die Gewährleistung, dass erzeugte Objekte kompatibel sind, während ein Nachteil darin besteht, dass die Erweiterung um neue Produkte Änderungen an der Fabrik und allen Unterklassen erfordert.
  - Das *Bridge*-Muster entkoppelt Abstraktion und Implementierung, sodass beide unabhängig voneinander erweitert werden können, was die Wartbarkeit und Sicherheit (z. B. durch Kapselung der Datenbankzugriffe) verbessert.

---
- **Zugehörige Zettel:**
  - [[Abstrakte_Fabrik_(Abstract_Factory)]]
  - [[Fabrikmethode]]
  - [[Prototyp_Muster]]
  - [[Brücke_(Bridge)]]
  - [[Produktfamilie]]
  - [[Lose_Kopplung]]
