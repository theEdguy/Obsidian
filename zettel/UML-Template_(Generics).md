---
id: 4da6129a-572c-508e-ba83-efbfd633801b
title: "UML-Template (Generics)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_4
  - draft
source: "Kapitel 4: Objektorientierung – Vererbung"
---

# [[UML-Template (Generics)]]

- **Kernkonzept:** Parametrisierte Klassen werden in UML als Template dargestellt. Der Platzhalter (z. B. <T>) wird in einem gestrichelten Kasten in der rechten oberen Ecke der Klasse notiert. Im Java-Code entspricht dies einer generischen Klasse.
- **Nutzen & Zweck:** Parametrisierte Klassen werden in UML als Template dargestellt. Der Platzhalter (z. B. <T>) wird in einem gestrichelten Kasten in der rechten oberen Ecke der Klasse notiert. Im Java-Code entspricht dies einer generischen Klasse.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
public class P<T> {
    private T daten;
    public T getDaten() { return daten; }
}
```
