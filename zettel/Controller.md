---
id: 44c79eb3-e66f-4cb8-9892-866c5095641f
title: "Controller"
date: 2026-06-24
tags:
  - software_engineering
  - komponente
  - mvc
  - architekturmuster
  - draft
source: "software_engineering_kapitel_15"
---

# [[Controller]]

- **Kernkonzept:** Der [[Controller]] ist eine zentrale [[Komponente]] im [[Model-View-Controller|MVC]]-[[Entwurfsmuster]], die als Vermittler zwischen der [[Präsentationsschicht]] ([[View]]) und der [[Logikschicht]] ([[Model]]) fungiert. Er verarbeitet [[Benutzereingabe|Benutzereingaben]], steuert den [[Anwendungsfluss]] und leitet [[Anfrage|Anfragen]] an das [[Modell]] weiter, ohne domänenspezifische [[Logik]] oder [[Datenhaltung]] zu enthalten.
- **Nutzen & Zweck:** Der [[Controller]] existiert, um die [[Trennung_von_Belangen|Trennung von Darstellung und Geschäftslogik]] zu gewährleisten und das Problem der engen [[Kopplung]] zwischen [[Benutzeroberfläche]] und [[Datenverarbeitung]] zu lösen. Durch diese [[Entkopplung]] verbessert er die [[Wartbarkeit]], [[Testbarkeit]] und [[Erweiterbarkeit]] der [[Software]], da Änderungen an der [[Oberfläche]] oder [[Logik]] unabhängig voneinander vorgenommen werden können. Zudem ermöglicht er die zentrale Steuerung des [[Anwendungsflusses]], die Koordination zwischen verschiedenen [[View|Views]] und [[Model|Models]] sowie die Wiederverwendung von [[Komponente|Komponenten]]. Der [[Controller]] eignet sich besonders für Anwendungen mit komplexen [[Interaktion|Interaktionen]], bei denen eine klare Trennung zwischen [[Präsentation]] und [[Logik]] erforderlich ist.
- **Abgrenzung & Grenzen:** Ein [[Controller]] sollte nicht genutzt werden, wenn die Anwendung sehr einfach ist und keine komplexe Steuerungslogik benötigt, da der Overhead des [[Model-View-Controller|MVC]]-[[Entwurfsmuster|Musters]] dann unnötig ist. Alternativ kann bei datenintensiven Anwendungen mit geringer [[Benutzerinteraktion]] ein datenzentriertes [[Entwurfsmuster]] wie [[Model-View-ViewModel|MVVM]] besser geeignet sein, da es mehr Verantwortung in die [[Präsentationsschicht]] verlagert. Im Gegensatz zum [[Model]], das die [[Geschäftslogik]] und [[Datenhaltung]] übernimmt, oder zur [[View]], die ausschließlich für die [[Darstellung]] zuständig ist, beschränkt sich der [[Controller]] auf die Steuerung und sollte keine domänenspezifische [[Logik]] oder [[Daten]] verwalten. Zudem ist das [[Model-View-Controller|MVC]]-[[Muster]] weniger geeignet für [[Systeme]] mit hoher [[Parallelität]] oder [[Echtzeitanforderung|Echtzeitanforderungen]], da der [[Controller]] sequenzielle [[Ablauf|Abläufe]] steuert und nicht für asynchrone oder [[Event-gesteuertes_System|Event-gesteuerte]] Szenarien optimiert ist.
- **Beispiel / Code:** ```java
// Beispiel 1: Controller in einer Web-Anwendung (Spring Boot)
@RestController
@RequestMapping("/members")
public class MemberController {
    @Autowired
    private MemberService memberService; // Verweis auf das [[Model]]

    @GetMapping("/{id}")
    public ResponseEntity<Member> getMember(@PathVariable Long id) {
        Member member = memberService.findById(id); // Delegation an das [[Model]]
        return ResponseEntity.ok(member);
    }

    @PostMapping
    public ResponseEntity<Member> createMember(@RequestBody Member member) {
        Member savedMember = memberService.save(member); // Steuerung des [[Ablaufs]]
        return ResponseEntity.status(HttpStatus.CREATED).body(savedMember);
    }
}

// Beispiel 2: Controller in einer Desktop-Anwendung (klassisches MVC)
public class MemberController {
    private MemberModel model;
    private MemberView view;

    public MemberController(MemberModel model, MemberView view) {
        this.model = model;
        this.view = view;
    }

    public void addMember(String name, String email) {
        model.addMember(name, email); // Aktualisierung des [[Modells]]
        view.updateMemberList(model.getMembers()); // Aktualisierung der [[View]]
    }

    public void removeMember(String email) {
        model.removeMember(email);
        view.updateMemberList(model.getMembers());
    }
}
```
