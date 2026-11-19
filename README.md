# Shopping-Behaviour

Code, data and questionnaire for the study **"Spending Without Trust: Influencer Exposure, Risk Containment and Social-Commerce Spending among Young Consumers in Bangladesh"**.

The study uses a cross-sectional survey of young social media users in Bangladesh. It asks whether trust in influencers decides if young consumers buy through social media, how much they spend, and which practices (such as cash on delivery and other safeguards) contain the risk when trust is low.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Alamgir-JUST/Shopping-Behaviour/blob/main/Shopping_Colab_Analysis.ipynb)
![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![Status](https://img.shields.io/badge/status-manuscript%20in%20preparation-lightgrey)

---

## Repository contents

| File | Description |
|---|---|
| `Shopping_Colab_Analysis.ipynb` | Full analysis notebook (18 numbered cells). It cleans the data and produces every table and figure in the article. |
| `survey_data.csv` | Survey data: 524 raw responses, 49 columns. |
| `Questionnaire.pdf` | The survey instrument, with all items and answer options. |
| `README.md` | This file. |

## Study at a glance

| Item | Value |
|---|---|
| Raw responses | 524 |
| After cleaning | 515 |
| Regression sample | 512 |
| Trust groups (regression sample) | Low 258, moderate 168, high 86 |
| Main exposure | Trust in influencers (Q18), analysed per +1 SD |
| Main outcomes | Ever bought, any monthly spend, spend thresholds, spend level, purchase frequency |
| Main models | Logit and ordered logit with robust (HC1) standard errors, covariate sets M0 to M3 (M2 is the main model) |

## Main findings

- A one standard deviation rise in trust is linked to higher odds of spending. The odds ratio is about 2.6 for any monthly spend and about 1.7 for spending at least BDT 500.
- Trust is only weakly related to whether a person has ever bought, and this result is fragile.
- Among respondents with low trust, about 74% still spend each month.
- Cash on delivery carries about 4% of the link between trust and spending. Four safeguards together carry about 8%. The number of influencers followed carries about 29%.
- Among low trust consumers, exposure and engagement explain spending better than income.
- The data are cross sectional and self reported, so all results are associations, not causal effects.

Full results, tables and figures are in the article and in the notebook outputs.

## Methods implemented

- Data cleaning, recoding and a data quality audit
- Descriptive statistics and group comparisons with multiplicity control (Benjamini-Hochberg FDR)
- Exploratory and confirmatory factor analysis, parallel analysis, reliability and validity
- Logit and ordered logit models with robust errors, and average marginal effects
- Equivalence tests (TOST), Bayes factors, Firth logit and bootstrap contrasts
- Mediation (5,000 bootstrap resamples) and moderation (12 moderators on 3 outcomes)
- Tests of the satisfaction hypothesis (H6) and the low trust spenders hypothesis (H7)
- Robustness checks: a 128 model specification curve, multiple imputation (m = 50), E-values and a second trust measure
- Latent class analysis of risk-containment practices (self-implemented EM algorithm)

## Notebook structure

| Cell | Content |
|---|---|
| 1 | Setup, figure style, helper functions, raw data and codebook |
| 2 | Cleaning, recoding, data quality audit and analytic samples |
| 3 | Sample profile |
| 4 | Descriptives: Likert items and behavioural outcomes |
| 5 | Multi-response and single-choice items |
| 6 | Measurement: factorability, parallel analysis, EFA and reliability |
| 7 | Confirmatory factor analysis and validity |
| 8 | The trust gradient |
| 9 | Group differences with multiplicity control |
| 10 | Correlations and collinearity |
| 11 | Core models: does trust gate participation or throttle intensity? |
| 12 | Is "ever bought" really unrelated to trust? |
| 13 | Risk-containment safeguards and cash on delivery (H3) |
| 14 | Mediation (H4) and moderation (H5) |
| 15 | Satisfaction (H6) and low trust spenders (H7) |
| 16 | Robustness checks, including the second trust measure |
| 17 | Latent class analysis of risk-containment practices |
| 18 | Export of tables, figures and captions |

## How to reproduce

### Option A: Google Colab (recommended)

1. Click the **Open in Colab** badge above.
2. Download `survey_data.csv` from this repository. In your Google Drive, create the folder `MyDrive/Shopping/` and upload the file into it.
3. Run the cells from top to bottom (**Runtime → Run all**). Later cells reuse objects from earlier ones, so do not skip cells and do not restart the runtime before Cell 18.
4. Results are written to `MyDrive/Shopping/outputs/`.

To use other locations, edit `DATA_PATH` and `OUT` in Cell 1.

### Option B: Local Jupyter

1. Clone the repository:
   ```bash
   git clone https://github.com/Alamgir-JUST/Shopping-Behaviour.git
   cd Shopping-Behaviour
   ```
2. Install the dependencies:
   ```bash
   pip install numpy pandas scipy statsmodels patsy matplotlib scikit-learn openpyxl semopy jupyter
   ```
   Cell 7 installs `semopy` automatically if it is missing.
3. Skip the Google Drive mount step at the top of the notebook. In Cell 1, set the two paths to local locations:
   ```python
   DATA_PATH = "survey_data.csv"
   OUT = "outputs"
   ```
4. Run all cells in order.

Total run time is about 15 to 20 minutes in Colab. Cells 16 and 17 are the slowest, at about 4 to 5 minutes each.

## Outputs

The notebook writes the following to `outputs/`:

- `tables/`: every table as CSV
- `figures/`: every figure as 300 dpi PNG and vector PDF
- `export/`: one Excel workbook with an index sheet, suggested figure captions, and a ZIP of everything

## Data description

`survey_data.csv` holds one row per respondent. The questionnaire (`Questionnaire.pdf`) covers:

- Demographics and social media use
- Exposure to influencers and the number of influencers followed
- Trust in influencers (Q18 and a Likert statement on trusting product recommendations)
- Perceived risk and risk-containment practices (cash on delivery, return policy, reviews, seller checks)
- Purchase behaviour (ever bought, frequency, monthly spend)
- Satisfaction and regret

Cell 1 contains the codebook that maps column names to short variable names. Cell 2 documents every recoding and exclusion.

### Privacy and ethics

- Participation was voluntary. Ethics approval details are given in the article.
- The file contains no names or contact details. Respondents are not identified.
- Please do not try to identify any respondent, and do not link these data to other sources for that purpose.

## Citation

If you use the code, data or questionnaire, please cite the article once it is published:

```bibtex
@article{shopping_behaviour_2026,
  title   = {Spending Without Trust: Influencer Exposure, Risk Containment and Social-Commerce Spending among Young Consumers in Bangladesh},
  author  = {Author A and Author B and Author C and Author D},
  journal = {[Journal]},
  year    = {2026},
  doi     = {[DOI]}
}
```

## License

- Code: MIT License
- Data and questionnaire: CC BY 4.0

## Contact

Corresponding author: Md. Alamgir Hossain (`alamgir.cse14.just@gmail.com`)

Repository maintainer: [Alamgir-JUST](https://github.com/Alamgir-JUST)
