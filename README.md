# NBA Team Ranking Prediction

This project uses NBA team-level performance statistics to predict end-of-season rankings. It applies statistical inference and machine learning techniques to understand which in-season metrics most strongly influence team success.

## Objective

- Predict each team's final season rank (1–30) using only in-season statistics.
- Identify which performance metrics have the strongest influence on end-of-season rankings.
- Evaluate model accuracy using R², MSE, and classification performance for Top 8 teams.

## Dataset Description

All data is stored in the `data/` directory. The following CSV files were used:

| File | Description |
|------|-------------|
| `Team Stats Per 100 Poss.csv` | Offensive team stats normalized per 100 possessions. |
| `Opponent Stats Per 100 Poss.csv` | Opponent stats allowed per 100 possessions. |
| `Team Summaries.csv` | Summary stats like win/loss record, Net Rating (`n_rtg`), SRS, pace, etc. |
| `Team Stats Per Game.csv` | Per-game team stats (optional, not used directly in modeling). |
| `Team Totals.csv` | Raw totals for all stats (not used directly, but available). |

After merging, the final dataset includes one row per team per season with their performance statistics and final rank (`season_rank`).

## Methods

### 1. Statistical Inference
- Hypothesis Test: Whether teams in the Top 8 differ in `Net Rating` from others.
- Bootstrap Sampling: 1,000 iterations to estimate confidence intervals.
- T-Test: Showed statistically significant difference (p < 0.001).

### 2. Predictive Modeling
- Random Forest Regressor: Used to predict `season_rank` from 9 core features.
- Performance:  
  - R² ≈ 0.88  
  - MSE ≈ 8.5  
  - Predictions closely matched actual rankings.

### 3. Classification
- Logistic Regression: Binary classification of whether a team finishes in the Top 8.
- Accuracy: 91%  
- Precision/Recall: Strong performance for both Top 8 and non-Top 8 teams.

## Key Features Used

- `e_fg_percent`: Effective FG%
- `tov_percent`: Turnover Rate
- `orb_percent`: Offensive Rebound Rate
- `ft_fga`: Free Throw Rate
- `pace`: Team pace
- Opponent versions of the above: `opp_e_fg_percent`, `opp_tov_percent`, etc.

## Key Insights

- Net Rating is the most statistically significant predictor of final ranking.
- Shooting efficiency and turnover margins are strong drivers of team success.
- Predictions are most accurate for high- and low-performing teams; mid-ranked teams are harder to distinguish.

## Tools Used

- Python (Pandas, NumPy, Scikit-Learn, Matplotlib, Seaborn)
- Jupyter Notebook
- Git and GitHub for version control

## Author(s)
Matthew Lertsmitivanta

This project was completed as part of a university sports analytics capstone. Contact mlertsmitivanta@gmail.com for questions or replication.
