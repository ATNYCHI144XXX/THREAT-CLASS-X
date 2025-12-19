# Mathematical Framework for Threat Analysis

## Overview
This document provides the mathematical and statistical foundations for analyzing threats in the THREAT-CLASS-X repository. All threat assessments should be grounded in quantifiable models with explicit assumptions.

---

## Core Principles

### 1. Quantifiable Risk Assessment
Every threat must be evaluated using:

$$R = P \times I \times (1 - M)$$

Where:
- $R$ = Risk score (0-10 scale)
- $P$ = Probability of occurrence (0-1)
- $I$ = Impact severity if occurs (0-10 scale)
- $M$ = Mitigation capability (0-1, where 1 = fully mitigable)

**Interpretation**:
- $R < 1$: Low priority monitoring
- $1 \leq R < 3$: Medium priority, develop mitigation
- $3 \leq R < 5$: High priority, active mitigation required
- $R \geq 5$: Critical, immediate action necessary

### 2. Uncertainty Quantification
All parameters must include confidence intervals:

$$P = p_{est} \pm \sigma_p$$

Report as: "Probability = 0.15 ± 0.05 (68% CI)"

### 3. Time-Dependent Analysis
Threats evolve over time:

$$R(t) = P(t) \times I(t) \times (1 - M(t))$$

Track temporal changes quarterly.

---

## Statistical Methods

### Probability Estimation Techniques

#### A. Frequency-Based (Historical Data Available)
For recurring events with historical record:

$$P_{annual} = \frac{n_{events}}{T_{observation}}$$

**Example**: Cascadia megathrust
- Historical events: 41 in past 10,000 years
- Average recurrence: 244 years
- $P_{annual} = 1/244 = 0.0041$ per year

**Cumulative Probability** (for $t$ years):
$$P(t) = 1 - e^{-\lambda t}$$

Where $\lambda = 1/T_{recurrence}$

#### B. Bayesian Estimation (Limited Data)
When historical data is sparse:

$$P(A|B) = \frac{P(B|A)P(A)}{P(B)}$$

Update probabilities as new evidence emerges.

#### C. Expert Elicitation
When no data exists:
1. Survey multiple independent experts
2. Use geometric mean: $P = \sqrt[n]{p_1 \times p_2 \times ... \times p_n}$
3. Report disagreement as uncertainty

**Minimum**: 3 experts, diverse backgrounds

---

## Models for Specific Threat Categories

### Geological/Tectonic Threats

#### Earthquake Probability

**Gutenberg-Richter Relationship**:
$$\log_{10} N = a - bM$$

- $N$ = number of earthquakes $\geq$ magnitude $M$ per year
- $a$ = regional seismicity (log of total events)
- $b$ ≈ 1.0 (typically 0.8-1.2)

**Application**: 
If $a = 5$ (region has 100,000 M≥0 quakes/year), then:
- M≥5: $N = 10^{5-5} = 100$ per year
- M≥6: $N = 10^{5-6} = 10$ per year
- M≥7: $N = 10^{5-7} = 1$ per year

**Fault Slip Accumulation**:
$$\Delta D = v \times t$$

- $\Delta D$ = slip deficit (meters)
- $v$ = plate velocity (m/year)
- $t$ = time since last rupture (years)

**Critical Threshold**: When $\Delta D > D_{characteristic}$, rupture likely.

#### Volcanic Eruption Forecasting

**Repose Interval Method**:
$$P(t) = \frac{t}{\bar{t}}$$ for $t < 2\bar{t}$

Where $\bar{t}$ = mean repose time between eruptions.

**Cox Model** (with precursors):
$$\lambda(t) = \lambda_0(t) e^{\beta_1 x_1 + \beta_2 x_2 + ...}$$

- $\lambda_0(t)$ = baseline hazard
- $x_i$ = precursor variables (seismicity, deformation, gas emissions)
- $\beta_i$ = coefficients (from historical data)

---

### Biological/Ecological Threats

#### Population Growth Model

**Logistic Growth**:
$$\frac{dP}{dt} = rP\left(1 - \frac{P}{K}\right)$$

- $P$ = population size
- $r$ = intrinsic growth rate
- $K$ = carrying capacity

**Solution**:
$$P(t) = \frac{K P_0 e^{rt}}{K + P_0(e^{rt}-1)}$$

**Application**: De-extinct species population trajectory
- Initial: $P_0 = 1$ (first individual)
- Growth rate: $r$ depends on species (0.03/year for elephants)
- Carrying capacity: $K$ = ecosystem-dependent

