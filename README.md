# Bayesian Breakout Prediction for U21 Forwards

**Brief Description**  
Analysis to forecast 2025 breakout stars among U21 forwards in the Premier League and Championship, using a weighted **Breakout Index** and a **Bayesian hierarchical regression** with partial pooling.

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
   \[
   \text{breakout\_index}_i = 0.35\,\text{npxG}_i + 0.25\,\text{xA}_i 
   + 0.15\,\text{PrgC}_i + 0.15\,\text{CPA}_i + 0.10\,\text{SuccTkon}_i
   \]

2. **Bayesian Hierarchical Regression**  
   \[
   \begin{aligned}
   \text{breakout\_index}_i &\sim \mathcal{N}(\mu_i,\,\sigma) \\
   \mu_i &= \alpha_{\text{team}[i]} 
             + \beta_{\text{age}}\cdot\text{Age}_i
             + \beta_{\text{elo}}\cdot\text{ELO}_i
             + \beta_{\text{PrgC}}\cdot\text{PrgC}_i \\
          &\quad\; + \beta_{\text{CPA}}\cdot\text{CPA}_i
             + \beta_{\text{SuccTkon}}\cdot\text{SuccTkon}_i
   \end{aligned}
   \]

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
Corresponding article can be found at:  
https://your-substack-link.com/bayesian-breakouts  

---
