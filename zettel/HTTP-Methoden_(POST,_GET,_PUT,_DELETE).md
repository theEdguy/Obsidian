---
id: d83be0dc-ca9a-459c-a506-047567653700
title: "HTTP-Methoden (POST, GET, PUT, DELETE)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - netzwerk
  - kommunikation
  - rest
  - http
  - crud
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[HTTP-Methoden (POST, GET, PUT, DELETE)]]

- **Kernkonzept:** HTTP-Methoden definieren standardisierte [[Operation|Operationen]] zur Manipulation von [[Ressource|Ressourcen]] in [[verteilte Systeme|verteilten Systemen]], insbesondere im [[REST-Architekturstil|REST-Architekturstil]]. Sie ermöglichen das Erstellen (POST), Abrufen (GET), Aktualisieren (PUT) und Löschen (DELETE) von [[Daten|Daten]].
- **Nutzen & Zweck:** Diese Methoden standardisieren die [[Kommunikation]] zwischen [[Client|Clients]] und [[Server|Servern]], indem sie eine einheitliche [[Schnittstelle]] für [[CRUD-Operation|CRUD-Operationen]] (Create, Read, Update, Delete) bereitstellen. Sie lösen das [[Problem]] der uneinheitlichen [[Datenmanipulation]] in [[verteilte Anwendungen|verteilten Anwendungen]] und ermöglichen [[Interoperabilität]] zwischen verschiedenen Systemen.
- **Abgrenzung & Grenzen:** HTTP-Methoden sind nicht geeignet für [[Operation|Operationen]], die komplexe [[Transaktion|Transaktionen]] oder [[Zustandsänderung|Zustandsänderungen]] über mehrere [[Ressource|Ressourcen]] hinweg erfordern. Alternativen wie [[SOAP]] oder [[GraphQL]] bieten hier mehr [[Flexibilität]] oder [[Typsicherheit]], sind aber oft [[komplexer]] in der [[Implementierung]]. GET sollte niemals für [[Datenänderung|Datenänderungen]] verwendet werden, da es als [[sicher]] und [[idempotent]] gilt.
- **Beispiel / Code:** Beispiel einer REST-API mit HTTP-Methoden (Python mit Flask):

```python
from flask import Flask, request, jsonify

app = Flask(__name__)
data_store = {}

@app.route('/resource/<id>', methods=['POST'])
def create_resource(id):
    data_store[id] = request.json
    return jsonify({'status': 'created'}), 201

@app.route('/resource/<id>', methods=['GET'])
def get_resource(id):
    return jsonify(data_store.get(id, {})), 200

@app.route('/resource/<id>', methods=['PUT'])
def update_resource(id):
    data_store[id] = request.json
    return jsonify({'status': 'updated'}), 200

@app.route('/resource/<id>', methods=['DELETE'])
def delete_resource(id):
    data_store.pop(id, None)
    return jsonify({'status': 'deleted'}), 200
```
