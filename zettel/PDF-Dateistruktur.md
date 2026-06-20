---
id: 30b20a75-159b-514a-b57e-5e801d9b34e9
title: "PDF-Dateistruktur"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_2
  - draft
source: "Kapitel 2: Bildrepräsentation"
---

# [[PDF-Dateistruktur]]

- **Kernkonzept:** Ein hierarchisch aufgebautes, geräteunabhängiges Dokumentenformat. Es besteht aus: Header (%PDF-X.Y), Body (indirekte Objekte wie Catalog, Pages, Page, Content-Streams), xref (Index aller Byte-Offsets der Objekte für wahlfreien Zugriff) und Trailer. Der Trailer enthält einen Verweis auf das Root-Objekt sowie das startxref-Offset. PDF-Reader verarbeiten Dateien von hinten nach vorne.
- **Nutzen & Zweck:** Ein hierarchisch aufgebautes, geräteunabhängiges Dokumentenformat. Es besteht aus: Header (%PDF-X.Y), Body (indirekte Objekte wie Catalog, Pages, Page, Content-Streams), xref (Index aller Byte-Offsets der Objekte für wahlfreien Zugriff) und Trailer. Der Trailer enthält einen Verweis auf das Root-Objekt sowie das startxref-Offset. PDF-Reader verarbeiten Dateien von hinten nach vorne.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** ```java
trailer
<< /Size 5
   /Root 1 0 R >>
startxref
506
%%EOF
```
