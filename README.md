# How to KudosMaxx: what drives engagement on Strava?

Group term project for MGSC 661 (Multivariate Statistics), McGill Master of Management in Analytics, 2026.

**Team:** Yasmine Mekki Berrada, Eglantine Dupuy, Astrid Philippet, Anto Abousefian
**My part:** Parts 4 and 5, checks and robustness (time-series check, refits, VIF, final model) and the logistic check and synthesis (breakout runs, H1 to H7 table, recommendations).

## Question

What drives the number of kudos a run gets on Strava: effort (distance, pace, PRs), presentation (photos, captions) or timing (weekends)?

## Data

Eglantine's Strava export, with kudos added by hand: 178 public runs from March 2024 to October 2026. Other activity types and private activities were removed. One runner, so the results are a case study.

## Approach

| Part | What it does |
|---|---|
| 1 | Cleaning, exploratory analysis, Welch t-tests, and a time control for audience growth (quadratic trend, since Strava keeps no past follower counts) |
| 2 | OLS baseline with robust (HC3) standard errors and diagnostics |
| 3 | Poisson count models A to D, likelihood-ratio tests, overdispersion check, rate ratios |
| 4 | Autocorrelation check, a previous-five-runs control, five robustness refits, VIF, locked final model |
| 5 | Logistic model of "breakout" runs, the H1 to H7 summary, recommendations |

## Main results (final Poisson model, 173 runs, robust standard errors)

- **Photo or video: about 20% more kudos** (rate ratio 1.20, p ≈ 0.0001). Significant in all five refits.
- **Distance: about 4% more kudos per km** (rate ratio 1.04, p < 0.001). Significant in all five refits.
- Weekend, captions, PRs, pace, elevation and achievements: no clear effect once distance, photos and audience growth are controlled for.
- Breakout runs (more kudos than the median of the previous 10): a photo multiplies the odds by 3.6. Test AUC 0.82 (0.71 on a time-based split).

| Hypothesis | Verdict |
|---|---|
| H1 Photo or video | Supported |
| H2 Achievements | Not supported |
| H3 Distance | Supported |
| H4 Caption or custom title | Not supported |
| H5 Speed | Not supported |
| H6 Weekend | Not supported once distance is controlled |
| H7 Personal record | Not supported |

## Files

- `KudosMaxx_Parts_1_5.ipynb`: the full analysis, with outputs.
- `How_to_KudosMaxx_Final_Presentation.pdf`: final presentation.

The raw export (`strava_activities.xlsx`) is not included. The notebook also writes CSV and PNG outputs to `outputs/` and `figures/` folders, which are not included either.

## Limitations

One runner and 178 runs; observational data, so photo runs may simply be more special runs; no historical follower counts; only 6 official races and 8 to 21 runs per PR level.
