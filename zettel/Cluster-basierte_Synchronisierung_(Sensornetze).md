---
id: afb6b3c3-a9db-5861-adb2-f755813bfeed
title: "Cluster-basierte Synchronisierung (Sensornetze)"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_1
  - draft
source: "Kapitel 1: Einführung"
---

# [[Cluster-basierte Synchronisierung (Sensornetze)]]

- **Kernkonzept:** Algorithmus zur Synchronisation von Arbeitszyklen disjunkter Sensoren zur Vermeidung dauerhafter Trennung. Jeder Knoten wählt eine zufällige Cluster-ID C. Knoten senden während der inaktiven Phase JOIN-Nachrichten. Empfängt A ein JOIN von B: Wenn C_A < C_B, leitet A die Nachricht an sein Cluster weiter und tritt C_B bei (Zeitanpassung an B). Wenn C_A > C_B, sendet A während B's aktiver Phase eine JOIN-Nachricht an B.
- **Nutzen & Zweck:** Algorithmus zur Synchronisation von Arbeitszyklen disjunkter Sensoren zur Vermeidung dauerhafter Trennung. Jeder Knoten wählt eine zufällige Cluster-ID C. Knoten senden während der inaktiven Phase JOIN-Nachrichten. Empfängt A ein JOIN von B: Wenn C_A < C_B, leitet A die Nachricht an sein Cluster weiter und tritt C_B bei (Zeitanpassung an B). Wenn C_A > C_B, sendet A während B's aktiver Phase eine JOIN-Nachricht an B.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
