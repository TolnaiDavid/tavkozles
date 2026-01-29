# MÉRÉSI JEGYZŐKÖNYV

**Név:** Tolnai Dávid
**Helyszín:** Kandó Kálmán Informatikai Technikum, V3 labor
**Dátum:** 2026. 01. 28.
**Téma:** Műveleti erősítő vizsgálata (Nem-invertáló alapkapcsolás)
**Eszközök:** NI ELVISmx (Function Generator, Oscilloscope), Áramkörszimulátor

---

## 1. A mérés célja
Egy nem-invertáló műveleti erősítő kapcsolás vizsgálata, az elméleti erősítés kiszámítása, majd összevetése a szimulációs és a valós (NI ELVISmx) mérési eredményekkel.

## 2. Kapcsolási rajz és komponensek
A mérés tárgya egy **nem-invertáló erősítő** (Non-Inverting Amplifier).

**Felhasznált alkatrészek:**
* **R1 (Föld felé):** $12.2\, \text{k}\Omega$
* **R2 (Visszacsatoló ág - Feedback):** $102\, \text{k}\Omega$
* **R_in (Bemeneti lezárás):** $104\, \text{k}\Omega$
* **Műveleti erősítő:** Ideális Op-Amp modell

## 3. Elméleti számítások
A nem-invertáló erősítő feszültségerősítését ($A_v$) az alábbi képlet határozza meg:

$$A_v = 1 + \frac{R_2}{R_1}$$

**Behelyettesítve az értékeket:**

$$A_v = 1 + \frac{102\, \text{k}\Omega}{12.2\, \text{k}\Omega}$$
$$A_v = 1 + 8.3606$$
$$A_{elméleti} \approx \mathbf{9.36}$$

Ez azt jelenti, hogy a kimeneti jel amplitúdója elméletileg 9.36-szorosa lesz a bemeneti jelnek.

---

## 4. Szimulációs eredmények
A kapcsolási rajzon látható szimulátor egyenáramú (DC) analízise alapján:
* **Kimeneti feszültség:** $9.36\, \text{V}$

Ez pontosan megegyezik az elméleti számítással, feltételezve, hogy a bemeneti feszültség $1\, \text{V}$ volt a szimuláció pillanatában.

---

## 5. Műszeres mérés (NI ELVISmx)

### 5.1. Bemeneti jel beállítása (Function Generator)
A függvénygenerátor beállításai a következők voltak:
* **Jelalak:** Szinusz
* **Frekvencia:** $100.0000\, \text{Hz}$
* **Amplitúdó (Vpp):** $1.00\, \text{V}$
* **DC Offset:** $0.00\, \text{V}$

### 5.2. Oszcilloszkóp mérések
Az oszcilloszkóp két csatornát rögzített:
* **Channel 0 (Sárga):** Bemeneti jel (Input)
* **Channel 1 (Kék):** Kimeneti jel (Output)

| Paraméter | Channel 0 (Bemenet) | Channel 1 (Kimenet) |
| :--- | :--- | :--- |
| **Beállítás (Scale)** | $200\, \text{mV/Div}$ | $1\, \text{V/Div}$ |
| **Frekvencia** | $99.999\, \text{Hz}$ | $9