**Time to Viable Population** ($P_{viable} = 1000$):
$$t = \frac{1}{r}\ln\left(\frac{P_{viable}(K-P_0)}{P_0(K-P_{viable})}\right)$$

#### Predator-Prey Dynamics

**Lotka-Volterra Equations**:
$$\frac{dP}{dt} = \alpha P - \beta PC$$
$$\frac{dC}{dt} = \delta \beta PC - \gamma C$$

- $P$ = prey population
- $C$ = predator (carnivore) population
- $\alpha$ = prey growth rate
- $\beta$ = predation rate
- $\delta$ = conversion efficiency
- $\gamma$ = predator death rate

**Equilibrium**:
$$P^* = \frac{\gamma}{\delta \beta}, \quad C^* = \frac{\alpha}{\beta}$$

**Application**: Impact of reintroduced megafauna predators

#### Epidemic Spread (Ancient Pathogens)

**SIR Model**:
$$\frac{dS}{dt} = -\beta SI$$
$$\frac{dI}{dt} = \beta SI - \gamma I$$
$$\frac{dR}{dt} = \gamma I$$

- $S$ = susceptible
- $I$ = infected
- $R$ = recovered/removed
- $\beta$ = transmission rate
- $\gamma$ = recovery rate

**Basic Reproduction Number**:
$$R_0 = \frac{\beta S_0}{\gamma}$$

If $R_0 > 1$: epidemic spreads
If $R_0 < 1$: epidemic dies out

**For ancient pathogens**: $S_0 \approx N$ (entire population susceptible)

---

### Magnetic Field Threats

#### Dipole Decay Model

**Exponential Decay**:
$$B(t) = B_0 e^{-\lambda t}$$

Current Earth's field:
- $B_0 = 50,000$ nT (1900)
- $B(2025) = 48,000$ nT
- $\lambda = \frac{\ln(50000/48000)}{125} \approx 0.000326$ per year
- Decay rate: ~5% per century

**Extrapolation** (linear approximation for small $t$):
$$B(2100) \approx 48000 \times (1 - 0.05 \times 0.75) = 46,200 \text{ nT}$$

#### Polar Wander Model

**Velocity**:
$$\vec{v}_{pole}(t) = \frac{d\vec{r}_{pole}}{dt}$$

Current North Magnetic Pole:
- Velocity: ~55 km/year (accelerating)
- Acceleration: ~0.5 km/year²

**Trajectory Prediction** (short-term):
$$\vec{r}(t) = \vec{r}_0 + \vec{v}_0 t + \frac{1}{2}\vec{a}t^2$$

**Note**: Long-term prediction unreliable (chaotic core dynamics)

#### Reversal Probability

**Poisson Process Model**:
$$P(t) = 1 - e^{-\lambda t}$$

Where $\lambda = 1/\bar{T}$ and $\bar{T}$ = mean interval between reversals (~250,000 years)

**Current** ($t = 780,000$ years since last):
$$P = 1 - e^{-780000/250000} = 0.959$$

