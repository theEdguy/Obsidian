---
id: ee8047c2-4207-44e5-b379-28f366007bab
title: "Application Programming Interface (API)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - schnittstelle
  - softwarearchitektur
  - kommunikation
  - verteilte-systeme
  - abstraktion
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Application Programming Interface (API)]]

- **Kernkonzept:** Eine [[Application Programming Interface|API]] definiert eine Schnittstelle, über die [[Softwarekomponente|Softwarekomponenten]] miteinander kommunizieren und [[Funktionalität|Funktionalitäten]] austauschen, ohne deren interne [[Implementierung]] zu kennen.
- **Nutzen & Zweck:** Eine [[API]] ermöglicht die [[Abstraktion]] von [[Komplexität]], fördert die [[Wiederverwendbarkeit]] von [[Code]] und erleichtert die [[Integration]] verschiedener [[Systeme]] oder [[Dienst|Dienste]]. Sie löst das Problem der direkten [[Abhängigkeit]] zwischen [[Komponente|Komponenten]] und ermöglicht [[Modularität]] in [[Verteilte Systeme|verteilten Systemen]].
- **Abgrenzung & Grenzen:** Eine [[API]] sollte nicht genutzt werden, wenn direkte [[Hardware]]-Zugriffe oder [[Low-Level]]-Operationen erforderlich sind, die keine [[Abstraktion]] erlauben. Alternativen wie [[Systemaufruf|Systemaufrufe]] oder [[Bibliothek|Bibliotheken]] bieten hier mehr Kontrolle, sind aber weniger portabel. Zudem kann eine übermäßig komplexe [[API]] die [[Wartbarkeit]] erschweren.
- **Beispiel / Code:** Ein einfaches Beispiel für eine [[REST-API]] in Python mit dem Framework Flask:

```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api/greet/<name>', methods=['GET'])
def greet(name):
    return jsonify({'message': f'Hello, {name}!'})

if __name__ == '__main__':
    app.run(debug=True)
```

Diese [[API]] stellt eine [[Endpunkt|Endpunkt]] bereit, der auf HTTP-GET-Anfragen reagiert und eine JSON-Antwort zurückgibt.
