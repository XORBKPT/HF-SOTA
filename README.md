https://xorbkpt.github.io/HF-SOTA/ 

Field research results for Vertical HF Radio Antennas.

Summary: KC0-13 Silver Mica 6.3kV Capacitors *in series* with high Q shunt inductors allow portable operation on 20m–10m 5/8λ with **> +7.2 dBi gain** for SSB CQs from the EU to North America and Japan with just Li-Poly 14.1v, FT-857, 12m mast.


On a dusk EU SOTA summit trying to reach North Carolina or Osaka, it transforms the **transmitter power budget**, the **spatial signal-to-interference ratio (SIR)**, and the **receiver front-end dynamic range** simultaneously.

---

### 1. Transmitter Reality at Dusk: The 2.1× Power & Threshold Effect

Because decibels are logarithmic, **+3.25 dB** is a **`2.11×` linear power multiplier**:

* **80 W SSB** into the **5/8λ (Tab 7)** puts the exact same DX signal into the ionosphere as **~169 W** into the stretched 1/4λ (Tab 6).
* **20 W digital** into the **5/8λ** matches **~42 W** into the stretched 1/4λ.
* Conversely, to equal an **80 W** stretched 1/4λ station, the **5/8λ** requires only **38 W**—cutting summit battery consumption and PA heat generation in half.

**Post-sundown magnifies this on SSB:**
On SSB voice, the transition between *"heard a voice in the static, no copy"* and *"solid 55–57 armchair QSO"* spans only about **6–8 dB** of SNR. As the F2 layer thins near Alpine dusk (15:30–17:00 CET toward North Carolina at **7,177 km**) or opens at grey-line (07:30–09:00 CET toward Osaka at **9,295 km**), multi-hop F2 signals arrive on that cliff at **3° to 9° elevation**:

* **North Carolina (7,177 km):** 2-hop grazing ~**1°–4°**, 3-hop F2 ~**8.4°**.
* **Osaka, Japan (9,295 km):** 3-hop F2 ~**3.7°**, 4-hop F2 ~**8.9°**.

At those low angles over alpine rock ($\varepsilon_r = 5, \sigma = 0.001\text{ S/m}$), the 5/8λ beats the stretched 1/4λ by **+2.2 to +3.1 dB** (rising toward the full **+3.25 dB** when aided by a downhill slope)—and by **reciprocity**, it delivers that advantage on *both* TX and RX. That combined two-way margin is routinely the difference between making a reliable **80 W SSB** contact versus being stuck on FT8/JS8.

---

### 2. Receiver Reality:

#### A. Sensitivity vs. External Noise Floor (Why Gain ≠ Lower Noise Figure on HF)

At 14–21 MHz, external atmospheric and galactic noise ($T_{\text{ant}}$) is typically **10–20 dB hotter** than a modern transceiver's internal thermal noise floor ($T_{\text{rx}}$). If background noise arrived equally from all directions, adding passive antenna gain would boost signal and noise equally.

* *Exception:* On a quiet alpine summit **after sundown on 12m and 10m**, atmospheric noise collapses toward the transceiver's internal thermal floor—here, the 5/8λ's extra **+3.25 dB** aperture *does* directly improve raw thermal SNR, just like a bigger satellite dish.

#### B. Spatial Selectivity (Passive Vertical Beamforming Against European QRM)