**Interpretation**: 96% cumulative probability, BUT reversals are memoryless (past doesn't constrain future).

**Better Model**: Include field strength as covariate
$$\lambda(B) = \lambda_0 e^{-\beta B}$$

Lower field strength → higher reversal probability

---

## Time Series Analysis

### Trend Detection

**Linear Regression**:
$$y = \alpha + \beta t + \epsilon$$

- $y$ = measured value
- $t$ = time
- $\beta$ = trend (change per unit time)
- $\epsilon$ = error term

**Significance Test**: $p < 0.05$ for $\beta \neq 0$

### Periodicity Detection

**Fourier Transform**:
$$F(\omega) = \int_{-\infty}^{\infty} f(t) e^{-i\omega t} dt$$

**Power Spectral Density**: Identifies dominant frequencies

**Application**: 
- Extinction events (test for ~26 Myr cycle)
- Earthquake sequences (aftershock patterns)
- Magnetic field variations (solar cycle influence)

### Change Point Detection

**CUSUM Method**:
$$S_t = \max(0, S_{t-1} + x_t - \mu - k)$$

Alarm when $S_t > h$ (threshold)

**Application**: Detect acceleration in seismicity or pole movement

---

## Spatial Analysis

### Clustering Detection

**Nearest Neighbor Analysis**:
$$R = \frac{\bar{d}_{observed}}{\bar{d}_{random}}$$

Where $\bar{d}_{random} = \frac{1}{2\sqrt{\lambda}}$ and $\lambda$ = point density

- $R < 1$: Clustered
- $R = 1$: Random
- $R > 1$: Regular/dispersed

**Application**: Ancient sites correlation with magnetic anomalies

### Spatial Correlation

**Moran's I**:
$$I = \frac{N}{W}\frac{\sum_i \sum_j w_{ij}(x_i - \bar{x})(x_j - \bar{x})}{\sum_i (x_i - \bar{x})^2}$$

- $w_{ij}$ = spatial weight (1 if neighbors, 0 otherwise)
- $W = \sum_i \sum_j w_{ij}$

**Test**: $p < 0.05$ indicates significant spatial autocorrelation

---

## Multi-Threat Integration

### Combined Probability

**Independent Events**:
$$P(A \cup B) = P(A) + P(B) - P(A)P(B)$$

**Example**: Probability of either Cascadia OR San Andreas in 30 years:
$$P = 0.15 + 0.60 - 0.15 \times 0.60 = 0.66 = 66\%$$

### Cascading Failures

**Conditional Probability**:
$$P(B|A) = \frac{P(A \cap B)}{P(A)}$$

**Example**: If Cascadia ruptures, probability of triggered San Andreas:
- $P(Cascadia) = 0.15$
- $P(San Andreas | Cascadia) = 0.05$ (stress transfer)
- $P(both) = 0.15 \times 0.05 = 0.0075$

### Systemic Risk

**Network Model**: Threats as nodes, interactions as edges

**Critical Threshold**: Fraction of nodes that must fail to trigger cascade

$$p_c = \frac{\langle k \rangle}{\langle k^2 \rangle}$$

Where $\langle k \rangle$ = mean degree, $\langle k^2 \rangle$ = second moment of degree distribution

---

## Validation and Calibration

### Backtesting

**Method**: Apply model to historical period with known outcome

**Metrics**:
1. **Accuracy**: $\frac{TP + TN}{Total}$
2. **Precision**: $\frac{TP}{TP + FP}$
3. **Recall**: $\frac{TP}{TP + FN}$

Where TP = true positive, TN = true negative, FP = false positive, FN = false negative

### Calibration Plot

Plot predicted probability vs. observed frequency:
- Perfect calibration: diagonal line
- Over-confident: curve above diagonal
- Under-confident: curve below diagonal

### Information Criteria

**Akaike Information Criterion**:
$$AIC = 2k - 2\ln(L)$$

- $k$ = number of parameters
- $L$ = likelihood

Lower AIC = better model (penalizes complexity)

---

## Sensitivity Analysis

### Parameter Variation

For model $R(p_1, p_2, ..., p_n)$, vary each parameter:

$$\frac{\partial R}{\partial p_i} \approx \frac{R(p_i + \Delta p_i) - R(p_i)}{\Delta p_i}$$

**Sensitivity Index**:
$$S_i = \frac{\partial R}{\partial p_i} \times \frac{p_i}{R}$$

Larger $|S_i|$ = more sensitive to parameter $p_i$

### Monte Carlo Simulation

1. Define probability distributions for uncertain parameters
2. Sample parameters randomly (10,000+ iterations)
3. Calculate $R$ for each sample
4. Report distribution of $R$ (mean, 90% confidence interval)

**Python Example**:
```python
import numpy as np

# Uncertain parameters
P = np.random.uniform(0.1, 0.3, 10000)
I = np.random.normal(7, 1, 10000)
M = np.random.beta(2, 5, 10000)

# Risk calculation
R = P * I * (1 - M)

# Results
print(f"Risk: {np.mean(R):.2f} ± {np.std(R):.2f}")
print(f"90% CI: [{np.percentile(R, 5):.2f}, {np.percentile(R, 95):.2f}]")
```

---

## Decision Theory

### Expected Utility

$$EU(action) = \sum_i P(outcome_i) \times U(outcome_i)$$

Where $U$ = utility (negative for costs, positive for benefits)

**Example**: Earthquake retrofit decision
- Cost of retrofit: $C$
- Probability of earthquake: $P$
- Damage without retrofit: $D$
- Damage with retrofit: $d < D$

**Expected utility of retrofit**:
$$EU_{retrofit} = -C - P \times d$$

**Expected utility of no action**:
$$EU_{no\ action} = -P \times D$$

**Decision**: Retrofit if $EU_{retrofit} > EU_{no\ action}$

Simplifies to: Retrofit if $C < P(D - d)$

---

## Communication of Uncertainty

### Verbal Equivalents

IPCC-style probability language:

| Probability | Verbal Description |
|-------------|-------------------|
| >99% | Virtually certain |
| 90-99% | Extremely likely |
| 66-90% | Likely |
| 33-66% | About as likely as not |
| 10-33% | Unlikely |
| 1-10% | Very unlikely |
| <1% | Exceptionally unlikely |

**Use**: "Cascadia megathrust in next 30 years is unlikely (10-15%)"

### Confidence Levels

Report parameter estimates with confidence intervals:
- 68% CI (±1σ): Common in science
- 90% CI: Regulatory standards
- 95% CI (±2σ): Statistical significance threshold

---

## Data Quality Standards

### Minimum Requirements

For inclusion in threat assessment:
1. **Source**: Peer-reviewed or verified government data
2. **Recency**: <5 years old (unless historical data)
3. **Precision**: Measurement error quantified
4. **Reproducibility**: Methodology documented

### Data Grading

- **Grade A**: Multiple independent verifications, high precision
- **Grade B**: Single peer-reviewed source, good precision
- **Grade C**: Expert estimate, moderate uncertainty
- **Grade D**: Anecdotal, high uncertainty (use only if no better data)

**Policy**: Grade D data requires disclaimer, cannot drive critical decisions

---

## Model Limitations and Caveats

### Known Issues

1. **Black Swans**: Models based on past data miss unprecedented events
2. **Non-stationarity**: Climate change alters baseline probabilities
3. **Complexity**: Interactions may be non-linear (models assume linear)
4. **Cognitive Biases**: Expert elicitation subject to anchoring, availability bias

### Best Practices

- **Ensemble modeling**: Use multiple independent models, compare
- **Regular updates**: Quarterly review, annual re-calibration
- **Transparency**: Document all assumptions
- **Humility**: Wide confidence intervals better than false precision

**Quote to remember**: "All models are wrong, but some are useful." - George Box

---

## Mathematical Tools Reference

### Software Recommendations

1. **Python**:
   - `numpy`, `scipy`: Numerical computation
   - `pandas`: Data handling
   - `matplotlib`, `seaborn`: Visualization
   - `scikit-learn`: Machine learning
   - `pymc3`: Bayesian analysis

2. **R**:
   - Base R: Statistical computing
   - `ggplot2`: Visualization
   - `spatstat`: Spatial statistics

3. **MATLAB**:
   - Signal processing
   - Differential equations

### Online Calculators

- Earthquake probability: USGS HayWired
- Population growth: Interactive simulations
- Risk matrices: Various templates

---

## Case Study: Worked Example

### Threat: Saber-Toothed Cat De-Extinction

**Step 1: Estimate Probability**
- Technical feasibility: 0.3 (expert estimate, Grade C)
- Timeline: 30-50 years
- 30-year probability: 0.3 × (30/40) = 0.225

**Step 2: Estimate Impact**
- Human deaths if escaped: 0-10 per year (depends on location)
- Livestock losses: High
- Ecological disruption: Medium
- Overall impact: 7/10

**Step 3: Estimate Mitigation**
- Containment technology: Good (modern zoos contain big cats)
- Regulatory framework: Moderate (developing)
- Mitigation capability: 0.7

**Step 4: Calculate Risk**
$$R = 0.225 \times 7 \times (1 - 0.7) = 0.47$$

**Interpretation**: Low-medium risk (current estimate)

**Step 5: Sensitivity Analysis**
Most sensitive to $P$ (technical feasibility) and $M$ (containment).

**Step 6: Uncertainty**
Using Monte Carlo (P ~ Uniform(0.2, 0.4), I ~ Normal(7, 1), M ~ Beta(2, 3)):
- Mean R: 0.53 ± 0.18
- 90% CI: [0.25, 0.85]

**Step 7: Recommendation**
Monitor research progress quarterly. If $P$ exceeds 0.5, develop strict containment regulations.

---

## Conclusion

Mathematical rigor in threat assessment:
1. Forces explicit assumptions
2. Enables comparison across diverse threats
3. Quantifies uncertainty
4. Supports decision-making

**All THREAT-CLASS-X analyses should reference this framework and document deviations.**

---

*Last Updated: December 2025*
*Framework Review: Annual*
