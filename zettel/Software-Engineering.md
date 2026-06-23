---
id: 5f418c27-8bfb-42eb-a950-1ce3b0929454
title: "Software Engineering"
date: 2026-06-24
tags:
  - software_engineering
  - grundlagen
  - prozessmodelle
  - draft
source: "SWE Slides – Kapitel 1: Die Notwendigkeit eines Prozesses"
---

# [[Software Engineering]]

- **Kernkonzept:** Software Engineering ist eine [[ingenieurwissenschaftliche_Disziplin|ingenieurwissenschaftliche]] [[Disziplin]], die sich mit der systematischen, disziplinierten und quantifizierbaren Entwicklung, Wartung und Verwaltung großer [[Software-System|Software-Systeme]] befasst. Es umfasst [[Methoden]], [[Werkzeuge]], [[Prozessmodelle]], [[Architekturprinzip|Architekturprinzipien]] wie [[Lose_Kopplung|lose Kopplung]] und [[Hohe_Kohäsion|hohe Kohäsion]] sowie strukturierte [[Software-Engineering-Prozess|Software-Engineering-Prozesse]], um [[Anforderung|Anforderungen]] in qualitativ hochwertige [[Softwarelösung|Softwarelösungen]] unter Berücksichtigung technischer, wirtschaftlicher und sozialer Aspekte umzusetzen.
- **Nutzen & Zweck:** Software Engineering existiert, um die [[Komplexität]] moderner [[Software-System|Software-Systeme]] beherrschbar zu machen und die [[Qualität]], [[Zuverlässigkeit]] sowie [[Wartbarkeit]] von [[Software]] zu gewährleisten. Es löst konkrete Probleme wie unklare [[Anforderung|Anforderungen]], unstrukturierte [[Entwicklungsprozess|Entwicklungsprozesse]], hohe [[Fehleranfälligkeit]], mangelnde [[Skalierbarkeit]] und ineffiziente [[Teamarbeit]], indem es strukturierte [[Vorgehensmodell|Vorgehensmodelle]] (z. B. [[Unified_Process|Unified Process]], [[iterative_Entwicklung|iterative Entwicklung]], [[Scrum]], [[Wasserfallmodell]], [[Extreme_Programming]]) und bewährte [[Methoden]] (z. B. [[UML]], [[Entwurfsmuster|Design Patterns]], [[Use-Case-getriebene_Analyse|Use-Case-getriebene Analyse]], [[Refactoring]], [[Bridge_Pattern|Bridge-Muster]]) bereitstellt. Dadurch werden [[Projekt|Projekte]] planbarer, [[Risiko|Risiken]] minimiert, [[Kosten]] kontrolliert, die [[Produktivität]] gesteigert und die Zusammenarbeit in interdisziplinären [[Team|Teams]] verbessert. Zudem ermöglicht es die Umsetzung [[funktionale_Anforderung|funktionaler]] und [[nicht-funktionale_Anforderung|nicht-funktionaler Anforderungen]] wie [[Sicherheit]], [[Performance]], [[Benutzerfreundlichkeit]] und [[Erweiterbarkeit]], indem klare [[Phase|Phasen]], [[Rolle|Rollen]] und [[Artefakt|Artefakte]] definiert werden, die eine nachvollziehbare und reproduzierbare Entwicklung sicherstellen. Durch den Einsatz von [[Architekturprinzip|Architekturprinzipien]] wie [[Schichtenmodell|Schichtenarchitektur]], [[Entwurfsmuster|Mustern]] (z. B. [[MVC]], [[Fassade]], [[Fabrikmethode]], [[Bridge_Pattern|Bridge-Muster]]) oder Prinzipien wie [[Lose_Kopplung|lose Kopplung]] und [[Hohe_Kohäsion|hohe Kohäsion]] wird die [[Modularität]], [[Wartbarkeit]] und [[Anpassungsfähigkeit]] von [[System|Systemen]] erhöht, was langfristig die [[Wartungskosten]] senkt.
- **Abgrenzung & Grenzen:** Software Engineering sollte nicht angewendet werden, wenn es sich um sehr kleine [[Projekt|Projekte]] mit minimaler [[Komplexität]] handelt, bei denen der Overhead durch formale [[Methoden]] oder umfangreiche [[Dokumentation]] den Nutzen übersteigt. Es unterscheidet sich von reiner [[Programmierung]] oder [[Ad-hoc-Entwicklung|Ad-hoc-Entwicklungsansätzen]] (z. B. „[[Code-and-Fix]]“) durch seinen ganzheitlichen Ansatz, der nicht nur die [[Implementierung]], sondern auch [[Analyse]], [[Softwareentwurf|Design]], [[Softwaretest|Testen]] und [[Wartung]] umfasst. Während explorative Ansätze wie [[Prototyping]] in frühen Forschungsphasen sinnvoll sein können, scheitern unstrukturierte Ansätze bei langfristigen oder [[sicherheitskritische_Systeme|sicherheitskritischen Systemen]] an mangelnder [[Struktur]] und [[Nachhaltigkeit]]. Alternativen wie [[No-Code-Plattform|No-Code-Plattformen]], [[Skripting]] oder [[agile_Methoden|agile Methoden]] (z. B. [[Extreme_Programming]], [[Scrum]]) können in einfachen Fällen effizienter sein, bieten jedoch keine ausreichende Kontrolle für komplexe oder skalierbare [[Systeme]]. Zudem eignet sich Software Engineering weniger für [[Projekt|Projekte]] mit extrem dynamischen oder unklaren [[Anforderung|Anforderungen]], die keine stabile Planungsgrundlage bieten, da starre [[Prozessmodelle]] die Flexibilität einschränken können. Im Vergleich zu rein [[agile_Methoden|agilen Methoden]] legt Software Engineering stärkeren Fokus auf [[Planung]] und [[Architektur]], was in hochdynamischen Umgebungen als zu starr empfunden werden kann. Prinzipien wie [[Lose_Kopplung|lose Kopplung]] oder [[Hohe_Kohäsion|hohe Kohäsion]] sind zwar universell anwendbar, erfordern jedoch disziplinierte Umsetzung, die in Ad-hoc-Ansätzen oft vernachlässigt wird. Für [[sicherheitskritische_Systeme|sicherheitskritische Systeme]] (z. B. Luftfahrt, Medizin) sind formale [[Methode|Methoden]] wie [[formale_Verifikation|formale Verifikation]] oft unverzichtbar, die über klassisches Software Engineering hinausgehen. Software Engineering ist kein Ersatz für [[Kreativität]] oder [[Domain_Wissen]], sondern ein Rahmenwerk zur Systematisierung und [[Qualitätssicherung]].
- **Beispiel / Code:** ```java
// Beispiel für Komposition in Java (Teile-Ganzes-Beziehung mit Existenzabhängigkeit)
class Motor {
    private String typ;

    public Motor(String typ) {
        this.typ = typ;
    }

    public void starten() {
        System.out.println("Motor wird gestartet.");
    }
}

class Auto {
    private final Motor motor; // Komposition: Motor existiert nur mit Auto

    public Auto(String motorTyp) {
        this.motor = new Motor(motorTyp); // Motor wird im Konstruktor erzeugt
    }

    public void fahren() {
        motor.starten();
        System.out.println("Auto fährt.");
    }
}

// Beispiel: Use-Case-Realisierung für eine Mitgliederverwaltung (funktionale Anforderung)
public class Mitglied {
    private String name;
    private String adresse;

    public void adresseAendern(String neueAdresse) {
        this.adresse = neueAdresse;
        System.out.println("Adresse erfolgreich geändert: " + neueAdresse);
    }
}

// Beispiel für einen Use Case als strukturierte Beschreibung (Vorlage für Implementierung)
public class MitgliedVerwaltenUseCase {
    // Akteure
    private Vereinsmanager manager;
    private MailClient mailClient;

    // Systemgrenze
    private MyClubSystem myClub;

    // Use-Case-Logik
    public void mitgliedBearbeiten(Mitglied mitglied, Aenderung aenderung) {
        if (aenderung.getTyp() == Aenderungstyp.ABTEILUNG) {
            mailClient.sendeBenachrichtigung(
                mitglied.getAbteilungsleiter(),
                "Abteilungswechsel von Mitglied " + mitglied.getName()
            );
        }
        myClub.aktualisiereMitglied(mitglied);
    }
}

// Beispiel: Nicht-funktionale Anforderung (Sicherheit) mit Metrik
public class SicherheitsManager {
    private Map<String, Integer> fehlversuche = new HashMap<>();

    public boolean authentifizieren(String benutzer, String passwort) {
        // Simulierte Authentifizierung mit Sperrmechanismus nach 3 Fehlversuchen
        if (fehlversuche.getOrDefault(benutzer, 0) >= 3) {
            System.out.println("Account gesperrt!");
            return false;
        }
        // ... Authentifizierungslogik
        return true;
    }
}

// Beispiel für eine klare Schichtenarchitektur nach dem Drei-Schichtenmodell
// (Präsentation, Logik, Persistenz) in einer Java-Anwendung

// Logikschicht: Geschäftslogik in einer dedizierten Klasse
public class MemberService {
    private MemberRepository memberRepository;

    public MemberService(MemberRepository memberRepository) {
        this.memberRepository = memberRepository;
    }

    public void addMember(Mitglied mitglied) {
        if (mitglied.isValid()) {
            memberRepository.save(mitglied);
        } else {
            throw new IllegalArgumentException("Ungültige Mitgliedsdaten");
        }
    }
}

// Persistenzschicht: Datenzugriff über ein Repository
public interface MemberRepository {
    void save(Mitglied mitglied);
    Mitglied findById(String id);
}

// Präsentationsschicht: Controller (z. B. in Spring MVC)
@RestController
@RequestMapping("/members")
public class MemberController {
    private final MemberService memberService;

    public MemberController(MemberService memberService) {
        this.memberService = memberService;
    }

    @PostMapping
    public ResponseEntity<String> createMember(@RequestBody Mitglied mitglied) {
        memberService.addMember(mitglied);
        return ResponseEntity.ok("Mitglied erfolgreich angelegt");
    }
}

// Beispiel für eine Fassade nach dem [[Fassade|Fassade-Muster]] (Facade Pattern)
// Vereinfacht den Zugriff auf komplexe Subsysteme durch eine einheitliche [[Schnittstelle]].
public interface ManagementFactory {
    ManagementFactory FACTORY = new ManagementFacade();
    
    MemberManagement memberManagement();
    // Weitere Methoden...
}

// Implementierung der Fassade
@Component
@ApplicationScope
class ManagementFacade implements MemberManagement {
    @Autowired
    private StateMachine stateMachine;
    
    @Override
    public void addMember(Mitglied mitglied) {
        stateMachine.handleEvent(new AddMemberEvent(mitglied));
    }
    // Weitere Implementierungen...
}

// Beispiel für eine Fabrikmethode im Software Engineering ([[Fabrikmethode|Erzeugungsmuster]])
abstract class AddressBook {
    protected abstract AddressLabel createAddressLabel();
    
    public BusinessCard createBusinessCard() {
        BusinessCard card = new BusinessCard();
        AddressLabel label = createAddressLabel();
        card.addLabel(label);
        return card;
    }
}

class FrenchAddressBook extends AddressBook {
    @Override
    protected AddressLabel createAddressLabel() {
        return new FrenchAddressLabel();
    }
}

// Beispiel für das [[Bridge_Pattern|Bridge-Muster]] (Strukturmuster)
// Entkopplung von Abstraktion und Implementierung
interface CipherImpl {
    void encryptFile(String filePath);
    void decryptFile(String filePath);
}

class AESCipher implements CipherImpl {
    @Override
    public void encryptFile(String filePath) {
        System.out.println("Verschlüsselung von " + filePath + " mit AES");
    }
    
    @Override
    public void decryptFile(String filePath) {
        System.out.println("Entschlüsselung von " + filePath + " mit AES");
    }
}

abstract class Cipher {
    protected CipherImpl implementation;
    
    protected Cipher(CipherImpl impl) {
        this.implementation = impl;
    }
    
    public abstract void encrypt(String filePath);
    public abstract void decrypt(String filePath);
}

class FileCipher extends Cipher {
    public FileCipher(CipherImpl impl) {
        super(impl);
    }
    
    @Override
    public void encrypt(String filePath) {
        implementation.encryptFile(filePath);
    }
    
    @Override
    public void decrypt(String filePath) {
        implementation.decryptFile(filePath);
    }
}

// Nutzung:
public class Main {
    public static void main(String[] args) {
        Cipher cipher = new FileCipher(new AESCipher());
        cipher.encrypt("daten.txt");
    }
}
```
