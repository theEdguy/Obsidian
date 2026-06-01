---
id: 8b206a8c-a00b-4cbc-9fa9-de3c067a4483
title: "Skalierungsmechanismen (Replikation/Caching)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - skalierung
  - verteilte-systeme
  - middleware
  - performance
  - verfügbarkeit
  - replikation
  - caching
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Skalierungsmechanismen (Replikation/Caching)]]

- **Kernkonzept:** Skalierungsmechanismen wie [[Replikation]] und [[Caching]] dienen der Leistungssteigerung und Verfügbarkeitserhöhung in [[Verteilte Systeme|verteilten Systemen]], indem Daten oder Dienste redundant vorgehalten oder temporär zwischengespeichert werden.
- **Nutzen & Zweck:** Diese Mechanismen lösen das [[Skalierbarkeitsproblem|Skalierbarkeitsproblem]] in [[Verteilte Systeme|verteilten Systemen]], indem sie Lastverteilung ermöglichen, Latenzen reduzieren und die Ausfallsicherheit erhöhen. Sie sind essenziell für Systeme mit hoher Nutzerzahl oder globaler Verteilung.
- **Abgrenzung & Grenzen:** Replikation und Caching sind nicht geeignet, wenn Konsistenzanforderungen streng sind (z. B. bei Finanztransaktionen) oder wenn der Overhead durch Synchronisation die Vorteile überwiegt. Alternativen wie [[Sharding]] oder [[Load Balancing]] können in solchen Fällen besser passen. Caching ist zudem ungeeignet für Daten mit hoher Änderungsfrequenz.
- **Beispiel / Code:** Beispiel für Caching mit Redis in einer verteilten Anwendung:
```python
import redis
import json

# Verbindung zum Redis-Cache herstellen
cache = redis.Redis(host='localhost', port=6379, db=0)

# Daten aus dem Cache abrufen oder bei Fehlschlag neu laden
def get_user_data(user_id):
    cache_key = f'user:{user_id}'
    user_data = cache.get(cache_key)
    
    if user_data is None:
        # Daten aus der Datenbank laden (simuliert)
        user_data = {'id': user_id, 'name': 'Max Mustermann', 'email': 'max@example.com'}
        # Daten im Cache speichern (mit TTL von 60 Sekunden)
        cache.setex(cache_key, 60, json.dumps(user_data))
    else:
        user_data = json.loads(user_data)
    
    return user_data
```
