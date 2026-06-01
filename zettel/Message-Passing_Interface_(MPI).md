---
id: cd322344-792c-4081-9d88-9f6bc854dee6
title: "Message-Passing Interface (MPI)"
date: 2026-06-01
tags:
  - verteilte_systeme
  - verteilte-systeme
  - parallelisierung
  - nachrichtenorientierte-kommunikation
  - mpi
  - hochleistungsrechnen
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[Message-Passing Interface (MPI)]]

- **Kernkonzept:** Das Message-Passing Interface (MPI) ist ein standardisiertes Protokoll für die nachrichtenorientierte [[Kommunikation|Kommunikation]] in [[Verteilte Systeme|verteilten Systemen]], das flexible und effiziente [[Datenübertragung|Datenübertragungen]] zwischen Prozessen ermöglicht. Es bietet verschiedene [[Operation|Operationen]] für synchrone und asynchrone [[Nachrichten|Nachrichten]]-Übermittlung.
- **Nutzen & Zweck:** MPI löst das [[Problem]] der [[Prozesskommunikation|Prozesskommunikation]] in [[Parallelrechner|Parallelrechnern]] und [[Cluster|Clustern]], indem es eine einheitliche Schnittstelle für die [[Datenübertragung|Datenübertragung]] bereitstellt. Es ermöglicht die Skalierung von Anwendungen auf mehrere [[Knoten|Knoten]] und verbessert die [[Leistung]] durch direkte [[Nachrichten|Nachrichten]]-Weitergabe ohne zentrale [[Vermittlung|Vermittlungsinstanz]].
- **Abgrenzung & Grenzen:** MPI eignet sich nicht für [[Anwendungsfälle|Anwendungsfälle]], die persistente [[Nachrichtenwarteschlangen|Nachrichtenwarteschlangen]] oder asynchrone [[Middleware]]-Lösungen erfordern, wie z. B. [[Message-Oriented Middleware (MOM)]]. Im Gegensatz zu MOM bietet MPI keine [[Pufferung|Pufferung]] oder [[Fehlerbehandlung|Fehlerbehandlungsmechanismen]] auf [[Systemebene]]. Für einfache [[Client-Server-Architekturen]] oder [[RPC]]-basierte Systeme ist MPI oft überdimensioniert.
- **Beispiel / Code:** // Beispiel: Einfache MPI-Kommunikation zwischen zwei Prozessen
#include <mpi.h>
#include <stdio.h>

int main(int argc, char** argv) {
    MPI_Init(&argc, &argv);
    
    int rank, size;
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    MPI_Comm_size(MPI_COMM_WORLD, &size);
    
    if (rank == 0) {
        int message = 42;
        MPI_Send(&message, 1, MPI_INT, 1, 0, MPI_COMM_WORLD);
        printf("Prozess %d hat Nachricht gesendet.\n", rank);
    } else if (rank == 1) {
        int received;
        MPI_Recv(&received, 1, MPI_INT, 0, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
        printf("Prozess %d hat Nachricht empfangen: %d\n", rank, received);
    }
    
    MPI_Finalize();
    return 0;
}
