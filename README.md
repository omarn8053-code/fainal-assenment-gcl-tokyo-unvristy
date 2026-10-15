# Telecom Churn Retention – "Predict → Time → Offer"

Final assignment for **GCI World 2026 September** (Matsuo-Iwasawa Lab, UTokyo): a data-driven business proposal to reduce customer churn at a mobile operator.

## Key findings (100,000 customers, churn rate 49.6%)
- Churn is **56.3%** when the handset is older than ~300 days vs **39.5%** when younger.
- Churn is **61.4%** at tenure months 11–13 vs **33.8%** at months 6–10 (likely end of the first commitment).
- Cheap handsets (≤ $50) churn more (57.5%) than premium ones (> $150: 41.0%).
- Best model: gradient boosting, **AUC 0.693** on a 20% hold-out set. The top-risk decile churns 78% vs 20% in the lowest.

## Proposal
Score customers monthly, act **before** the handset-age / tenure cliff, and send a timed handset-upgrade or loyalty offer to high-risk customers.

Simulated net profit (test outcomes scaled to 100k customers): about **$672K** per cycle when contacting the top 70% by risk vs **$548K** when contacting everyone.
These figures rest on **assumptions that are not in the data** (contact $2, incentive $100 paid on acceptance, 20% take-up, 40% margin, 12 months kept). A real A/B pilot is needed to measure take-up.

## Repository contents
| Path | What it is |
|---|---|
| `telecom_churn_retention.ipynb` | Full pipeline: EDA, feature engineering, 3 models, profit simulation |
| `slides/final_assignment_slides.pdf` | 13-slide presentation |
| `figures/` | Charts exported by the notebook |

## How to run
1. The dataset (`Client.csv`, `Record.csv`) comes from the course and is **not included** here.
2. Put both CSV files next to the notebook, or set `DATA_DIR` in the first code cell (Colab: path to the folder in your Drive).
3. `pip install -r requirements.txt`, then run all cells.

## Limitations
- The ~50% churn rate suggests re-sampled data, so absolute probabilities will differ on a live customer base.
- No contract-type or competitor data; financial inputs are assumptions.

*Built with AI assistance (Claude); see the assignment submission for the chat history.*
