---
aliases:
- View
date: 2026-05-30
id: 0e25b1e9-47db-4090-b519-c8a03b7ce36c
source: SWE Slides (Folien 226-240)
tags:
- software_engineering
- design_pattern
- benutzeroberfläche
- präsentation
- draft
title: View_im_MVC
---

# [[View_im_MVC]]

- **Kernkonzept:** Die [[View]] im [[Model_View_Controller_Pattern|MVC-Muster]] ist für die Darstellung der [[Daten]] aus dem [[Modell]] verantwortlich und aktualisiert sich bei Änderungen durch [[Beobachter|Beobachtermechanismen]].
- **Nutzen & Zweck:** Sie löst das Problem der [[Vermischung_von_Präsentation_und_Logik|Vermischung von Präsentation und Logik]] und ermöglicht mehrere [[Darstellung|Darstellungen]] derselben [[Daten]].
- **Abgrenzung & Grenzen:** Nicht zu verwechseln mit der [[Geschäftslogik]] oder [[Datenverarbeitung]]. Sollte keine [[Logik]] enthalten, die nicht direkt mit der [[Präsentation]] zusammenhängt.
- **Beispiel / Code:** ```java
public class ProductView implements Observer {
    private ProductModel model;
    
    public ProductView(ProductModel model) {
        this.model = model;
        model.addObserver(this);
    }
    
    public void display() {
        System.out.println("Product: " + model.getProductName());
    }
    
    @Override
    public void update() {
        display();
    }
}
```
