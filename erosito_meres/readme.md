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
* **Műveleti erősítő:** Ideális Op-Amp modell (Simulációban) / NI myDAQ (Valós mérésben)

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
Az oszcilloszkóp két csatornát rögzített (Bemenet és Kimenet).

| Paraméter | Channel 0 (Bemenet) | Channel 1 (Kimenet) |
| :--- | :--- | :--- |
| **Beállítás (Scale)** | $200\, \text{mV/Div}$ | $1\, \text{V/Div}$ |
| **Frekvencia** | $99.999\, \text{Hz}$ | $99.988\, \text{Hz}$ |
| **Csúcs-csúcs feszültség ($V_{p-p}$)** | **$1.002\, \text{V}$** | **$9.357\, \text{V}$** |
| **RMS feszültség** | $353.65\, \text{mV}$ | $3.287\, \text{V}$ |

---

## 6. Kiértékelés és hibaszámítás

A mért értékek alapján a tényleges erősítés ($A_{mért}$):

$$A_{mért} = \frac{V_{out(p-p)}}{V_{in(p-p)}} = \frac{9.357\, \text{V}}{1.002\, \text{V}} \approx \mathbf{9.338}$$

**Hiba számítás (eltérés az elméleti értéktől):**

$$\text{Hiba} (\%) = \left| \frac{A_{elméleti} - A_{mért}}{A_{elméleti}} \right| \times 100$$

$$\text{Hiba} (\%) = \left| \frac{9.36 - 9.338}{9.36} \right| \times 100 \approx \mathbf{0.23\%}$$

---

## 7. Összegzés

Az alábbi táblázat összefoglalja az elméleti, szimulált és mért eredményeket:

| Adat | Elméleti számítás | Szimuláció | Mért (Valós) | Hiba (%) |
| :--- | :--- | :--- | :--- | :--- |
| **Erősítés ($A_v$)** | $9.36$ | $9.36$ | $9.338$ | $0.23\%$ |
| **Kimeneti fesz.** (1V bemenetnél) | $9.36\, \text{V}$ | $9.36\, \text{V}$ | $9.357\, \text{V}$ | - |

**Következtetés:**
A mérés során sikeresen összeállítottuk és vizsgáltuk a nem-invertáló erősítő kapcsolást. A mért és számított értékek közötti eltérés minimális (**0.23%**), ami a műszerek pontosságából és az ellenállások toleranciájából adódhat. A mérés igazolta az elméleti összefüggést.
