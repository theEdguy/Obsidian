---
id: ab7578dc-38f8-4c3c-bf05-978b4900c8f9
title: "Broker-Komplexität (O(N))"
date: 2026-06-01
tags:
  - verteilte_systeme
  - architektur
  - middleware
  - skalierbarkeit
  - verteilte-systeme
  - koordination
  - draft
source: "VS2 Handout Chapter 02 (Architekturen)"
---

# [[Broker-Komplexität (O(N))]]

- **Kernkonzept:** Die [[Broker|Broker]]-Komplexität (O(N)) beschreibt die lineare Skalierung der Anzahl benötigter [[Wrapper|Wrapper]] in einem [[Middleware|Middleware]]-System, wenn ein zentraler [[Broker]] zur [[Koordination|Koordination]] zwischen N [[Anwendung|Anwendungen]] eingesetzt wird.
- **Nutzen & Zweck:** Das Konzept löst das [[Problem]] der quadratischen Komplexität (O(N²)) bei direkter 1-zu-1-[[Verbindung|Verbindungen]] zwischen [[Anwendung|Anwendungen]]. Durch einen [[Broker]] wird die Anzahl der [[Wrapper]] auf 2N reduziert, was die [[Skalierbarkeit]] und [[Wartbarkeit]] des Systems verbessert.
- **Abgrenzung & Grenzen:** Nicht geeignet, wenn der [[Broker]] selbst zum [[Flaschenhals]] wird oder wenn die [[Latenz]] durch die zusätzliche [[Indirektion]] kritisch ist. Alternativen wie [[Peer-to-Peer]]-Systeme oder direkte [[Kommunikation]] sind vorzuziehen, wenn keine zentrale [[Koordination]] benötigt wird.
- **Beispiel / Code:** Beispiel für eine [[Broker]]-basierte [[Middleware]]:\n\n1. Jede [[Anwendung]] kommuniziert nur mit dem [[Broker]].\n2. Der [[Broker]] leitet [[Anfrage|Anfragen]] an die passenden [[Wrapper]] weiter.\n3. Für N [[Anwendung|Anwendungen]] werden 2N [[Wrapper]] benötigt (N für Clients, N für Server).\n\nVergleich:\n- 1-zu-1: N × (N − 1) = O(N²) [[Wrapper]].\n- [[Broker]]-basiert: 2N = O(N) [[Wrapper]].
