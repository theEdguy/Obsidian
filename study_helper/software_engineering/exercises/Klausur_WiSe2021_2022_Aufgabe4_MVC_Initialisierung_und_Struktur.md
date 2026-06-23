---
id: 3f70a312-34d5-40b9-ad69-d5faaf8a21ca
title: "Klausur_WiSe2021_2022_Aufgabe4_MVC_Initialisierung_und_Struktur"
date: 2026-05-30
tags:
  - software_engineering
  - wise2021_2022
  - klausur_ws_2021_2022
  - mvc
  - entwurfsmuster
  - software_architektur
  - observer_pattern
  - klassendiagramm
  - exercise
  - draft
source: "SWE 2021-2022 mit Loesung.pdf"
---

# [[Klausur_WiSe2021_2022_Aufgabe4_MVC_Initialisierung_und_Struktur]]

- **Aufgabenstellung:** 
  - **a:**
  (7 Punkte) Ergänzen Sie die fehlenden Beschriftungen in der schematischen Abbildung des MVC-Initialisierungsprozesses. Die Abbildung zeigt die Initialisierung eines Systems, das das [[Model_View_Controller|MVC-Muster]] zur Entkopplung von Oberfläche und Geschäftslogik nutzt. Achten Sie insbesondere auf:
  - Die korrekte Benennung der beteiligten Komponenten (Model, View, Controller).
  - Die notwendigen Parameter der einzelnen Operationen (z. B. Referenzen, die zwischen den Komponenten übergeben werden).
  - Die typische Reihenfolge der Initialisierungsschritte.
  - **b:**
  (4 Punkte) Passen Sie die schematische Darstellung so an, dass sie folgende Sachverhalte abbildet:
  - Eine Anwendung verfügt in der Regel über viele [[View|Views]].
  - Eine [[View]] kann viele [[Controller]] beinhalten.
  - Eine Anwendung ohne [[View|Views]] ist sinnlos, eine [[View]] ohne [[Controller]] jedoch nicht zwingend.
  Zeigen Sie die Beziehungen zwischen den Komponenten klar auf und ergänzen Sie ggf. fehlende Pfeile oder Referenzen.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **beschreibung:**
  Die typische Initialisierung eines MVC-Systems erfolgt in folgenden Schritten:
  1. Das **Model** wird initialisiert (z. B. mit Geschäftslogik oder Daten).
  2. Die **View** wird erstellt und erhält eine Referenz auf das **Model**, um Daten anzuzeigen.
  3. Der **Controller** wird initialisiert und erhält Referenzen auf **Model** und **View**, um Benutzerinteraktionen zu verarbeiten.
  4. Die **View** registriert sich beim **Model** als [[Observer|Observer]] (falls das [[Observer_Pattern]] verwendet wird), um bei Änderungen benachrichtigt zu werden.
  
  Die Beschriftungen der Abbildung sollten wie folgt lauten:
  - **Model** (ohne Parameter, da es unabhängig initialisiert wird).
  - **View(Model model)** (erhält eine Referenz auf das **Model**).
  - **Controller(Model model, View view)** (erhält Referenzen auf **Model** und **View**).
  - **model.addObserver(view)** (falls das [[Observer_Pattern]] genutzt wird).
    - **hinweis:** Falls die Abbildung Pfeile für Rückrufe oder Benachrichtigungen enthält, sollten diese als `update()` oder `notify()` beschriftet werden, um das [[Observer_Pattern]] widerzuspiegeln.
  - **b:**
  - **beschreibung:**
  Die angepasste schematische Darstellung sollte folgende Elemente enthalten:
  - **Ein Model** (zentrale Geschäftslogik).
  - **Mehrere Views** (z. B. View1, View2), die jeweils eine Referenz auf das **Model** besitzen.
  - **Mehrere Controller** pro View (z. B. Controller1, Controller2 für View1), die Referenzen auf das **Model** und die zugehörige **View** halten.
  - **Optionale Controller**: Eine View kann auch ohne Controller existieren, aber nicht umgekehrt.
  
  Die Beziehungen sollten wie folgt visualisiert werden:
  - **Model** → **View1**, **View2** (Referenzen für Datenzugriff).
  - **View1** → **Controller1**, **Controller2** (mehrere Controller pro View).
  - **Controller1** → **Model** und **View1** (Referenzen für Interaktion).
  - **View1** → **Model** (Registrierung als [[Observer|Observer]], falls das [[Observer_Pattern]] genutzt wird).
  
  Pfeile für Benachrichtigungen (z. B. `update()`) sollten vom **Model** zu allen registrierten **Views** zeigen.
- **Theoretischer Bezug:** 
  - [[Model_View_Controller|MVC-Muster]]
  - [[Observer_Pattern]]
  - [[Lose_Kopplung]]
  - [[Klassendiagramm]]
  - [[Entwurfsmuster]]
- **Stolpersteine / Fehlerquellen:** 
  - Vermischung der Initialisierungsreihenfolge: Oft wird fälschlich angenommen, dass der Controller zuerst initialisiert wird. Tatsächlich wird das **Model** typischerweise zuerst erstellt.
  - Fehlende Referenzen: Vergessen, dass der **Controller** sowohl das **Model** als auch die **View** benötigt, um Benutzerinteraktionen zu verarbeiten.
  - Falsche Annahme zur [[View|View]]-Controller-Beziehung: Eine **View** kann ohne **Controller** existieren, aber ein **Controller** benötigt immer eine **View**.
  - Unklare [[Observer|Observer]]-Registrierung: Oft wird nicht berücksichtigt, dass die **View** sich beim **Model** als [[Observer|Observer]] registrieren muss, um auf Änderungen reagieren zu können.
  - Überflüssige Abhängigkeiten: Einführung von Abhängigkeiten zwischen **Views** oder **Controllern**, die gegen das Prinzip der [[Lose_Kopplung]] verstoßen.
