---
id: 1365eaa1-b52b-441c-beb5-59823b2363a0
title: "Klausur_SoSe2024_Aufgabe4_Scheduler_Algorithmen_und_Binaere_Suche"
date: 2026-05-30
tags:
  - software_engineering
  - sose2024
  - klausur_sose_2024
  - scheduler
  - algorithmen
  - binaere_suche
  - lineare_suche
  - rekursion
  - java
  - exercise
  - draft
source: "SWE-SoSe-2024 - (Loesung).pdf"
---

# [[Klausur_SoSe2024_Aufgabe4_Scheduler_Algorithmen_und_Binaere_Suche]]

- **Aufgabenstellung:** 
  - **a:** Veranschaulichen Sie den aktuell implementierten Algorithmus zum Auffinden der richtigen Einfügeposition in der Klasse `ShortestJobFirst`. Vervollständigen Sie dazu das folgende Sequenzdiagramm. Der Algorithmus soll die lineare Suche darstellen, die im Code durch eine Schleife realisiert wird.
  - **b:** Ändern Sie die Implementierung der Klasse `ShortestJobFirst` so ab, dass anstelle der linearen Suche eine effizientere binäre Suche verwendet wird. Orientieren Sie sich dabei am gegebenen Sequenzdiagramm und Code-Snippet. Achten Sie darauf, dass die Methode `addJob` einen booleschen Rückgabewert erhält, der angibt, ob das Hinzufügen erfolgreich war.
- **Lösungsweg / Musterlösung:** 
  - **a:**
  - **beschreibung:**
  Der aktuell implementierte Algorithmus durchläuft die Liste `jobs` linear, um die korrekte Einfügeposition für einen neuen Job zu finden. Dabei wird die `estimatedTime()` des neuen Jobs mit der `estimatedTime()` jedes bestehenden Jobs verglichen. Sobald ein Job mit einer größeren oder gleichen `estimatedTime()` gefunden wird, wird der neue Job an dieser Position eingefügt. Falls kein solcher Job existiert, wird der neue Job am Ende der Liste eingefügt.
  
  **Sequenzdiagramm (textuell beschrieben):**
  1. `ShortestJobFirst` erhält einen neuen Job `newJob`.
  2. Initialisiere `idx = 0`.
  3. Iteriere über die Liste `jobs`:
     - Vergleiche `newJob.estimatedTime()` mit `job.estimatedTime()` für jeden Job `job` in `jobs`.
     - Falls `newJob.estimatedTime() < job.estimatedTime()`, breche die Schleife ab.
     - Erhöhe `idx` bei jedem Durchlauf.
  4. Füge `newJob` an der Position `idx` in die Liste `jobs` ein.
  5. Die Methode `nextJob()` entfernt und gibt den ersten Job der Liste zurück (oder `null`, falls die Liste leer ist).
    - **code:**
  ```java
  public void addJob(Job newJob) {
      int idx = 0;
      for (Job job : this.jobs) {
          if (newJob.estimatedTime() < job.estimatedTime()) break;
          idx++;
      }
      this.jobs.add(idx, newJob);
  }
  ```
  - **b:**
  - **beschreibung:**
  Die Implementierung wird so geändert, dass eine binäre Suche zur Ermittlung der Einfügeposition verwendet wird. Die Methode `addJob` gibt `false` zurück, wenn die Kapazität der Liste erreicht ist. Die binäre Suche wird in der privaten Hilfsmethode `getPosBS` rekursiv durchgeführt.
  
  **Anpassungen:**
  1. Füge ein Feld `capacity` zur Klasse hinzu, um die maximale Größe der Liste zu speichern.
  2. Passe den Konstruktor an, um `capacity` zu initialisieren.
  3. Implementiere die binäre Suche in `getPosBS`.
  4. Ändere die Signatur von `addJob` zu `public boolean addJob(Job newJob)`.
    - **code:**
  ```java
  public class ShortestJobFirst {
      private List<Job> jobs;
      private final int capacity;
  
      public ShortestJobFirst(int capacity) {
          this.jobs = new ArrayList<>(capacity);
          this.capacity = capacity;
      }
  
      public boolean addJob(Job newJob) {
          if (this.jobs.size() >= this.capacity) {
              return false;
          }
          this.jobs.add(this.getPosBS(newJob, 0, this.jobs.size() - 1), newJob);
          return true;
      }
  
      private int getPosBS(Job newJob, int min, int max) {
          if (min > max) {
              return min;
          }
          int idx = (min + max) / 2;
          Job job = this.jobs.get(idx);
          return (newJob.estimatedTime() < job.estimatedTime())
              ? this.getPosBS(newJob, min, idx - 1)
              : this.getPosBS(newJob, idx + 1, max);
      }
  
      public Job nextJob() {
          return (this.jobs.isEmpty()) ? null : this.jobs.remove(0);
      }
  }
  ```
- **Theoretischer Bezug:** 
  - Die Aufgabe bezieht sich auf [[Algorithmus|Algorithmen]] zur Suche, insbesondere [[Lineare_Suche]] und [[Binaere_Suche]].
  - Die Implementierung der [[Schnittstelle|Schnittstellen]] und die Verwendung von [[Liste|Listen]] sind zentrale Konzepte der [[Objektorientierte_Programmierung|objektorientierten Programmierung]].
  - Die binäre Suche setzt voraus, dass die Liste sortiert ist, was hier durch das Einfügen an der korrekten Position gewährleistet wird (vgl. [[Sortieralgorithmus|Sortieralgorithmen]]).
  - Die Rekursion in der binären Suche ist ein Beispiel für [[Rekursion|rekursive Programmierung]].
- **Stolpersteine / Fehlerquellen:** 
  - Die lineare Suche in Teilaufgabe a) ist ineffizient (O(n)), während die binäre Suche (O(log n)) eine sortierte Liste voraussetzt. Ein häufiger Fehler ist, die Liste nicht sortiert zu halten oder die binäre Suche auf einer unsortierten Liste anzuwenden.
  - Bei der binären Suche muss darauf geachtet werden, dass die Indizes `min` und `max` korrekt aktualisiert werden, um Endlosrekursion zu vermeiden.
  - Die Methode `addJob` in Teilaufgabe b) gibt einen booleschen Wert zurück, was leicht übersehen werden kann. Ein häufiger Fehler ist, die Rückgabe von `false` bei voller Liste zu vergessen.
  - Die Rekursion in `getPosBS` kann bei sehr großen Listen zu einem [[Stack_Overflow|Stack-Overflow]] führen, falls die Rekursionstiefe zu groß wird. Eine iterative Lösung wäre hier robuster.
  - Die Kapazitätsprüfung in `addJob` erfordert ein zusätzliches Feld `capacity`, das im ursprünglichen Code nicht vorhanden ist. Dies muss im Konstruktor initialisiert werden.
