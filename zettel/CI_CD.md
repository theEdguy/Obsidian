---
id: 7df2eedb-39a6-4441-83ae-9fb329324e91
title: "CI_CD"
date: 2026-05-30
tags:
  - software_engineering
  - devops
  - software_process
  - automatisierung
  - draft
source: "SWE Slides (Folien 316-330)"
---

# [[CI_CD]]

- **Kernkonzept:** [[CI_CD]] (Continuous Integration/Continuous Delivery) ist eine [[Praxis]] in der [[Softwareentwicklung]], bei der [[Code]]-Änderungen kontinuierlich integriert, getestet und ausgeliefert werden. Ziel ist die schnelle Bereitstellung von [[Software]] mit hoher [[Qualität]].
- **Nutzen & Zweck:** Es löst das Problem der späten Fehlererkennung und manuellen [[Deployment|Deployments]], die zu [[Qualitätsproblemen]] und Verzögerungen führen. Ermöglicht schnelle Feedback-Schleifen und automatisierte [[Auslieferung]].
- **Abgrenzung & Grenzen:** Nicht sinnvoll für kleine [[Projekt|Projekte]] mit geringer [[Code]]-Basis oder wenn der [[Aufwand]] für die Einrichtung der [[Infrastruktur]] zu hoch ist.
- **Beispiel / Code:** Kein Code-Beispiel, da es sich um eine [[Praxis]] handelt. Typische Schritte:
1. [[Code]] in [[Repository]] committen
2. Automatisierte [[Build]]-Pipeline auslösen
3. [[Test|Tests]] durchführen
4. Bei Erfolg: [[Deployment]] in Staging/Produktion.
