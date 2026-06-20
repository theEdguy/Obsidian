---
id: 9724c834-a38c-5ff4-a09b-3e1638ca47e7
title: "REST (Representational State Transfer)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_2
  - draft
source: "Kapitel 2: Architekturen"
---

# [[REST (Representational State Transfer)]]

- **Kernkonzept:** Ressourcenbasierter Architekturstil auf Basis einheitlicher Schnittstellen und zustandsloser Kommunikation. Jede Ressource ist über eine eindeutige URI adressierbar. Operationen basieren auf Standard-Methoden (HTTP POST/Create, GET/Read, PUT/Update, DELETE/Delete). Nachrichten sind selbstbeschreibend.
- **Nutzen & Zweck:** Ressourcenbasierter Architekturstil auf Basis einheitlicher Schnittstellen und zustandsloser Kommunikation. Jede Ressource ist über eine eindeutige URI adressierbar. Operationen basieren auf Standard-Methoden (HTTP POST/Create, GET/Read, PUT/Update, DELETE/Delete). Nachrichten sind selbstbeschreibend.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
PUT http://mybucket.s3.amazonaws.com/myobject.txt
```
