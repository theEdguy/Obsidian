---
id: f61497bb-624e-4aee-ba2f-0479eae0317a
title: "Partieller Ausfall"
date: 2026-06-01
tags:
  - verteilte_systeme
  - zuverlässigkeit
  - fehlertoleranz
  - systemdesign
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Partieller Ausfall]]

- **Kernkonzept:** Ein [[Ausfall]] in einem [[verteilten System]], bei dem nur ein Teil der [[Knoten]] oder [[Komponente|Komponenten]] betroffen ist, während der Rest weiter funktioniert.
- **Nutzen & Zweck:** Macht [[verteilte Systeme]] robuster, da nicht das gesamte System ausfällt, wenn ein [[Knoten]] oder eine [[Komponente]] versagt.
- **Abgrenzung & Grenzen:** Erfordert Mechanismen zur [[Fehlererkennung]] und -behebung, was die Komplexität erhöht. In einigen Fällen kann ein partieller [[Ausfall]] schwer zu diagnostizieren oder zu beheben sein.
- **Beispiel / Code:** Ein Datenbank-Cluster, bei dem ein Server ausfällt, aber die anderen Server weiterhin Anfragen bearbeiten können, während der ausgefallene Server wiederhergestellt wird.
