# Lektürenotiz: SWE Vorlesung Folien 331 bis 345
- **QUELLE:** `subjects/software_engineering/slides/SWE.txt` (Slide 331-345)
- **AUTOR/AUTOREN:** Prof. Dr. Thomas Fuchß
- **KEY_INSIGHTS:**
  - Erzeugungsmuster kapseln den Prozess der Objekterzeugung und ermöglichen es, das System unabhängig von der konkreten Implementierung und Entstehung der Objekte zu gestalten, wodurch der Fokus auf Schnittstellen gelegt wird.
  - Fabrikmethoden bieten eine dedizierte Schnittstelle zur Erzeugung von Objekten, die von Unterklassen überschrieben werden kann, um die Erzeugung spezifischer Objekte zu delegieren und die Erweiterbarkeit des Systems zu verbessern.
  - Durch die Verwendung abstrakter Fabrikmethoden oder parametrisierter Fabrikmethoden lässt sich die Objekterzeugung flexibel anpassen, sodass unterschiedliche Varianten (z. B. länderspezifische Adressformate) konsistent und ohne Code-Duplikation umgesetzt werden können.
  - Eine zentrale Herausforderung bei Erzeugungsmustern besteht darin, die Konsistenz der erzeugten Objekte sicherzustellen, insbesondere wenn mehrere zusammenhängende Objekte (z. B. Adress-, Telefon- und Geschäftslabel) aufeinander abgestimmt sein müssen.
  - Erzeugungsmuster wie das Fabrikmethoden-Muster fördern die Wiederverwendbarkeit und Wartbarkeit von Code, da sie die Kopplung zwischen Client-Code und konkreten Produktklassen reduzieren.

---
- **Zugehörige Zettel:**
  - [[Erzeugungsmuster]]
  - [[Singleton]]
  - [[Fabrikmethode]]
  - [[Abstrakte_Fabrik]]
  - [[Parametrisierte_Fabrikmethode]]
  - [[Lose_Kopplung]]
  - [[Kohäsion]]
