---
id: 2db2f4ed-ef37-52b6-bc35-7f1c79568905
title: "Thread-Kontext vs. Prozess-Kontext"
date: 2026-06-20
tags:
  - software_engineering
  - kapitel_3
  - draft
source: "Kapitel 3: Prozesse"
---

# [[Thread-Kontext vs. Prozess-Kontext]]

- **Kernkonzept:** Der Thread-Kontext enthält die minimalen Register- und Speicherwerte für eine Ausführungseinheit (Stack Pointer, Programmzähler, Zustand) innerhalb desselben Adressraums. Der Prozess-Kontext umfasst zusätzlich den gesamten Adressraum und die MMU-Register. Thread-Kontextwechsel sind wesentlich günstiger, da kein Adressraumwechsel stattfindet.
- **Nutzen & Zweck:** Der Thread-Kontext enthält die minimalen Register- und Speicherwerte für eine Ausführungseinheit (Stack Pointer, Programmzähler, Zustand) innerhalb desselben Adressraums. Der Prozess-Kontext umfasst zusätzlich den gesamten Adressraum und die MMU-Register. Thread-Kontextwechsel sind wesentlich günstiger, da kein Adressraumwechsel stattfindet.
- **Abgrenzung & Grenzen:** Siehe Definition.
- **Beispiel / Code:** Kein Codebeispiel vorhanden.
