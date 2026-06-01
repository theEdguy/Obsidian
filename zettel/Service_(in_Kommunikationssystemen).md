---
id: d6482985-7c59-4a1e-82a8-287781e3647c
title: "Service (in Kommunikationssystemen)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - verteilte-systeme
  - kommunikation
  - schnittstelle
  - modularisierung
  - rest
  - service-orientierung
  - modularität
  - protokoll
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Service (in Kommunikationssystemen)]]

- **Kernkonzept:** Ein [[Service|Service]] in [[Kommunikationssystem|Kommunikationssystemen]] stellt eine wohldefinierte [[Funktionalität]] bereit, die über eine [[Schnittstelle|Schnittstelle]] von anderen [[Komponente|Komponenten]] oder [[System|Systemen]] genutzt werden kann, ohne deren interne [[Implementierung]] zu kennen. Ein [[Interface|Interface]] definiert dabei die [[Schnittstelle|Schnittstelle]] zwischen [[Komponente|Komponenten]] oder [[Schicht|Schichten]], um [[Daten]]austausch und [[Interaktion]] zu standardisieren und die [[Kapselung]] zu gewährleisten.
- **Nutzen & Zweck:** Ein [[Service]] ermöglicht die [[Entkopplung]] von [[Komponente|Komponenten]] in [[verteilte Systeme|verteilten Systemen]], fördert die [[Wiederverwendbarkeit]] von [[Funktionalität|Funktionalitäten]] und vereinfacht die [[Integration]] durch standardisierte [[Schnittstelle|Schnittstellen]]. Durch die Nutzung von [[Interface|Interfaces]] wird die [[Modularität]] weiter gestärkt, da [[Komponente|Komponenten]] oder [[Schicht|Schichten]] unabhängig voneinander entwickelt, getestet und ausgetauscht werden können. Dies erleichtert die [[Erweiterbarkeit]] und [[Wartbarkeit]] von [[System|Systemen]] und ermöglicht die [[Isolation]] von [[Fehler|Fehlern]]. Zudem unterstützt es die [[Interoperabilität]] zwischen heterogenen [[System|Systemen]] durch klare [[Protokoll|Protokolle]] und [[Datenformat|Datenformate]].
- **Abgrenzung & Grenzen:** Ein [[Service]] oder [[Interface]] sollte nicht genutzt werden, wenn [[Echtzeitanforderung|Echtzeitanforderungen]] oder direkte [[Hardware]]-Zugriffe erforderlich sind, da [[Latenz]] und [[Abstraktion]] die [[Performance]] beeinträchtigen können. Im Vergleich zu [[monolithische Systeme|monolithischen Systemen]] oder [[direkte Prozeduraufruf|direkten Prozeduraufrufen]] führt die Nutzung von [[Service|Services]] und [[Interface|Interfaces]] zu höherem [[Overhead]] durch [[Netzwerkkommunikation]], [[Serialisierung]] oder [[Protokoll]]-Handling. Alternativen wie [[Funktion|Funktionen]], [[Bibliothek|Bibliotheken]] oder [[Shared Memory]] sind bei lokaler [[Ausführung]] oder extrem niedriger [[Latenz]] oft effizienter, bieten jedoch weniger [[Flexibilität]] und [[Entkopplung]]. Zudem kann die [[Komplexität]] durch die Einführung zusätzlicher [[Schicht|Schichten]] oder [[Middleware]] steigen, was die [[Fehlerdiagnose]] erschwert.
- **Beispiel / Code:** Ein einfacher [[HTTP-Service]] in Python mit dem [[Framework]] Flask, der eine [[REST-Schnittstelle]] bereitstellt:

```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/api/greet', methods=['GET'])
def greet():
    name = request.args.get('name', 'World')
    return jsonify({'message': f'Hello, {name}!'})

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```

Dieser [[Service]] nutzt eine [[Schnittstelle]] über [[HTTP]] und gibt eine [[JSON]]-Antwort zurück.

Ein weiteres Beispiel zeigt ein [[Socket]]-[[Interface]] in Python für [[Client-Server]]-Kommunikation:

**Server:**
```python
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.bind(('', 8080))
s.listen(1)
(conn, addr) = s.accept()
data = conn.recv(1024)
conn.send(data.upper().encode())
conn.close()
```

**Client:**
```python
from socket import *
s = socket(AF_INET, SOCK_STREAM)
s.connect(('localhost', 8080))
s.send(b'Hello')
print(s.recv(1024).decode())
s.close()
```

Das [[Interface]] (hier: Socket-API) abstrahiert die [[Netzwerkkommunikation]] und ermöglicht [[Interoperabilität]] zwischen [[Client]] und [[Server]].
