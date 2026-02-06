# Aktív Sávszűrő Áramkör Dokumentáció és Mérési Jegyzőkönyv

Ez a dokumentum a sávszűrő áramkör felépítését, paramétereit, valamint az **NI myDAQ** adatgyűjtő eszközzel végzett frekvenciaválasz-mérések eredményeit tartalmazza.

## 1. Áramköri Leírás

Az áramkör egy műveleti erősítőre épülő **aktív sávszűrő** (Active Band-Pass Filter). A kapcsolás topológiája a többszörös visszacsatolású (MFB - Multiple Feedback) struktúrát követi, amely alkalmas a kívánt frekvenciasáv kiemelésére.

* **Erősítő típusa:** LM324 (Négyes műveleti erősítő - Quad Op-Amp)
* **Funkció:** Sávszűrő (Band-Pass), amely a központi frekvencia környezetében erősít, alatta és felette vág.

## 2. Alkatrészlista (BOM)

| Megnevezés | Érték / Típus | Mennyiség | Funkció a körben |
| :--- | :--- | :--- | :--- |
| **Integrált Áramkör** | **LM324** | 1 db | Aktív erősítő elem (Op-Amp) |
| **Ellenállás** | $220\,\Omega$ | 2 db | Bemeneti illesztés és osztó |
| **Ellenállás** | $12.2\,\text{k}\Omega$ | 1 db | Visszacsatoló ellenállás (Gain beállítás) |
| **Kondenzátor** | $100\,\text{nF}$ | 2 db | Frekvenciafüggő elemek (Vágási frekvenciák) |
| **Mérőeszköz** | **NI myDAQ** | 1 db | Jelgenerálás és mérés |
<img width="1088" height="645" alt="Képernyőkép 2026-02-05 102413" src="https://github.com/user-attachments/assets/69bbbc23-7339-4f78-b6d3-0b80b440c24c" />


## 3. Mérési Környezet (NI myDAQ)

A frekvenciamenet vizsgálata az **NI ELVISmx Bode Analyzer** szoftvermodul és az **NI myDAQ** hardver segítségével történt.

### Beállítások:
* **Eszköz (Device):** `myDAQ1 (NI myDAQ)`
* **Mérési tartomány:** $100.00\,\text{Hz}$ – $15.00\,\text{k}\text{Hz}$
* **Felbontás:** 40 lépés / dekád
* **Bemeneti jel (Peak):** $0.10\,\text{V}$

### Bekötés (Connections):
A szoftver visszajelzése alapján a myDAQ csatlakoztatása:
* **AO 0 (Analog Output 0):** Stimulus Channel – A szűrő bemenetére adott vizsgálójel.
* **AI 0 (Analog Input 0):** Referencia csatorna – A bemeneti jel visszaellenőrzése.
* **AI 1 (Analog Input 1):** Response Channel – A szűrő kimenetén mért jel.

## 4. Mérési Eredmények (Kurzor adatok alapján)

A Bode-diagramon a karakterisztika három jellegzetes pontja került rögzítésre: a rezonanciacsúcs, valamint a karakterisztika alsó és felső lefutó szakasza.

### A. Rezonanciapont (Központi frekvencia)
A szűrő itt éri el a maximális átvitelt.
* **Frekvencia ($f_0$):** **$1412.54\,\text{Hz}$**
* **Erősítés (Gain):** **$26.52\,\text{dB}$** (kb. 21.1-szeres feszültségerősítés)
* **Fázis:** $164.55^\circ$

### B. Alsó mérési pont (Low Frequency)
A felfutó ág ellenőrző pontja.
* **Frekvencia:** $354.81\,\text{Hz}$
* **Erősítés (Gain):** $3.04\,\text{dB}$
* **Fázis:** $-93.66^\circ$
* *Megjegyzés:* A jel itt már jelentősen csillapított a csúcshoz képest.

### C. Felső mérési pont (High Frequency)
A lefutó ág ellenőrző pontja.
* **Frekvencia:** $5308.84\,\text{Hz}$
* **Erősítés (Gain):** $3.09\,\text{dB}$
* **Fázis:** $87.91^\circ$

## 5. Eredmények értékelése és eredmények és kép a működéséröl

1.  **Amplitúdó-menet (Gain):**
    * A mért görbe szabályos sávszűrő karakterisztikát mutat, éles csúccsal $1.4\,\text{kHz}$-nél.
    * A $26.5\,\text{dB}$-es csúcserősítés azt mutatja, hogy az áramkör a hasznos sávban nemcsak szűr, hanem jelentősen erősít is.
    * A myDAQ mérése zajmentes, tiszta lefutást mutat mindkét oldalon.

2.  **Fázismenet (Phase):**
    * A fázisgörbe a rezonanciafrekvenciánál jellemző átfordulást (Phase Wrap) mutat, ami a Bode-diagramokon megszokott jelenség, és az áramkör helyes működését igazolja.
3.  **Képek az áramkör teszteléséröl, valamint a 3dB pontról:**
<img width="912" height="722" alt="Képernyőkép 2026-02-05 103119" src="https://github.com/user-attachments/assets/280c7bef-919d-4b43-a93b-ce6da02999da" />
<img width="910" height="726" alt="Képernyőkép 2026-02-05 102736" src="https://github.com/user-attachments/assets/ec509499-3ed5-4028-8926-d50b8810e38a" />
<img width="910" height="721" alt="Képernyőkép 2026-02-05 103135" src="https://github.com/user-attachments/assets/ef150496-7d03-4688-a296-6a7b09ebc35c" />

## 6. Képek az áramkör készítéséről

---
*Dátum: 2025.03.12.*
*Hardver: NI myDAQ | Szoftver: NI ELVISmx*
