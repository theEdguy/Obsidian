---
id: 8f7b0431-313c-4519-94d8-d679fb3f809c
title: "Objekte (in der Softwarearchitektur)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - softwarearchitektur
  - verteilte-systeme
  - objektorientierung
  - kapselung
  - rpc
  - modularität
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Objekte (in der Softwarearchitektur)]]

- **Kernkonzept:** In der [[Softwarearchitektur]] sind [[Objekt|Objekte]] gekapselte Einheiten, die [[Zustand]] und [[Verhalten]] (Methoden) vereinen und über wohldefinierte [[Schnittstelle|Schnittstellen]] kommunizieren. Sie ermöglichen die Modellierung verteilter Systeme durch [[Prozeduraufruf|Prozeduraufrufe]], auch über [[Netzwerk|Netzwerke]] hinweg.
- **Nutzen & Zweck:** Objekte lösen das Problem der [[Komplexität]]sbewältigung in verteilten Systemen durch [[Kapselung]] von [[Daten]] und [[Logik]]. Sie fördern [[Wiederverwendbarkeit]], [[Modularität]] und [[Erweiterbarkeit]] von [[Komponente|Komponenten]], indem sie interne [[Implementierung]]en verbergen und klare [[Schnittstelle|Schnittstellen]] bereitstellen.
- **Abgrenzung & Grenzen:** Objektbasierte Architekturen sind weniger geeignet für Systeme mit hoher [[Skalierbarkeit]]sanforderung oder [[Latenz]]-empfindlichen Operationen, da [[Prozeduraufruf|Prozeduraufrufe]] über [[Netzwerk|Netzwerke]] [[Overhead]] verursachen. Alternativen wie [[REST]]-basierte oder [[Publish-Subscribe]]-Architekturen bieten hier [[Entkopplung]] und [[Flexibilität]]. Zudem sind sie schwerer zu warten, wenn [[Objekt|Objekte]] zu stark [[gekoppelt]] sind oder [[Zustand]] global geteilt wird.
- **Beispiel / Code:** Ein einfaches Beispiel für ein verteiltes Objekt in Python (mit Remote Method Invocation):

```python
# Server-Seite (Objekt-Implementierung)
class Calculator:
    def add(self, a, b):
        return a + b

# Client-Seite (Aufruf über Netzwerk)
from xmlrpc.client import ServerProxy
proxy = ServerProxy('http://localhost:8000')
result = proxy.add(5, 3)  # Aufruf des entfernten Objekts
print(result)  # Ausgabe: 8
```

*Erläuterung*: Das `Calculator`-Objekt kapselt die Methode `add` und wird über eine [[RPC]]-Schnittstelle (hier XML-RPC) aufgerufen. Der Client interagiert mit dem Objekt, ohne dessen interne [[Implementierung]] zu kennen.
