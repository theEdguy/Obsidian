---
id: ebfc5c12-4173-4194-9e8f-fdc90f2edbdb
title: "One-Way Call"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - kommunikation
  - schichtenmodell
  - asynchron
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[One-Way Call]]

- **Kernkonzept:** Ein [[One-Way Call]] ist ein [[Kommunikationsmuster|Kommunikationsmuster]] in [[geschichteten Architekturen|geschichteten Architekturen]], bei dem eine [[Schicht]] eine Anfrage an eine darunterliegende [[Schicht]] sendet, ohne auf eine Antwort zu warten.
- **Nutzen & Zweck:** Das Konzept ermöglicht [[asynchrone Kommunikation]] zwischen [[Schichten]] und reduziert [[Abhängigkeiten]] sowie [[Latenzzeiten]], da der [[Aufrufer]] nicht auf eine [[Rückmeldung]] warten muss. Es löst das [[Problem]] der [[Blockierung]] bei [[synchronen Aufrufen]] und eignet sich für [[Fire-and-Forget-Szenarien]] wie [[Logging]] oder [[Benachrichtigungen]].
- **Abgrenzung & Grenzen:** Ein [[One-Way Call]] sollte nicht genutzt werden, wenn eine [[Bestätigung]] oder [[Rückgabe]] von Daten erforderlich ist, da keine Antwort erfolgt. Im Gegensatz zu [[Request/Response]] oder [[Upcall]] fehlt die [[Rückkopplung]], was bei kritischen [[Operationen]] zu [[Fehleranfälligkeit]] führen kann. Alternativen wie [[asynchrone Rückrufe]] oder [[Message Queues]] bieten mehr [[Kontrolle]] über den [[Datenfluss]].
- **Beispiel / Code:** Ein einfaches Beispiel in Python mit Sockets, bei dem der Client eine Nachricht sendet, ohne auf eine Antwort zu warten:

```python
# Client (One-Way Call)
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.connect(("localhost", 12345))
s.send(b"Daten ohne Antwort")  # Fire-and-Forget
s.close()
```

Auf Serverseite wird die Nachricht empfangen, aber keine Antwort gesendet (z. B. für Logging-Zwecke).
