---
aliases:
- Controller
date: 2026-05-30
id: ff49f9cb-a271-4199-8ec5-ed78369247b3
source: SWE Slides (Folien 226-240)
tags:
- software_engineering
- design_pattern
- eingabeverarbeitung
- software_architektur
- draft
title: Controller_im_MVC
---

# [[Controller_im_MVC]]

- **Kernkonzept:** Der [[Controller]] im [[Model_View_Controller_Pattern|MVC-Muster]] verarbeitet [[Benutzereingabe|Benutzereingaben]], interpretiert sie und leitet sie als [[Aktion|Aktionen]] an das [[Modell]] weiter. Er enthält keine domänenspezifische [[Logik]].
- **Nutzen & Zweck:** Er löst das Problem der [[Vermischung_von_Eingabe_und_Logik|Vermischung von Eingabe und Logik]] und ermöglicht die [[Entkopplung]] der [[Benutzeroberfläche]] von der [[Geschäftslogik]].
- **Abgrenzung & Grenzen:** Sollte keine domänenspezifische [[Logik]] enthalten – diese gehört ins [[Modell]]. Unterscheidet sich von [[Presenter]] im [[MVP_Pattern]] durch die direkte Interaktion mit der [[View]].
- **Beispiel / Code:** ```java
public class ProductController {
    private ProductModel model;
    private ProductView view;
    
    public ProductController(ProductModel model, ProductView view) {
        this.model = model;
        this.view = view;
    }
    
    public void handleUserInput(String input) {
        model.setProductName(input);
    }
}
```