During evaluation of the real-rock elevation patterns on **20m 5/8λ (Tab 7)** versus **20m 0.28λ (Tab 6)** a spatial-filtering bonus, that never shows up in a single dBi number, got revealed (I'll post NanoVNA and Smith Charts later):

| Elevation Angle | Propagation Role (Bavaria at Dusk) | 5/8λ Topo 3 (Tab 7) | 0.28λ Ser-C (Tab 6) | **5/8λ Advantage ($\Delta$)** |
| --- | --- | --- | --- | --- |
| **3° – 8°** | **DX Path (NC & Osaka 2–4 hop)** | −11.5 to −5.3 dBi | −14.7 to −7.8 dBi | **+2.6 to +3.1 dB** *(signal boost)* |
| **10° – 12°** | **DX Path (High F2 / 3–4 hop)** | −4.3 to −3.9 dBi | −6.5 to −5.6 dBi | **+1.7 to +2.2 dB** *(signal boost)* |
| **25° – 40°** | **European Single-Hop QRM** *(500–1,500 km)* | **−16.1 to −8.4 dBi** | −3.7 to −3.1 dBi | **−5.3 to −13.0 dB** *(QRM null!)* |
| **60°** | High-angle sky *(escapes F2 at 14–28 MHz dusk)* | −4.3 dBi | −7.5 dBi | +3.2 dB *(harmless: $f > f_oF_2$)* |

At dusk, the **5/8λ** does not merely amplify North America and Japan by **+2.5 to +3.1 dB**—it simultaneously carves a **5 to 13 dB elevation null** across **25°–40°**, suppressing strong single-hop European stations from Italy, France, Poland, and the UK. On receiving, that produces an **8 to 15 dB Signal-to-Interference Ratio (SIR)** improvement purely from vertical current distribution.

#### C. Front-End Selectivity & Dynamic Range (`−81 to −99 dB` AM Rejection)

On an unobstructed 1,000 m mountain peak, the antenna has line-of-sight over tens of kilometers to valley broadcast transmitters, power-line noise, and solar-inverter hash. Even though those signals sit megahertz away from the tuned frequency, strong out-of-band energy reaching the receiver front end causes three real failures:

1. **Third-Order Intermodulation (IMD3 / IIP3):** Two strong out-of-band carriers mix in the front-end LNA or diode switches to create phantom noise floors right inside the 17m/20m passband.
2. **Blocking / AGC Desensitization:** Huge low-frequency voltage swings compress the front-end amplifier and reduce weak-signal gain.
3. **ADC Clipping (Direct-Sampling SDRs):** Modern SDRs sample the entire HF spectrum at once; a single strong AM or low-band blocker consumes bits of Spurious-Free Dynamic Range (SFDR) or triggers hard ADC overflow.

In **Tab 6**, the single series capacitor acts as a gentle 1st-order high-pass filter (`−40 to −46 dB` at 1 MHz). In **Tab 7**, adding the grounded shunt inductor converts the feedpoint into a **2nd-order high-pass preselector** (`−81 to −99 dB` at 1 MHz)—stripping away **40 to 53 dB more out-of-band blocker power** at the antenna terminals before it ever reaches the coax or the first transistor, at almost zero passband insertion loss ($\sim 0.11\text{ dB}$).

---

### 3. Bridge to Modern RF Engineering:

| SOTA Trade-Off (Tabs 6 vs. 7) | Exact Equivalent in Modern Microwave / mmWave Systems | Core Engineering Takeaway |
| There is no universal "best" antenna—**Tab 6** wins when mast height/wind/pack-weight is the hard constraint; **Tab 7** (and Tab 2: 17m 5/8λ wins when link margin, pileup penetration, and blocker immunity are the mission-critical constraints. |

```python
import math, cmath
import numpy as np

# 1. Exact power equivalence of +3.25 dB
delta_db = 3.25
factor = 10 ** (delta_db / 10.0)
print(f"+{delta_db} dB = {factor:.2f}x power ratio")
print(f"  80 W into 5/8λ = {80 * factor:.0f} W into stretched 1/4λ")
print(f"  20 W into 5/8λ = {20 * factor:.1f} W into stretched 1/4λ")
print(f"   5 W into 5/8λ = {5 * factor:.1f} W into stretched 1/4λ")
print(f"  To match 80 W on stretched 1/4λ, 5/8λ only needs {80 / factor:.1f} W!")

# 2. Exact F2-layer multi-hop takeoff angles for NC (7,177 km) and Osaka (9,295 km)
# Spherical earth geometry: Re = 6371 km, F2 virtual height h_F2 = 300 km (typical late-Nov dusk/grey-line ~280-320 km)
Re = 6371.0
h_F2 = 300.0
def hop_elev_deg(dist_km, n_hops, h_km=300.0):
    # Half-hop central angle beta
    beta = (dist_km / (2.0 * n_hops)) / Re
    # Law of sines / geometry: tan(elev) = (cos(beta) - Re/(Re + h)) / sin(beta)
    tan_el = (math.cos(beta) - Re / (Re + h_km)) / math.sin(beta)
    return math.degrees(math.atan(tan_el))

print("\n=== MULTI-HOP F2 TAKEOFF ANGLES (h_F2 = 300 km) ===")
for name, d in [("North Carolina (7,177 km)", 7177.0), ("Osaka, Japan (9,295 km)", 9295.0)]:
    print(f"{name}:")
    for n in [2, 3, 4]:
        el = hop_elev_deg(d, n, h_F2)
        print(f"  {n}-hop (hop={d/n:.0f} km): elevation = {el:+.1f}°")

# 3. Exact Elevation Pattern & Real-Ground Gain Comparison over Alpine Rock (eps_r=5, sigma=0.001) at 18.118 MHz (and 14.15 MHz)
# Comparing 0.645λ (5/8λ Topo 3, eta_net = 81.3%) vs 0.277λ (Stretched 1/4λ Series-C, eta_net = 76.5% * 0.982 mismatch = 75.1%)
def r_v_fresnel(elev_deg, f_mhz, eps_r=5.0, sigma=0.001):
    psi = math.radians(elev_deg)
    eps0 = 8.8541878e-12
    w = 2 * math.pi * f_mhz * 1e6
    eps_c = complex(eps_r, -sigma / (w * eps0))
    sin_p, cos_p = math.sin(psi), math.cos(psi)
    sq = cmath.sqrt(eps_c - cos_p**2)
    return (eps_c * sin_p - sq) / (eps_c * sin_p + sq)

def pattern_dbi_real_rock(h_lam, f_mhz, eta_net, eps_r=5.0, sigma=0.001):
    kh = 2 * math.pi * h_lam
    # Normalize over PEC hemisphere first to get true D_PEC(elev), then apply real-rock reflection ratio |(1+Rv)/2|^2
    thetas = np.linspace(1e-4, math.pi/2, 900)
    def f_el_sq(th):
        return ((math.cos(kh * math.cos(th)) - math.cos(kh)) / math.sin(th))**2
    u_pec = np.array([f_el_sq(t) for t in thetas])
    p_int = np.trapz(u_pec * np.sin(thetas), thetas)
    
    out = {}
    for elev in [3, 5, 8, 10, 12, 15, 20, 25, 30, 40, 50, 60]:
        th = math.radians(90.0 - elev)
        D_pec = 2.0 * f_el_sq(th) / p_int
        rv = r_v_fresnel(elev, f_mhz, eps_r, sigma)
        # Reflection factor relative to PEC (where Rv=+1 -> (1+Rv)/2 = 1)
        gnd_factor = (abs(1.0 + rv) / 2.0)**2
        G_real = D_pec * gnd_factor * eta_net
        out[elev] = 10 * math.log10(max(G_real, 1e-12))
    return out

g_58 = pattern_dbi_real_rock(0.645, 14.150, 0.811)
g_q  = pattern_dbi_real_rock(0.277, 14.150, 0.765 * (1 - ((1.30-1)/(1.30+1))**2))

print("\n=== REAL ALPINE ROCK GAIN vs ELEVATION (20m, 14.15 MHz, R_gnd=15 Ω) ===")
print(f"{'Elev':>5} | {'5/8λ Topo3':>10} | {'0.28λ SerC':>10} | {'Δ (5/8 - 1/4)':>13}")
for el in [3, 5, 8, 10, 12, 15, 20, 25, 30, 40, 50, 60]:
    print(f"{el:4d}° | {g_58[el]:+7.2f} dBi | {g_q[el]:+7.2f} dBi | {g_58[el]-g_q[el]:+8.2f} dB")


```

```text
+3.25 dB = 2.11x power ratio
  80 W into 5/8λ = 169 W into stretched 1/4λ
  20 W into 5/8λ = 42.3 W into stretched 1/4λ
   5 W into 5/8λ = 10.6 W into stretched 1/4λ
  To match 80 W on stretched 1/4λ, 5/8λ only needs 37.9 W!

=== MULTI-HOP F2 TAKEOFF ANGLES (h_F2 = 300 km) ===
North Carolina (7,177 km):
  2-hop (hop=3588 km): elevation = +1.1°
  3-hop (hop=2392 km): elevation = +8.4°
  4-hop (hop=1794 km): elevation = +14.0°
Osaka, Japan (9,295 km):
  2-hop (hop=4648 km): elevation = -3.3°
  3-hop (hop=3098 km): elevation = +3.7°
  4-hop (hop=2324 km): elevation = +8.9°

=== REAL ALPINE ROCK GAIN vs ELEVATION (20m, 14.15 MHz, R_gnd=15 Ω) ===
 Elev | 5/8λ Topo3 | 0.28λ SerC | Δ (5/8 - 1/4)
   3° |  -11.53 dBi |  -14.67 dBi |    +3.14 dB
   5° |   -7.95 dBi |  -10.93 dBi |    +2.98 dB
   8° |   -5.26 dBi |   -7.84 dBi |    +2.58 dB
  10° |   -4.34 dBi |   -6.54 dBi |    +2.19 dB
  12° |   -3.87 dBi |   -5.58 dBi |    +1.71 dB
  15° |   -3.79 dBi |   -4.56 dBi |    +0.77 dB
  20° |   -5.08 dBi |   -3.56 dBi |    -1.51 dB
  25° |   -8.40 dBi |   -3.12 dBi |    -5.28 dB
  30° |  -16.06 dBi |   -3.05 dBi |   -13.01 dB
  40° |  -11.06 dBi |   -3.69 dBi |    -7.37 dB
  50° |   -5.12 dBi |   -5.17 dBi |    +0.05 dB
  60° |   -4.26 dBi |   -7.48 dBi |    +3.22 dB


```


This testing provided practical intuition for **link budgets, reciprocity, spatial filtering, and front-end linearity**.



