---
id: 1579a09f-c1d7-415f-9231-459380f66399
title: "MPI_bsend"
date: 2026-06-01
tags:
  - verteilte_systeme
  - mpi
  - nachrichtenorientierte_kommunikation
  - asynchron
  - pufferung
  - parallele-programmierung
  - synchronisation
  - parallelisierung
  - nicht_blockierend
  - draft
source: "VS2 Handout Chapter 04 (Kommunikation)"
---

# [[MPI_bsend]]

- **Kernkonzept:** MPI_bsend ist eine [[nicht-blockierende_Operation|nicht-blockierende]] [[Sendefunktion]] im [[Message-Passing_Interface|Message-Passing Interface (MPI)]], die eine ausgehende [[Nachricht]] an einen lokalen [[Puffer]] anhängt und sofort zurückkehrt, ohne auf den Abschluss der [[Nachrichtenübertragung|Übertragung]] zu warten. MPI_issend erweitert dieses Konzept als [[nicht-blockierende_Operation|nicht-blockierende]] [[Sendefunktion]], die jedoch erst zurückkehrt, wenn der [[Empfänger|Empfangsprozess]] mit der Verarbeitung der [[Nachricht]] beginnt, und bietet somit eine [[Synchronisation|teilweise Synchronisation]] ohne vollständige [[Blockierung]].
- **Nutzen & Zweck:** MPI_bsend ermöglicht [[asynchrone_Kommunikation]] in [[verteilte_Systeme|verteilten Systemen]], indem es [[Prozess|Prozesse]] entkoppelt und [[Blockierung|Blockierungen]] bei [[Nachrichtenübertragung|Nachrichtenübertragungen]] vermeidet. Dies steigert die [[Effizienz]] durch [[überlappende_Kommunikation_und_Berechnung|überlappende Kommunikation und Berechnung]], insbesondere um [[Latenz]] zu verbergen. MPI_issend bietet einen Mittelweg zwischen [[nicht-blockierende_Operation|nicht-blockierenden]] und [[blockierende_Operation|blockierenden]] [[Sendefunktion|Sendefunktionen]], indem es [[Synchronisation]] mit dem Beginn des [[Empfang|Empfangsprozesses]] sicherstellt, ohne auf den vollständigen Abschluss der [[Übertragung]] zu warten. Dies verbessert die [[Parallelisierung]] und reduziert [[Synchronisationsblockaden]], die bei rein [[blockierende_Operation|blockierenden]] Operationen wie [[MPI_ssend]] auftreten können. Beide Funktionen adressieren unterschiedliche Anforderungen an [[Ressourcennutzung]] und [[Konsistenz]] in [[parallele_Programmierung|parallelen Programmen]].
- **Abgrenzung & Grenzen:** MPI_bsend sollte nicht genutzt werden, wenn eine garantierte [[Zustellung]] oder [[Synchronisation]] erforderlich ist, da es keine Bestätigung über den [[Empfang]] der [[Nachricht]] gibt. Im Vergleich zu [[MPI_send]] (blockierend) oder [[MPI_ssend]] (synchron) bietet es weniger Kontrolle über den [[Übertragungsstatus]]. MPI_issend hingegen bestätigt nur den Beginn des [[Empfang|Empfangs]], nicht aber dessen Abschluss, und ist somit weniger streng als [[MPI_ssend]], aber strenger als [[MPI_isend]]. MPI_ssend kann zu [[Deadlock|Deadlocks]] führen, wenn der [[Empfänger]] nicht rechtzeitig antwortet, während MPI_issend dieses Risiko reduziert, ohne die [[Komplexität]] von [[Request-Objekt|Request-Objekten]] wie bei MPI_isend einzuführen. MPI_bsend erfordert zudem die explizite Reservierung eines [[Puffers]] mit `MPI_Buffer_attach`, während MPI_issend keine [[Pufferung]] im [[Sender]] vornimmt. Für einfache [[Anwendung|Anwendungen]] mit geringer [[Parallelität]] kann der [[Overhead]] der [[nicht-blockierende_Operation|nicht-blockierenden Operationen]] unnötig sein, da sie zusätzliche [[Komplexität]] durch [[Pufferverwaltung]] oder [[Request-Objekt|Request-Objekte]] einführen.
- **Beispiel / Code:** ```c
#include <mpi.h>
#include <stdio.h>

int main(int argc, char** argv) {
    MPI_Init(&argc, &argv);
    
    int rank;
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    
    if (rank == 0) {
        // Beispiel für MPI_bsend (nicht-blockierend, gepuffert)
        int buffer[100];
        int buffer_size = 100 * sizeof(int);
        MPI_Buffer_attach(buffer, buffer_size);
        
        int message = 42;
        MPI_Bsend(&message, 1, MPI_INT, 1, 0, MPI_COMM_WORLD);
        printf("Prozess 0 hat Nachricht mit MPI_bsend gesendet.\n");
        
        // Puffer freigeben
        MPI_Buffer_detach(&buffer, &buffer_size);
        
        // Beispiel für MPI_isend (nicht-blockierend mit Request-Objekt)
        int data = 84;
        MPI_Request request_isend;
        MPI_Isend(&data, 1, MPI_INT, 1, 1, MPI_COMM_WORLD, &request_isend);
        
        printf("Prozess 0: Nachricht mit MPI_isend gesendet, führe weitere Berechnungen aus...\n");
        
        // Warte auf Abschluss der Übertragung
        MPI_Wait(&request_isend, MPI_STATUS_IGNORE);
        printf("Prozess 0: MPI_isend-Übertragung abgeschlossen.\n");
        
        // Beispiel für MPI_issend (nicht-blockierend mit Empfangsbestätigung)
        int issend_data = 126;
        MPI_Request request_issend;
        MPI_Issend(&issend_data, 1, MPI_INT, 1, 2, MPI_COMM_WORLD, &request_issend);
        
        printf("Prozess 0: Nachricht mit MPI_issend gesendet, warte auf Empfangsbestätigung...\n");
        
        // Warte auf Bestätigung des Empfangsbeginns
        MPI_Wait(&request_issend, MPI_STATUS_IGNORE);
        printf("Prozess 0: MPI_issend-Empfangsbestätigung erhalten.\n");
        
        // Beispiel für MPI_ssend (synchron, blockierend)
        int ssend_data = 252;
        MPI_Ssend(&ssend_data, 1, MPI_INT, 1, 3, MPI_COMM_WORLD);
        printf("Prozess 0 hat Daten synchron mit MPI_ssend gesendet.\n");
    } else if (rank == 1) {
        // Empfang der MPI_bsend-Nachricht
        int received_message;
        MPI_Recv(&received_message, 1, MPI_INT, 0, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
        printf("Prozess 1 hat Nachricht von MPI_bsend empfangen: %d\n", received_message);
        
        // Empfang der MPI_isend-Nachricht
        int received_data;
        MPI_Recv(&received_data, 1, MPI_INT, 0, 1, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
        printf("Prozess 1 hat Nachricht von MPI_isend empfangen: %d\n", received_data);
        
        // Empfang der MPI_issend-Nachricht
        int received_issend_data;
        MPI_Recv(&received_issend_data, 1, MPI_INT, 0, 2, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
        printf("Prozess 1 hat Nachricht von MPI_issend empfangen: %d\n", received_issend_data);
        
        // Empfang der MPI_ssend-Nachricht
        int received_ssend_data;
        MPI_Recv(&received_ssend_data, 1, MPI_INT, 0, 3, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
        printf("Prozess 1 hat Daten von MPI_ssend empfangen: %d\n", received_ssend_data);
    }
    
    MPI_Finalize();
    return 0;
}
```

**Hinweis:** MPI_bsend erfordert die explizite Reservierung eines [[Puffers]] mit `MPI_Buffer_attach`, während MPI_issend ein [[Request-Objekt]] zurückgibt, das für spätere [[Synchronisation]] (z. B. mit `MPI_Wait`) genutzt wird. MPI_ssend blockiert vollständig, bis der [[Empfänger]] die [[Nachricht]] erhalten hat, und MPI_isend ermöglicht [[nicht-blockierende_Operation|nicht-blockierende]] [[Übertragung]] ohne Bestätigung.
