# 📊 Projekt-Status: Zettelkasten & Podcast-System

Dieses Dokument gibt dir eine tagesaktuelle Übersicht darüber, welche Materialien verarbeitet wurden, welche Podcasts und Quizzes gerade generiert werden und wie deine Vorbereitung auf die Software Engineering (SWE) Klausur strukturiert ist.

---

## 🏃 Aktueller Generierungs-Status (Hintergrund-Prozess)

Gerade läuft die **vollständige Generierung aller 5 Kapitel** im Hintergrund. 
- **Aktiver Prozess**: `generate_all_chapters.py`
- **Fortschritt**: Kapitel 1 (`Grundlagen_und_Prozesse`) wird slide-by-slide gerendert und direkt per Mistral TTS vertont.

---

## 📂 Kapitel-Übersicht & Dateipfade

Die Vorlesungsfolien (387 Slides) wurden in **5 thematische Kapitel** unterteilt. Für jedes Kapitel wird ein eigener Ordner unter `obsidian_vault/Zettelkasten/podcasts/` angelegt, der Folgendes enthält:
1. **Podcast-Audio (`.mp3`)**: Fließende Vorlesung im kontinuierlichen Monolog-Stil (keine Listen, kein Code-Rauschen) gesprochen von **Mistral (Voice: Paul)**.
2. **Vorlesungs-Skript (`.txt`)**: Der vorgelesene Text in sauberem Fließtext.
3. **Study-Quiz (`quiz/Quiz_SWE_Slides_*.md`)**: Ein Obsidian-freundliches Multiple-Choice-Quiz mit 10–15 Fragen. Die Antworten sind in ausklappbaren `<details>`-Blöcken versteckt.

### 🗺️ Die 5 Kapitel im Überblick

| Kapitel | Thema | Folien-Bereich | Speicherort | Status |
| :--- | :--- | :--- | :--- | :--- |
| **Kapitel 1** | Grundlagen & Vorgehensmodelle | Slides 1–75 | `podcasts/Chapter_1_Grundlagen_und_Prozesse/` | 🔄 Generiert gerade... |
| **Kapitel 2** | Objektorientierte Konzepte | Slides 76–122 | `podcasts/Chapter_2_Objektorientierte_Konzepte/` | ⏳ Warteschlange |
| **Kapitel 3** | Anforderungen & Use Cases | Slides 123–199 | `podcasts/Chapter_3_Anforderungen_und_Use_Cases/` | ⏳ Warteschlange |
| **Kapitel 4** | Systemarchitektur & Interaktion | Slides 200–325 | `podcasts/Chapter_4_Systemarchitektur_und_Interaktion/` | ⏳ Warteschlange |
| **Kapitel 5** | Entwurfsmuster (Design Patterns) | Slides 326–388 | `podcasts/Chapter_5_Entwurfsmuster/` | ⏳ Warteschlange |

---

## 📚 Zettelkasten Datenbank-Statistiken

Dein Zettelkasten ist voll funktionsfähig und verbindet Vorlesungsinhalte direkt mit Altklausuren:

*   **Zettel (Konzepte)**: **209 atomare Wissensnotizen** im Ordner `zettel/` (z. B. [[Wasserfallmodell]], [[MVC_Pattern]], [[Architekturzentrierung]]).
*   **Lektürenotizen (Literature Notes)**: **31 Lektürenotizen** im Ordner `literature/`, die jeweils 15 Slides zusammenfassen und direkt mit den zugehörigen Zetteln verlinken.
*   **Übungsaufgaben (Exercises)**: **37 klausurnahe Aufgaben** im Ordner `exercises/`, extrahiert aus den letzten 8 Altklausuren (z. B. `Klausur_SoSe2023_Aufgabe1_Vorgehensmodelle_Wasserfall_vs_Agil`). Jede Aufgabe ist mit den theoretischen Zetteln verlinkt.

---

## 🛠️ Letzte technische Verbesserungen

- **Rate-Limit-Schutz**: Das Generierungsskript wartet bei einer API-Überlastung (HTTP 429) automatisch ab und versucht es nach einem Cooldown erneut, statt abzustürzen.
- **Trenner-Filter**: Symbole wie Trennstriche (`---`) werden vor der TTS-Synthese entfernt, um "Empty Speech Input"-Fehler der Mistral-API zu verhindern.
- **Wissens-Synthese**: Für jede Folie zieht das Generierungsskript automatisch den Kontext aus allen verlinkten Zettel-Dateien heran, um eine fachlich exakte und tiefe Erklärung zu formulieren.

---

## 🎯 So nutzt du die Materialien zum Lernen

1. **Anhören & Mitlesen**: Öffne das Podcast-Audio des jeweiligen Kapitels und lies bei Bedarf im zugehörigen Skript mit. Alle Fachbegriffe sind als Obsidian-Wikilinks [[Link]] klickbar, sodass du direkt auf den passenden Zettel springen kannst.
2. **Selbsttest (Quiz)**: Gehe in den Ordner `quiz/` des Kapitels, öffne die Quiz-Datei im Lesemodus und teste dein Wissen. Klicke auf `🔑 Antwort anzeigen / Show Answer` für die Lösung und eine detaillierte Begründung.
3. **Üben**: Löse die Übungsaufgaben unter `exercises/`. Wenn du Theorie nachschlagen musst, klicke einfach auf die verlinkten Zettel oben in der Aufgabe.
