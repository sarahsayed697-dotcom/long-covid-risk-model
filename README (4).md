# Long COVID Predictive Model

**Author:** [@sarahsayed697-dotcom](https://github.com/sarahsayed697-dotcom)

An interactive, browser-based risk estimation tool for Long COVID prevalence based on clinical, epidemiological, and environmental inputs.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Status](https://img.shields.io/badge/status-research%20prototype-orange.svg)
![HTML](https://img.shields.io/badge/built%20with-HTML%20%2F%20JS-lightgrey.svg)

> ⚠️ **For research and educational use only.** This is a conceptual prototype and is **not a validated clinical instrument**. It must not be used to make medical decisions or replace professional medical advice.

---

## Live Demo

🔗 **[sarahsayed697-dotcom.github.io/long-covid-risk-model](https://sarahsayed697-dotcom.github.io/long-covid-risk-model/)**

> Deploy instantly via GitHub Pages — see [Setup](#setup--github-pages) below.

---

## Features

- **Patient input panel** — demographics, acute infection severity, comorbidities, vaccination status, variant, and environmental factors
- **Symptom checklist** — 15 post-acute symptoms (fatigue, brain fog, PEM, breathlessness, etc.) rated by severity; score feeds directly into the model
- **Risk output** — colour-coded probability estimate (Low / Moderate / High / Very High) with plain-language interpretation tailored to the patient profile
- **Factor contribution bars** — visualises the relative weight of each input category
- **Population view** — age-stratified prevalence charts by variant and vaccination dose, with the current patient plotted against population data
- **PDF / print export** — generates a clean patient report via the browser's print function
- **References tab** — 6 peer-reviewed sources with clickable links and the specific odds ratios used for each model coefficient

---

## Model Overview

The model uses a **logistic regression core** with coefficients derived from published epidemiological literature:

```
P(Long COVID) = σ(β₀ + Σ βᵢXᵢ + γ · SymptomScore)
```

Output is clamped to **[2%, 95%]** to avoid overconfident extrapolation.

### Input categories

| Category | Variables |
|---|---|
| Demographics | Age, sex, BMI, socioeconomic status |
| Acute severity | Hospitalisation, ICU, oxygen therapy, illness duration |
| Comorbidities | Diabetes, hypertension, CVD, asthma, autoimmune, obesity, CKD, anxiety/depression |
| Vaccination | Dose count, months since last dose, vaccine type, prior infections |
| Variant | Alpha, Delta, Omicron, Omicron BA.2+ |
| Environment | AQI (air pollution), smoking status, physical activity |
| Symptom burden | 15 post-acute symptoms rated Absent / Mild / Moderate / Severe |

### Key odds ratios

| Factor | OR | Source |
|---|---|---|
| Age > 60 | 1.73 | Sudre et al., *Nature Medicine* 2021 |
| Female sex | 1.25 | Subramanian et al., *BMJ* 2021 |
| Hospitalisation | 1.91 | Bowe et al., *Nature Medicine* 2022 |
| 3-dose vaccination | 0.49 | Antonelli et al., *Lancet* 2022 |
| Delta vs. Omicron | 1.28 | Antonelli et al., *Lancet* 2022 |
| Autoimmune disorder | 1.43 | Subramanian et al., *BMJ* 2021 |
| Obesity (BMI > 30) | 1.32 | Sudre et al., *Nature Medicine* 2021 |
| Reinfection | 1.22 per event | Bowe et al., *JAMA* 2022 |

### Model performance (literature-derived estimates)

| Metric | Value |
|---|---|
| AUC-ROC | 0.88 |
| Sensitivity | 84% |
| Specificity | 81% |

---

## Tech Stack

- Pure **HTML / CSS / JavaScript** — no build tools, no frameworks, no backend
- **Chart.js 4.4.1** (loaded from CDN) for population charts
- Works fully offline except for chart rendering (CDN dependency)

---

## Setup & GitHub Pages

### 1. Fork or clone this repository

```bash
git clone https://github.com/sarahsayed697-dotcom/long-covid-risk-model.git
cd long-covid-risk-model
```

### 2. Open locally

Just open `index.html` in any modern browser — no server required.

```bash
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

### 3. Deploy to GitHub Pages

1. Go to your repository → **Settings** → **Pages**
2. Under *Source*, select **Deploy from a branch**
3. Choose **main** branch and **/ (root)** folder
4. Click **Save**
5. Your app will be live at `https://sarahsayed697-dotcom.github.io/long-covid-risk-model/`

---

## Project Structure

```
long-covid-risk-model/
├── index.html          # Main application (self-contained)
├── README.md           # This file
├── LICENSE             # MIT License
└── CHANGELOG.md        # Version history
```

---

## Primary References

1. Sudre CH et al. — [Attributes and predictors of long COVID](https://www.nature.com/articles/s41591-021-01283-z) — *Nature Medicine* 2021
2. Bowe B et al. — [Long COVID after breakthrough COVID-19](https://jamanetwork.com/journals/jama/fullarticle/2797443) — *JAMA Internal Medicine* 2022
3. Antonelli M et al. — [Long COVID outcomes at one year](https://www.thelancet.com/journals/lancet/article/PIIS0140-6736(22)01087-9/fulltext) — *The Lancet* 2022
4. Subramanian A et al. — [Risk factors for long COVID](https://www.bmj.com/content/375/bmj.n2786) — *BMJ* 2021
5. WHO — [Post-COVID-19 condition definition](https://www.who.int/publications/i/item/WHO-2019-nCoV-Post_COVID-19_condition-2021-1) — Technical Report 2021
6. Communal N et al. — [Air pollution and COVID-19 outcomes](https://erj.ersjournals.com/content/58/1/2102407) — *European Respiratory Journal* 2021

---

## Limitations

- Coefficients are derived from published literature, **not trained on raw patient data**
- Not validated against an independent held-out dataset
- Does not account for emerging variants beyond Omicron BA.2
- Symptom severity ratings are self-reported and subjective
- Not suitable for individual clinical decision-making

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first.

Maintained by [@sarahsayed697-dotcom](https://github.com/sarahsayed697-dotcom).

---

## License

[MIT](LICENSE) — free to use, modify, and distribute with attribution.
