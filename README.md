# RTSM Framework — Rupee Trade Settlement Monitor

**Live dashboard → [https://github.com/anisreesuresh/Rupee-Trade-Settlement-Mechanism-Framework]*

---

## What this is

An interactive policy dashboard classifying countries into a **2×2 scenario framework** for rupee trade settlement adoption. Built to support research on India's efforts to internationalise the Indian Rupee (INR) as a bilateral settlement currency.

The framework maps countries along two axes:
- **US trade pressure** — composite E_US index capturing tariff exposure, sanctions, and reciprocal tariff rates (including Trump Liberation Day tariffs through March 2026)
- **Rupee absorbability** — whether India runs a trade surplus with the partner, enabling rupees to circulate back as Indian import payments

---

## The four scenarios

| | High absorbability (India surplus) | Low absorbability (India deficit) |
|---|---|---|
| **High US pressure** | **S1 — Opportunity** Motive + Means | **S3 — Rupee trap** Motive, no means |
| **Low US pressure** | **S2 — Feasible** Means, low motive | **S4 — Minimal case** Neither |

### S1 — Opportunity quadrant
Countries with both an incentive (US tariff/sanctions pressure) and the operational means (India trade surplus enables rupee recycling). Currently sparse at the major-economy level. Key examples: **Turkey** (US$2.7bn India surplus, US steel tariffs), **Vietnam** (19% reciprocal tariff), **Cambodia** (49% tariff — highest non-sanctions rate in ASEAN).

### S2 — Feasibility quadrant  
High rupee absorbability, low US pressure. India runs large surpluses — partners can recycle rupees — but the push factor is absent. Key examples: **Bangladesh** (US$9.3bn India surplus, SRVA Vostro accounts active), **Sri Lanka** (US$2.69bn surplus, Vostro accounts opened), **Nepal**, **Bhutan**. Demand here may rise as global dollar de-monopolisation accelerates.

### S3 — Rupee accumulation trap
Strong US pressure drives dollar-avoidance incentive, but India runs trade deficits — partners accumulate rupees with nowhere to deploy them. Paradigm case: **Russia** (India deficit US$57bn in 2024). Also: **Iran**, **China** (India deficit ~US$85bn). Policy fix: rupee asset outlets (Masala bonds, INR trade financing).

### S4 — Minimal case
Neither motive (low US pressure) nor means (India import deficit). Examples: **Saudi Arabia** (petrodollar anchor, India energy deficit ~US$32bn), **South Korea**, **UAE**.

---

## Dashboard features

- **2×2 interactive matrix** — hover over any country dot for full data
- **Scenario detail panel** — click any scenario card for full analysis and country list
- **Country data table** — filterable and sortable by scenario, US pressure, absorbability, trade volume
- **E_US index formula panel** — updated composite index including Trump reciprocal tariffs, with full 2025–26 tariff event timeline

---

## E_US Index formula

```
E_US,i = w1·T_i + w2·S_US,i + w3·F_i + w4·RT_i + w5·(1 − USD_inv,i)
```

| Variable | Definition | Weight |
|---|---|---|
| `T_i` | Share of exports under Section 301/232 tariffs (USTR) | 0.20 |
| `S_US,i` | Bilateral US trade / GDP — US economic reliance | 0.15 |
| `F_i` | OFAC sanctions flag (binary) | 0.25 |
| `RT_i` | **Trump reciprocal tariff rate** (normalised) — Liberation Day rates, Russia-oil penalties, Section 122 post-IEEPA ruling | **0.30** |
| `USD_inv,i` | Inverted USD invoicing share (BIS) | 0.10 |

`RT_i` carries the highest weight as the most dynamic and policy-relevant variable in 2025–26.

---

## Key 2025–26 tariff events captured

| Date | Event |
|---|---|
| Apr 2, 2025 | Liberation Day — 10% universal baseline + country-specific reciprocals under IEEPA |
| Apr 9, 2025 | 90-day pause for all except China (145%); India held at 26% |
| Jul–Aug 2025 | Rates finalised; India hit with +25% Russia-oil penalty → total 50% |
| Nov 2025 | US–China deal; rate reduced from 145% → 30% |
| Feb 2026 | Supreme Court strikes down IEEPA; Section 122 replaces. US–India deal: rate → 18%, Russia-oil penalty lifted |
| Mar 12, 2026 | USTR Section 301 forced-labour probe opened on 60+ countries including India, Bangladesh, Sri Lanka, UAE |

---

## Data sources

| Variable | Source |
|---|---|
| Bilateral trade (X, M) | UN Comtrade API · India Ministry of Commerce Data Bank |
| US tariff rates | USTR Section 301/232 lists · WTO Tariff Profiles |
| Reciprocal tariffs | USTR Liberation Day schedules (April 2025) |
| Sanctions | US Treasury OFAC SDN list |
| Rupee Vostro balances | RBI SRVA circulars · RBI Database on Indian Economy (DBIE) |
| FX reserves | IMF International Financial Statistics (IFS) |
| Correspondent banking | BIS CPIS · SWIFT Connectivity Reports |
| USD invoicing share | BIS Triennial Survey |

---

## How to update the data

All country data is in the `<script>` block at the bottom of `index.html`, in the `countries` array. Each country is one object:

```javascript
{name:"Bangladesh", Eus:0.38, absorb:0.82, B:0.78, surplus:9.3, total:20, sanction:0, s:"S2", vol:13,
 note:"India surplus US$9.3bn (2023–24); SRVA Vostro accounts active"},
```

To update a tariff rate or surplus figure: find the country by name, change the relevant number, commit the file. The live site updates within 2 minutes.

---

## Simulation models (forthcoming)

The simulation layer described in the full paper — Agent-Based Model (ABM), System Dynamics, and Monte Carlo scenarios — will be added as Python notebooks in `/models`. These require a Python runtime (Google Colab recommended) and cannot run directly on GitHub Pages.

---

## Citation

If you use this framework in research or policy work, please cite as:

> *RTSM Framework: A 2×2 Scenario Analysis of Rupee Trade Settlement Adoption* (2026).  
> Interactive dashboard: `https://your-username.github.io/rtsm-framework`

---

## Files in this repository

```
index.html       ← Live dashboard (open this in a browser)
README.md        ← This file
```

---

*Data current as of March 2026. Framework developed with reference to RBI SRVA circulars, IMF DOTS, UN Comtrade, USTR tariff schedules, and US Treasury OFAC data.*
