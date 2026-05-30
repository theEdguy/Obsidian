---
id: 71c291a6-2d64-485b-803f-fcf79ec7627d
title: "Bridge_Pattern"
date: 2026-05-30
tags:
  - software_engineering
  - strukturmuster
  - design_pattern
  - architektur
  - strukturpattern
  - draft
source: "SWE Slides (Folien 361-375)"
---

# [[Bridge_Pattern]]

- **Kernkonzept:** Ein [[Strukturmuster]], das die [[Abstraktion]] von der [[Implementierung]] trennt, um beide unabhängig voneinander erweitern zu können. Das [[Bridge_Pattern|Bridge-Muster]] vermeidet eine feste Bindung zwischen [[Schnittstelle|Schnittstellen]] und konkreten [[Implementierung|Implementierungen]], sodass [[Abstraktion|Abstraktionen]] und [[Implementierung|Implementierungen]] zur Laufzeit kombiniert werden können.
- **Nutzen & Zweck:** Fördert [[Flexibilität]] und [[Wiederverwendbarkeit]], indem es [[Abstraktion|Abstraktionen]] und [[Implementierung|Implementierungen]] entkoppelt. Es löst das Problem der [[Klassenexplosion]] bei der Kombination mehrerer [[Abstraktion|Abstraktionen]] und [[Implementierung|Implementierungen]] und ermöglicht die unabhängige Weiterentwicklung von [[Schnittstelle|Schnittstellen]] und [[Implementierung|Implementierungen]], ohne dass Änderungen an einer Seite die andere beeinflussen. Besonders nützlich in Systemen mit variablen [[Schnittstelle|Schnittstellen]] und [[Implementierung|Implementierungen]], die [[Lose_Kopplung]] erfordern.
- **Abgrenzung & Grenzen:** Erhöht die [[Komplexität]] des [[Designs]] und ist nicht notwendig, wenn [[Abstraktion|Abstraktionen]] und [[Implementierung|Implementierungen]] stabil sind oder sich nicht unabhängig ändern. Unterscheidet sich vom [[Adapter_Pattern]], da es nicht bestehende [[Schnittstelle|Schnittstellen]] anpasst, sondern eine stabile [[Abstraktion]] für variable [[Implementierung|Implementierungen]] schafft. Nicht geeignet, wenn nur eine einzige [[Implementierung]] existiert oder wenn [[Schnittstelle|Schnittstellen]] und [[Implementierung|Implementierungen]] eng gekoppelt bleiben sollen.
- **Beispiel / Code:** ```java
// Beispiel 1: Grafik-Rendering mit [[Bridge_Pattern|Bridge-Muster]]
interface Zeichnung {
    void zeichnen();
}

class VektorZeichnung implements Zeichnung {
    @Override
    public void zeichnen() {
        System.out.println("Vektorzeichnung");
    }
}

abstract class Form {
    protected Zeichnung zeichnung;
    
    Form(Zeichnung zeichnung) {
        this.zeichnung = zeichnung;
    }
    
    abstract void anzeigen();
}

class Kreis extends Form {
    Kreis(Zeichnung zeichnung) {
        super(zeichnung);
    }
    
    @Override
    void anzeigen() {
        zeichnung.zeichnen();
        System.out.println("Kreis");
    }
}

// Beispiel 2: Verschlüsselung mit [[Bridge_Pattern|Bridge-Muster]]
interface Cipher {
    void set_key(byte[] key);
    void encrypt_file(String input, String output);
}

abstract class CipherImpl {
    abstract void set_key(byte[] key);
    abstract void encrypt_block(byte[] data);
}

class AESImpl extends CipherImpl {
    @Override
    void set_key(byte[] key) { /* AES-spezifische Logik */ }
    
    @Override
    void encrypt_block(byte[] data) { /* AES-Verschlüsselung */ }
}

class FileCipher implements Cipher {
    private CipherImpl impl;
    
    FileCipher(CipherImpl impl) {
        this.impl = impl;
    }
    
    @Override
    public void set_key(byte[] key) {
        impl.set_key(key);
    }
    
    @Override
    public void encrypt_file(String input, String output) {
        // Dateiverarbeitung + Aufruf von impl.encrypt_block()
    }
}
```
