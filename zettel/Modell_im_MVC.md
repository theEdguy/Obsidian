---
id: dc7a8579-06d6-41b7-bce6-e5a75d9e6540
title: "Modell_im_MVC"
date: 2026-05-30
tags:
  - software_engineering
  - design_pattern
  - software_architektur
  - datenmodellierung
  - draft
source: "SWE Slides (Folien 226-240)"
---

# [[Modell_im_MVC]]

- **Kernkonzept:** Das [[Modell]] im [[Model_View_Controller_Pattern|MVC-Muster]] kapselt die [[Daten]] und die domänenspezifische [[Logik]] einer [[Anwendung]]. Es ist unabhängig von der [[Benutzeroberfläche]] und benachrichtigt [[Beobachter|Beobachter]] über Änderungen.
- **Nutzen & Zweck:** Es löst das Problem der [[Vermischung_von_Daten_und_Logik|Vermischung von Daten und Logik]] mit der [[Präsentation]] und ermöglicht die [[Wiederverwendbarkeit]] des [[Modell|Modells]] in verschiedenen [[Kontext|Kontexten]].
- **Abgrenzung & Grenzen:** Nicht zu verwechseln mit reinen [[Datenstruktur|Datenstrukturen]] ohne [[Logik]]. Unterscheidet sich von [[Active_Record_Pattern]] durch die explizite Trennung von [[Daten]] und [[Geschäftslogik]].
- **Beispiel / Code:** ```java
public class ProductModel {
    private String productName;
    private List<Observer> observers = new ArrayList<>();
    
    public void addObserver(Observer observer) {
        observers.add(observer);
    }
    
    public void setProductName(String name) {
        this.productName = name;
        notifyObservers();
    }
    
    private void notifyObservers() {
        for (Observer observer : observers) {
            observer.update();
        }
    }
    
    public String getProductName() {
        return productName;
    }
}
```
