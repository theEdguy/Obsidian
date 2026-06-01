---
id: eeda748f-283a-4de0-bda4-fa17215a28a6
title: "Cloud Computing"
date: 2026-06-01
tags:
  - verteilte_systeme
  - infrastruktur
  - skalierbarkeit
  - dienstleistung
  - hochleistungsrechnen
  - paralleles_rechnen
  - draft
source: "VS2 Handout Chapter 01 (Einführung)"
---

# [[Cloud Computing]]

- **Kernkonzept:** [[Cloud Computing]] bezeichnet die Bereitstellung von [[IT-Ressource|IT-Ressourcen]] (z. B. [[Rechenleistung]], [[Speicher]], [[Datenbank|Datenbanken]]) über das [[Internet]], wobei die [[Infrastruktur]] von einem Anbieter verwaltet wird. Eine spezifische Ausprägung ist [[Cluster_Computing]], bei dem eine Gruppe homogener [[Maschine|Maschinen]], verbunden über ein [[LAN]], gemeinsam als ein System arbeitet, um parallele [[Berechnung|Berechnungen]] durchzuführen.
- **Nutzen & Zweck:** [[Cloud Computing]] ermöglicht flexible und skalierbare Nutzung von [[IT-Ressource|IT-Ressourcen]] ohne eigene [[Hardware]], löst das Problem begrenzter lokaler [[Ressource|Ressourcen]] und erlaubt bedarfsgerechte Skalierung. [[Cluster_Computing]] ergänzt dies durch kostengünstige Hochleistungsrechnungen, indem mehrere Standard-[[Maschine|Maschinen]] parallel genutzt werden, was besonders für rechenintensive [[Anwendung|Anwendungen]] wie Simulationen oder [[Datenanalyse|Datenanalysen]] vorteilhaft ist.
- **Abgrenzung & Grenzen:** [[Cloud Computing]] führt zu Abhängigkeit vom Anbieter und potenziellen [[Datenschutz|Datenschutzproblemen]], da die Kontrolle über die [[Infrastruktur]] im Vergleich zu [[On-Premise-Lösung|On-Premise-Lösungen]] eingeschränkt ist. [[Cluster_Computing]] ist hingegen auf ein [[LAN]] begrenzt und skaliert nicht ohne Weiteres über lokale Netzwerke hinaus. Heterogene Umgebungen erfordern komplexere Verwaltung, wie sie etwa in [[Grid_Computing]] umgesetzt wird.
- **Beispiel / Code:** Ein Beispiel für [[Cloud Computing]] ist [[Amazon Web Services]] (AWS), das virtuelle [[Server]], [[Speicher]] und [[Datenbank|Datenbanken]] als [[Dienstleistung]] anbietet:

```java
// Beispiel: Bereitstellung einer virtuellen Maschine in AWS
AmazonEC2 ec2 = AmazonEC2ClientBuilder.defaultClient();
RunInstancesRequest request = new RunInstancesRequest(
    "ami-0abcdef1234567890", // AMI-ID
    1, // Anzahl der Instanzen
    1  // Anzahl der virtuellen CPUs
);
RunInstancesResult result = ec2.runInstances(request);
```

Im [[Cluster_Computing]] könnte eine parallele Simulation wie folgt umgesetzt werden:

```python
# Beispiel: Parallele Berechnung in einem Cluster mit MPI
from mpi4py import MPI

comm = MPI.COMM_WORLD
rank = comm.Get_rank()
size = comm.Get_size()

# Jeder Knoten im Cluster übernimmt einen Teil der Berechnung
data = [i * rank for i in range(100)]
result = sum(data)

# Ergebnisse werden zusammengeführt
if rank == 0:
    total = result
    for i in range(1, size):
        total += comm.recv(source=i)
    print("Gesamtergebnis:", total)
else:
    comm.send(result, dest=0)
```
