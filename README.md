# Bayesian Breakout Prediction for Young Forwards

**Brief Description**  
Analysis to forecast 2025 breakout stars among young (U24) forwards in the Premier League and Championship, using a weighted **Breakout Index** and a **Bayesian hierarchical regression** with partial pooling.

---

## Data Source  
Data was collected from [FBref.com](https://fbref.com) and [ClubElo.com](https://clubelo.com).

---

## Files  
- **breakout.ipynb**: The Jupyter Notebook containing the data-prep, model code, and visualisations.  
- **breakout1.csv**: The curated dataset used for analysis.

---

## Analysis Methods  
Here you’ll find the full mathematical details and model specifications:

1. **Breakout Index Definition**  
  breakout_index_i = 0.35 * npxG_per90 
                  + 0.25 * xA_per90 
                  + 0.15 * PrgC_per90 
                  + 0.15 * CPA_per90 
                  + 0.10 * SuccTkon_per90

2. **Bayesian Hierarchical Regression**  
   breakout_index_i ~ Normal(mu_i, sigma)

    mu_i = alpha_team[i]
      + beta_age       * Age_i
      + beta_elo       * ELO_i
      + beta_PrgC      * PrgC_i
      + beta_CPA       * CPA_i
      + beta_SuccTkon  * SuccTkon_i

   - **α<sub>team</sub>** are team-level random intercepts (partial pooling).  
   - **β** coefficients capture the average effect of each feature.  
   - Implemented in **Bambi** (PyMC backend) with default weakly-informative priors.

3. **Inference & Visualization**  
   - Posterior sampling via MCMC (ℎ𝑎𝑚𝑖𝑙𝑡𝑜𝑛𝑖𝑎𝑛 Monte Carlo).  
   - **Posterior distributions** of coefficients & credible intervals.  
   - **Posterior-mean predictions** for each player.  
   - **Ranked tables**, **histograms**, and **scatter plots** to communicate findings.

---

## Article  
The corresponding article can be found at:  
[https://your-substack-link.com/bayesian-breakouts](https://underthelights.substack.com/p/predicting-breakout-forwards-with)  

---
