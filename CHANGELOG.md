# Changelog

All notable changes to this project will be documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [1.2.0] — 2026-03-19

### Added
- **Symptom checklist tab** — 15 post-acute symptoms rated by severity (Absent / Mild / Moderate / Severe); weighted burden score feeds into the logistic regression model
- **Plain-language interpretation** — dynamic, patient-specific paragraph explaining the risk output in plain English, adapting to hospitalization, vaccination status, comorbidities, and symptom burden
- **PDF / print export** — "Export as PDF" button triggers a print stylesheet producing a clean patient report with date stamp and disclaimer
- **References tab** — 6 peer-reviewed sources with clickable links; odds ratio table with full attribution for each model coefficient
- **Input validation** — ICU toggle is now disabled unless Hospitalization is also checked (ICU without hospitalization is clinically impossible)
- Chronic kidney disease added as a comorbidity option
- Patient marker plotted on population age-band chart (triangle marker at patient's age group)
- Patient's current vaccination dose highlighted with border on the vaccination chart

### Changed
- Navigation restructured to 5 tabs: Patient inputs → Symptom checklist → Risk output → Population view → References
- Symptom burden score integrated into the model formula: P = σ(β₀ + ΣβᵢXᵢ + γ·SymptomScore)
- Factor contribution bars now include a "Symptom burden" row
- "Edit inputs" back button added to results tab

---

## [1.1.0] — 2026-03-18

### Added
- Disclaimer banner (amber, top of page) marking the tool as research/educational only
- Print stylesheet for basic PDF export

### Changed
- Disclaimer moved inside the container div for correct layout
- Tab structure cleaned up

---

## [1.0.0] — 2026-03-17

### Initial release

- Logistic regression model with 6 input categories: demographics, acute severity, comorbidities, vaccination, variant, environment/lifestyle
- Three-tab layout: Patient inputs / Risk output / Population view
- Colour-coded risk card (Low / Moderate / High / Very High)
- Factor contribution bar chart
- Protective vs. risk factor badges
- Population prevalence charts by age group (variant comparison) and vaccination dose
- Key epidemiological findings bar chart
- Chart.js 4.4.1 for data visualisation
- Fully self-contained single HTML file — no backend, no build tools
