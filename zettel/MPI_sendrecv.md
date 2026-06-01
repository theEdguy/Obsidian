---
id: 1845eb92-0743-46fc-a5ab-b26c0b85c541
title: "MPI_sendrecv"
date: 2026-06-01
tags:
  - verteilte_systeme
  - mpi
  - verteilte-systeme
  - nachrichtenorientierte-kommunikation
  - parallele-programmierung
  - synchronisation
  - blockierende-operation
  - koordination
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[MPI_sendrecv]]

- **Kernkonzept:** MPI_sendrecv ist eine [[Operation|Operation]] im [[Message-Passing Interface|Message-Passing Interface (MPI)]], die das gleichzeitige Senden und Empfangen von [[Nachricht|Nachrichten]] in einem [[Prozess|Prozess]] ermöglicht, um [[Deadlock|Deadlocks]] zu vermeiden und die [[Effizienz]] der [[Kommunikation]] in [[Verteilte Systeme|verteilten Systemen]] zu erhöhen. Im Gegensatz zu [[MPI_recv|MPI_recv]], das ausschließlich den blockierenden Empfang von [[Nachricht|Nachrichten]] ermöglicht, kombiniert MPI_sendrecv [[Synchronisation]] und [[Pufferung]] für bidirektionale [[Datenübertragung]].
- **Nutzen & Zweck:** Diese [[Operation]] löst das Problem der [[Blockierung]] bei bidirektionaler [[Kommunikation]] in [[parallele Programmierung|parallelen Programmen]], indem sie [[Synchronisation]] und [[Pufferung]] integriert. Sie verhindert [[Warteschleifen]] und [[Deadlock|Deadlocks]], optimiert die [[Datenübertragung]] und ist besonders nützlich für [[Ringkommunikation]] oder [[Nachbarschaftsaustausch]]. Während [[MPI_recv]] lediglich den blockierenden Empfang von [[Nachricht|Nachrichten]] sicherstellt, ermöglicht MPI_sendrecv die effiziente Koordination von [[Prozess|Prozessen]] in [[verteilte Systeme|verteilten Umgebungen]] durch gleichzeitige Sende- und Empfangsoperationen. Dies reduziert die [[Latenz]] und verbessert die [[Skalierbarkeit]] in [[Hochleistungsrechnen|Hochleistungsrechenumgebungen]].
- **Abgrenzung & Grenzen:** MPI_sendrecv sollte nicht genutzt werden, wenn [[asynchrone Kommunikation]] oder [[nicht-blockierende Kommunikation]] erforderlich ist, da es blockierende [[Operation|Operationen]] durchführt. In solchen Fällen sind [[MPI_isend|MPI_isend]] und [[MPI_irecv|MPI_irecv]] besser geeignet, da sie [[Prozess|Prozessen]] ermöglichen, während der [[Datenübertragung]] weiterzuarbeiten. Zudem ist MPI_sendrecv weniger flexibel als separate [[MPI_send|MPI_send]]- und [[MPI_recv|MPI_recv]]-[[Operation|Operationen]] bei komplexen [[Kommunikationsmuster|Kommunikationsmustern]], da es keine individuelle Steuerung der Sende- und Empfangsparameter erlaubt. Für [[persistente Kommunikation]] oder [[Event-gesteuerte Systeme|Event-gesteuerte Systeme]] sind [[Message-Queuing-Systeme]] wie IBM MQ oder [[Publish-Subscribe-Modell|Publish-Subscribe-Modelle]] oft besser geeignet.
- **Beispiel / Code:** ### Beispiel 1: Ringkommunikation mit MPI_sendrecv
```c
#include <mpi.h>
#include <stdio.h>

int main(int argc, char** argv) {
    MPI_Init(&argc, &argv);
    int rank, size;
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    MPI_Comm_size(MPI_COMM_WORLD, &size);
    
    int send_data = rank;
    int recv_data;
    int next_rank = (rank + 1) % size;
    int prev_rank = (rank - 1 + size) % size;
    
    MPI_Sendrecv(&send_data, 1, MPI_INT, next_rank, 0,
                 &recv_data, 1, MPI_INT, prev_rank, 0,
                 MPI_COMM_WORLD, MPI_STATUS_IGNORE);
    
    printf("Prozess %d empfing %d von Prozess %d\n", rank, recv_data, prev_rank);
    MPI_Finalize();
    return 0;
}
```
*Beispiel: Ringkommunikation mit MPI_sendrecv zur Vermeidung von Deadlocks.*

### Beispiel 2: Einfache blockierende Kommunikation mit MPI_recv
```c
#include <mpi.h>
#include <stdio.h>

int main(int argc, char** argv) {
    MPI_Init(&argc, &argv);
    
    int world_rank;
    MPI_Comm_rank(MPI_COMM_WORLD, &world_rank);
    
    if (world_rank == 0) {
        int data = 42;
        MPI_Send(&data, 1, MPI_INT, 1, 0, MPI_COMM_WORLD);
    } else if (world_rank == 1) {
        int received_data;
        MPI_Recv(&received_data, 1, MPI_INT, 0, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
        printf("Prozess 1 erhielt: %d\n", received_data);
    }
    
    MPI_Finalize();
    return 0;
}
```
*Beispiel: Einfache Punkt-zu-Punkt-Kommunikation mit MPI_recv.*
