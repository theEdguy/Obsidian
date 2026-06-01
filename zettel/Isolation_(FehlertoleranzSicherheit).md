---
id: a1501b16-687e-40a9-ba25-47e07ffdcdff
title: "Isolation (Fehlertoleranz/Sicherheit)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - fehlertoleranz
  - sicherheit
  - virtualisierung
  - prozesse
  - verteilte-systeme
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Isolation (Fehlertoleranz/Sicherheit)]]

- **Kernkonzept:** Isolation bezeichnet die [[Trennung|Trennung]] von [[Prozess|Prozessen]] oder [[Komponente|Komponenten]] in [[Verteiltes System|verteilten Systemen]], um [[Fehler|Fehler]] oder [[Sicherheitsrisiko|Sicherheitsrisiken]] einzudämmen und die [[Stabilität]] des Gesamtsystems zu gewährleisten. Sie verhindert, dass sich [[Fehlverhalten]] oder [[Angriff|Angriffe]] auf andere Teile des Systems ausbreiten.
- **Nutzen & Zweck:** Isolation löst das Problem der [[Fehlerausbreitung]] und [[Sicherheitslücke|Sicherheitslücken]] in [[Verteiltes System|verteilten Systemen]]. Durch die [[Trennung|Trennung]] von [[Prozess|Prozessen]] oder [[Dienst|Diensten]] wird sichergestellt, dass ein [[Ausfall]] oder [[Angriff]] lokal bleibt und nicht das gesamte System beeinträchtigt. Dies erhöht die [[Fehlertoleranz]] und [[Sicherheit]].
- **Abgrenzung & Grenzen:** Isolation sollte nicht genutzt werden, wenn enge [[Interaktion]] oder [[Datenfreigabe]] zwischen [[Komponente|Komponenten]] erforderlich ist, da sie [[Performance|Performance]]-Overhead durch [[Kontextwechsel]] oder [[Kommunikationskosten]] verursachen kann. Alternativen wie [[Thread|Threads]] (gemeinsamer Adressraum) sind effizienter, bieten aber weniger Schutz. Virtualisierung (z. B. [[Container]]) ist ein Kompromiss zwischen Isolation und Effizienz.
- **Beispiel / Code:** Ein Beispiel für Isolation in der Praxis ist die Nutzung von [[Container|Containern]] (z. B. Docker) oder [[Virtuelle Maschine|virtuellen Maschinen]]:

```
// Beispiel: Isolation durch Container (Docker)
docker run --memory="512m" --cpus="1" my-isolated-service
```

Hier wird ein [[Dienst]] in einem isolierten Container ausgeführt, der maximal 512 MB RAM und eine CPU-Kern nutzt. Ein [[Absturz]] oder [[Angriff]] auf diesen Container betrifft nicht andere [[Dienst|Dienste]] auf demselben Host.
