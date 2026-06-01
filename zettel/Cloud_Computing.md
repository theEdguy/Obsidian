---
id: 471ddaeb-dce4-4794-a7a8-76fb490b741e
title: "Cloud Computing"
date: 2026-06-01
tags:
  - verteilte_systeme
  - infrastruktur
  - skalierbarkeit
  - dienstleistung
  - hochleistungsrechnen
  - paralleles_rechnen
  - virtualisierung
  - dienstmodelle
  - draft
source: "VS2 Handout Chapter 03 (Prozesse)"
---

# [[Cloud Computing]]

- **Kernkonzept:** [[Cloud_Computing]] bezeichnet die Bereitstellung von [[IT-Ressource|IT-Ressourcen]] wie [[Rechenleistung]], [[Speicherkapazität|Speicherkapazitäten]], [[Datenbank|Datenbanken]] und [[Dienst|Diensten]] über das [[Internet]], wobei die [[Infrastruktur]] durch [[Virtualisierung|Virtualisierung]] von [[Hardware]]-Komponenten flexibel und skalierbar verwaltet wird. Eine spezifische Ausprägung ist [[Cluster_Computing]], bei dem eine Gruppe homogener [[Maschine|Maschinen]], verbunden über ein [[LAN]], gemeinsam als ein System arbeitet, um parallele [[Berechnung|Berechnungen]] durchzuführen.
- **Nutzen & Zweck:** [[Cloud_Computing]] ermöglicht [[Organisation|Organisationen]] die flexible und bedarfsgerechte Nutzung von [[IT-Ressource|IT-Ressourcen]] ohne eigene [[Hardware]], was [[Skalierbarkeit]], [[Kosteneffizienz]] und vereinfachte Wartung von [[Anwendung|Anwendungen]] und [[Dienst|Diensten]] bietet. Es löst das Problem begrenzter lokaler [[Ressource|Ressourcen]] und erlaubt dynamische Anpassung an wechselnde Anforderungen. [[Cluster_Computing]] ergänzt dies durch kostengünstige [[Hochleistungsrechnen|Hochleistungsrechnungen]], indem mehrere Standard-[[Maschine|Maschinen]] parallel genutzt werden, was besonders für rechenintensive [[Anwendung|Anwendungen]] wie [[Simulation|Simulationen]] oder [[Datenanalyse|Datenanalysen]] vorteilhaft ist. Zudem unterstützt es [[Paralleles_Rechnen|parallele Berechnungen]] und reduziert die Abhängigkeit von teurer Spezial-[[Hardware]].
- **Abgrenzung & Grenzen:** [[Cloud_Computing]] führt zu Abhängigkeit von [[Anbieter|Anbietern]] (Vendor Lock-in) und potenziellen [[Datenschutz|Datenschutzproblemen]], da die Kontrolle über die [[Infrastruktur]] im Vergleich zu [[On-Premise-Lösung|On-Premise-Lösungen]] eingeschränkt ist. Es eignet sich nicht für [[Anwendung|Anwendungen]] mit hohen [[Echtzeitanforderung|Echtzeitanforderungen]] oder strengen [[Datenschutz|Datenschutzvorgaben]], da [[Latenzzeit|Latenzzeiten]] und [[Datenhoheit]] kritisch sein können. Alternativen wie [[Edge_Computing]] oder lokale [[Server]] bieten hier Vorteile. [[Cluster_Computing]] ist hingegen auf ein [[LAN]] begrenzt und skaliert nicht ohne Weiteres über lokale [[Netzwerk|Netzwerke]] hinaus. Heterogene Umgebungen erfordern komplexere Verwaltung, wie sie etwa in [[Grid_Computing]] umgesetzt wird.
- **Beispiel / Code:** Ein Beispiel für [[Cloud_Computing]] ist die Bereitstellung von [[Infrastructure-as-a-Service|Infrastructure-as-a-Service (IaaS)]] bei [[Amazon Web Services]] (AWS), das virtuelle [[Server]], [[Speicher]] und [[Datenbank|Datenbanken]] als [[Dienstleistung]] anbietet. Die [[Virtualisierung|Virtualisierung]] ermöglicht die Isolation von [[Ressource|Ressourcen]] auf gemeinsamer [[Hardware]]:

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

Alternativ kann eine virtuelle Maschine über die AWS CLI erstellt werden:

```bash
# AWS CLI-Befehl zur Erstellung einer EC2-Instanz (VM)
aws ec2 run-instances --image-id ami-0abcdef1234567890 --instance-type t2.micro --key-name MyKeyPair
```

Im [[Cluster_Computing]] könnte eine parallele [[Simulation]] wie folgt umgesetzt werden:

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
