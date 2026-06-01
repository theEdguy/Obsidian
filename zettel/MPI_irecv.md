---
id: 6f70d1f9-d3cb-415a-8717-0e5c5f86f8cc
title: "MPI_irecv"
date: 2026-06-01
tags:
  - verteilte_systeme
  - mpi
  - nachrichtenorientierte_kommunikation
  - parallelisierung
  - asynchrone_operationen
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[MPI_irecv]]

- **Kernkonzept:** MPI_irecv ist eine nicht-blockierende Empfangsoperation im [[Message-Passing Interface|Message-Passing Interface (MPI)]], die es einem [[Prozess|Prozess]] ermöglicht, eine [[Nachricht]] asynchron zu empfangen, ohne auf deren Ankunft warten zu müssen.
- **Nutzen & Zweck:** Dieses Konzept löst das [[Problem]] der [[Effizienz|Effizienzsteigerung]] in [[verteilten Systemen|verteilten Systemen]], indem es [[Prozesse]] von blockierenden [[Operationen]] befreit. Es ermöglicht die Überlappung von [[Kommunikation]] und [[Berechnung]], was die [[Performance]] verbessert.
- **Abgrenzung & Grenzen:** MPI_irecv sollte nicht genutzt werden, wenn eine [[synchronisation|synchronisierte]] [[Kommunikation]] erforderlich ist oder wenn der [[Prozess]] ohne die empfangene [[Nachricht]] nicht fortfahren kann. Im Gegensatz zu MPI_recv blockiert MPI_irecv nicht, erfordert jedoch zusätzliche Mechanismen (z. B. MPI_Test oder MPI_Wait) zur Überprüfung des [[Empfangsstatus|Empfangsstatuses]].
- **Beispiel / Code:** #include <mpi.h>
#include <stdio.h>

int main(int argc, char** argv) {
    MPI_Init(&argc, &argv);
    
    int rank;
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    
    if (rank == 0) {
        int data = 42;
        MPI_Send(&data, 1, MPI_INT, 1, 0, MPI_COMM_WORLD);
    } else if (rank == 1) {
        int received_data;
        MPI_Request request;
        MPI_Irecv(&received_data, 1, MPI_INT, 0, 0, MPI_COMM_WORLD, &request);
        
        // Nicht-blockierende Operation: Prozess kann weiterarbeiten
        printf("Prozess 1 arbeitet weiter, während auf die Nachricht gewartet wird.\n");
        
        // Überprüfen, ob die Nachricht empfangen wurde
        MPI_Wait(&request, MPI_STATUS_IGNORE);
        printf("Prozess 1 hat die Nachricht empfangen: %d\n", received_data);
    }
    
    MPI_Finalize();
    return 0;
}
