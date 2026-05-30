---
id: 886b1150-7988-4a27-afb9-361ad22ac8b4
title: "Zugriffskontrolle"
date: 2026-05-30
tags:
  - software_engineering
  - security
  - systemdesign
  - draft
source: "SWE Slides (Folien 151-165)"
---

# [[Zugriffskontrolle]]

- **Kernkonzept:** Die [[Zugriffskontrolle]] ist ein [[Sicherheitsmechanismus]], der regelt, welche [[Akteur|Akteure]] oder [[Systemkomponente|Systemkomponenten]] auf welche [[Ressource|Ressourcen]] (z. B. [[Daten]], [[Funktionalität]]) zugreifen dürfen. Sie umfasst [[Authentisierung]], [[Autorisierung]] und [[Protokollierung]].
- **Nutzen & Zweck:** Sie verhindert [[unbefugter_Zugriff|unbefugte Zugriffe]] und stellt sicher, dass [[Benutzer]] nur die [[Berechtigung|Berechtigungen]] haben, die für ihre [[Rolle]] erforderlich sind. Ohne sie besteht das Risiko von [[Datenleak|Datenleaks]] oder [[Sabotage]].
- **Abgrenzung & Grenzen:** Im Gegensatz zur [[Verschlüsselung]] (die [[Daten]] schützt) regelt sie *wer* auf [[Daten]] zugreifen darf. Sie sollte nicht mit [[Firewall|Firewalls]] verwechselt werden, die [[Netzwerkzugriff|Netzwerkzugriffe]] kontrollieren.
- **Beispiel / Code:** ```plaintext
Nach 3 Fehlversuchen bei der [[Anmeldung]] wird der [[Account]] für 5 Minuten gesperrt.
```
