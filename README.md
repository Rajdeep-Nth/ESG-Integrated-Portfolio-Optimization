# ESG-Integrated-Portfolio-Optimization
Combining ESG scores and stock performance to offer an optimized view for Indian investors.
## 1. Introduction
The increasing regulatory, consumer, and institutional focus on sustainability has made ESG-integrated investing mainstream in Indian markets. While investors seek returns, they are also increasingly required to consider ESG impact when allocating capital. Classical Modern Portfolio Theory (MPT) does not include ESG objectives; hence, a multi-objective optimization approach is required to balance risk, return, and sustainability in portfolio construction.

## 2. Problem Statement
How can an investor construct an equity portfolio that maximizes financial returns, minimizes risk, and meets minimum ESG qualityâ€”especially using assets and ESG ratings from Indian stock markets and indices?

## 3. Objective & Significance
- Develop a portfolio optimization framework that jointly maximizes Sharpe ratio and ESG score, while controlling risk and meeting regulatory or concentration constraints.
- Offer actionable and replicable tools for sustainable investment decision-making in Indian financial markets.
- Build a user-accessible web application to automate and visualize the optimization process.

## 4. Literature Review
- NSGA-III and other evolutionary algorithms have found recent success in multi-objective portfolio selection[99][61][103].
- Academic work on Indian ESG indices recognizes the existence of BSE 100 ESG, NSE Nifty100 ESG, and specialty indices (Greenex, Carbonex) as key data sources[68][75][101][104].
- Current research establishes the business case and outperformance potential for high-ESG portfolios in India[112].

## 5. System Design and Architecture
### Backend
- Python (Flask/FastAPI)
- pymoo for multi-objective optimization
- Data pipeline for fetching stock prices and ESG scores (NSE/BSE, third-party APIs)

### Frontend
- React/Bootstrap web interface
- Dashboard visualization (charts, Pareto frontier, performance metrics)
- RESTful API integration

### Database
- PostgreSQL or cloud-hosted DB for price, return, and ESG data
---

## 6. Mathematical Formulation
Let N = number of assets. Decision variable w = [w1, ..., wN], where wi is the portfolio weight for asset i.

### Objective Functions
- **Maximize Sharpe Ratio:**
  
    \[
    \text{Sharpe}(w) = \frac{\mu^T w - r_f}{\sqrt{w^T \Sigma w}}
    \]
  Where \( \mu \) is vector of expected returns, \( r_f \) is risk-free rate, and \( \Sigma \) is the covariance matrix.

- **Maximize ESG Score:**
  
    \[
    \text{ESG}(w) = esg^T w
    \]
  Where \( esg \) is the ESG score vector for assets.

- **Minimize Portfolio Variance:** (Optional)
  
    \[
    \text{Var}(w) = w^T \Sigma w
    \]

### Constraints
- Fully invested: \( \sum_{i=1}^N w_i = 1 \)
- No short selling: \( w_i \geq 0 \) for all i
- Max single-asset exposure: \( w_i \leq b_{max} \) (e.g., 15%)
- ESG threshold (optional): \( esg^T w \geq ESG_{min} \)
- Sector exposures, cardinality (optional)

### Multi-Objective Evolutionary Optimization
Use NSGA-III to generate Pareto-optimal portfolios for simultaneous objective maximization[61][103].

---

## 7. Data Sources and ESG Ratings
- **Stock prices**: NSE/BSE official APIs, Yahoo Finance India, or data vendors
- **ESG ratings**: SES (BSE), NSE Sustainability Ratings, Nifty100 ESG index methods
- **Index methodology references**: [68][75][101][104][107]

### ESG Scoring in India
- Stocks graded A+ to D based on environmental, social, and governance disclosures[101][104]
- Ratings updated annually using SES and public sustainability reports

---

## 8. Implementation Workflow
1. **Data Pipeline Setup**: Fetch prices & ESG scores for chosen stock universe
2. **Return & Risk Calculation**: Calculate log returns, covariance matrix
3. **ESG Score Processing**: Convert categorical/environmental ESG grades to normalized scores
4. **Optimization Model**: Define objectives & constraints, run NSGA-III/pymoo
5. **Results Extraction**: Identify Pareto frontier, best portfolios by risk/return/ESG
6. **Visualization & Reporting**: Show allocations, historical simulation, and performance/ESG comparison

---

## 9. System Features (Web Application)
- Asset selection (NSE/BSE stocks)
- Parameter sliders: Risk tolerance, ESG target, max asset weight
- Optimization run with visualization of Sharpe-ESG-Pareto front portfolios
- Summary analytics: Backtest, ESG compliance reporting, trade-off exploration
- Downloadable reports & outputs
- (Optionally) User login, saved portfolios, live data refresh

---

## 10. Analysis and Expected Outcomes
- Will generate a set of optimized portfolios with explicit trade-offs between risk, return, and ESG
- Empirical demonstration of Indian ESG indices' utility in sustainable investing
- User-friendly system for academic or practical extension
- Possible insights: ESG-tilted portfolios may mitigate downside risk with limited return sacrifice[61][68][104][112]

## 11. References
[61][68][75][99][101][103][104][107][112]

---

## Appendix â€“ List of Indian ESG Indices
- Nifty100 ESG
- Nifty100 Enhanced ESG
- S&P BSE 100 ESG
- S&P BSE Greenex
- S&P BSE Carbonex
