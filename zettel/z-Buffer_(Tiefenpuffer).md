---
id: cae95625-332e-541a-b84a-64266f8960c6
title: "z-Buffer (Tiefenpuffer)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_6
  - draft
source: "Kapitel 6: Graphik-Pipeline & Rasterung"
---

# [[z-Buffer (Tiefenpuffer)]]

- **Kernkonzept:** Zweidimensionaler Bildspeicher, der die z-Tiefe jedes geschriebenen Pixels speichert. Da in negativer z-Richtung geblickt wird, wird ein neues Fragment nur gezeichnet, wenn sein z-Wert größer (näher am Auge bei 0) ist als der bereits gespeicherte Wert. Verhindert das Zeichnen verdeckter Geometrie.
- **Nutzen & Zweck:** Zweidimensionaler Bildspeicher, der die z-Tiefe jedes geschriebenen Pixels speichert. Da in negativer z-Richtung geblickt wird, wird ein neues Fragment nur gezeichnet, wenn sein z-Wert größer (näher am Auge bei 0) ist als der bereits gespeicherte Wert. Verhindert das Zeichnen verdeckter Geometrie.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
