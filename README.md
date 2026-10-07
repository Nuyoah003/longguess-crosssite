# LongGuess — Cross-Site Password Guessing Results

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23208965.svg)](https://doi.org/10.5281/zenodo.23208965)

Supplementary data for the paper:

> **Bridging Short and Long Password Spaces: The LongGuess Framework for Sparse Password Modeling**
> Xudong Yang, Zhenjia Xiao, Jincheng Li, Kaiwen Xing, Keshav Sood, Hu Xiong (Senior Member, IEEE)

This repository hosts the additional cross-site experimental results of the paper (Fig. 9,
Appendix "Additional Cross-Site Results") together with the raw counts behind the efficiency
table, and points to the leaked password datasets used in this work. It is intended as a
code/data companion, not as an appendix: the paper is self-contained and reports its
conclusions in the body.

## Datasets

The leaked password datasets used in this work are openly available at:

**<https://drive.google.com/drive/folders/1RyMspmJPBt01smMUZ8mDsOiuhnNqJCcg?usp=sharing>**

The evaluation draws on **Rockyou, 7K7K, CSDN, Dodonew, Netease, Mathway, 000Webhost,
Linkedin, Parkmobile, Craftrise, Clixsense** and **Tianya**. Please refer to Table I of the
paper for the source, language and release date of each dataset, and to the dataset licences
for terms of use.

## Contents

```
figures/
  eps/                     15 vector figures (.eps) — one per cross-site scenario
  fig9_overview.pdf        all 15 curves composed as in Fig. 9 of the paper
  fig9_overview.png        raster version of the above
  fig9_overview.tex        LaTeX source that composes the overview
  subfigure_index.csv      maps each .eps file to its scenario pair
data/
  table6_efficiency_counts.csv   raw counts behind the efficiency table
```

## Cross-site scenarios

Each figure plots the **cumulative number of cracked long passwords** against the **guessing
budget** (10^1 … 10^14) for eight models:

`PCFG`, `OMEN`, `FLA`, `CKL_PCFG`, `RFGuess`, `LongGuess-corpus`, `LongGuess-pwd`,
`LongGuess-pwd+corpus`.

Dataset abbreviations: `MW` Mathway, `NE` Netease, `WH` 000Webhost, `DN` Dodonew,
`PM` Parkmobile, `TY` Tianya, `CR` Craftrise, `TB` Taobao, `RY` Rockyou, `CD` CSDN.
`A+B → C+D` means the models are trained on A+B and evaluated on C+D.

| # | Scenario | File |
|---|---|---|
| a | MW+NE → WH+DN | `cross_mathway_netease2000webhost_dodonew_longguess.eps` |
| b | MW+NE → PM+TY | `cross_mathway_netease2parkmobile_tianya_longguess.eps` |
| c | MW+NE → CR+TB | `cross_mathway_netease2craftrise_taobao_longguess.eps` |
| d | WH+DN → RY+CD | `cross_000webhost_dodonew2rockyou_csdn_longguess.eps` |
| e | WH+DN → MW+NE | `cross_000webhost_dodonew2mathway_netease_longguess.eps` |
| f | WH+DN → PM+TY | `cross_000webhost_dodonew2parkmobile_tianya_longguess.eps` |
| g | WH+DN → CR+TB | `cross_000webhost_dodonew2craftrise_taobao_longguess.eps` |
| h | PM+TY → RY+CD | `cross_parkmobile_tianya2rockyou_csdn_longguess.eps` |
| i | PM+TY → MW+NE | `cross_parkmobile_tianya2mathway_netease_longguess.eps` |
| j | PM+TY → WH+DN | `cross_parkmobile_tianya2000webhost_dodonew_longguess.eps` |
| k | PM+TY → CR+TB | `cross_parkmobile_tianya2craftrise_taobao_longguess.eps` |
| l | CR+TB → RY+CD | `cross_craftrise_taobao2rockyou_csdn_longguess.eps` |
| m | CR+TB → MW+NE | `cross_craftrise_taobao2mathway_netease_longguess.eps` |
| n | CR+TB → WH+DN | `cross_craftrise_taobao2000webhost_dodonew_longguess.eps` |
| o | CR+TB → PM+TY | `cross_craftrise_taobao2parkmobile_tianya_longguess.eps` |

Evaluation protocol (datasets, preprocessing, guess budgets, baseline configuration) is
described in the paper.

## Efficiency counts

`data/table6_efficiency_counts.csv` gives the cumulative number of cracked long passwords for
`LongGuess-pwd` before (`Original`) and after (`Optimised`) the efficiency optimisation, at
budgets 10^1 … 10^14, on two cross-site scenarios:

- **Scenario 1**: train on Rockyou+CSDN, test on Craftrise+Taobao (`RY+CD → CR+TB`)
- **Scenario 2**: train on Parkmobile+Tianya, test on 000Webhost+Dodonew (`PM+TY → WH+DN`)

Columns: `scenario, model, 10^1, 10^2, …, 10^14`.

## Viewing the figures

The `.eps` files are vector graphics. Use any EPS-capable viewer, or convert them, e.g.

```bash
# to PDF (poppler)
epstopdf figures/eps/cross_mathway_netease2000webhost_dodonew_longguess.eps
```

For quick viewing, open `figures/fig9_overview.pdf` (or the `.png`).

To rebuild the overview from the individual `.eps` files:

```bash
cd figures
pdflatex -shell-escape fig9_overview.tex      # -shell-escape is required (eps -> pdf)
```

## License

Data and figures: CC BY 4.0 (see `LICENSE`). The leaked password datasets are distributed by
their original collectors; please respect their terms of use. Please cite the paper above if
you use these results.

## Notes

- Raw per-point curve values are not included; the figures are the authoritative rendering of
  these results. Curves were produced with Matplotlib.
- If you need the underlying numeric series, please contact the authors.
