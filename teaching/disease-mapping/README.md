# Disease mapping — childhood obesity in Palma

A hands-on **spatial epidemiology** seminar for **2nd-year Nursing** students.

It walks through the descriptive core of *disease mapping* with **areal data**: observed vs. expected counts, **indirect standardisation**, the **Standardised Incidence Ratio (SIR / RIE)**, static and interactive choropleth maps, the **socioeconomic gradient** of childhood obesity, and the **small-numbers problem**. Bayesian smoothing (INLA/BYM) is deliberately left out and only pointed to as the next step.

Deliberately introductory and applied to the Pre-Environs research line.

## Files

```
disease-mapping/
├── index.qmd          # the tutorial — Spanish (Quarto + R)
├── index-ca.qmd       # the tutorial — Catalan
├── _quarto.yml        # project config (renders to _site/)
├── referencias.bib    # bibliography
└── data/
    ├── palma_secciones.geojson                  # 245 census sections (real geometry + covariates)
    ├── obesidad_infantil_palma_sintetica.csv    # synthetic child-obesity counts
    └── README.md                                # data dictionary & provenance
```

> Health data are **synthetic**. Deprivation (SEE IP2011) and income (INE ADRH 2022) covariates are **real**. No health microdata are used or published.

## Render locally

Requires [R](https://www.r-project.org/) and [Quarto](https://quarto.org/docs/get-started/).

```bash
# from this folder
quarto render
# outputs: _site/index.html (Spanish) and _site/index-ca.html (Catalan)
```

R packages: `sf`, `dplyr`, `readr`, `ggplot2`, `leaflet`, `htmltools`, `scales`, `RColorBrewer`, `knitr`, `rmarkdown`.

## Publish on GitHub Pages

The workflow [`.github/workflows/publish.yml`](../../.github/workflows/publish.yml) renders and deploys automatically on every push.

**One-time setup:** in the repository, go to **Settings → Pages → Build and deployment → Source** and choose **"GitHub Actions"**. After the first run, the live URL appears in the workflow summary (typically `https://preenvirons.github.io/PreEnvirons/`).
