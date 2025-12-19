# Contributing to THREAT-CLASS-X

Thank you for your interest in contributing to the THREAT-CLASS-X threat analysis repository. This guide outlines how to submit observations, data, and analyses.

---

## What We're Looking For

### Threat Observations
- **New locations** with unusual properties
- **Magnetic field measurements** from verified instruments
- **Ancient site discoveries** with documentation
- **Tectonic/seismic data** from verified sources
- **De-extinction research** updates from peer-reviewed sources
- **Google Earth findings** with coordinates and screenshots

### Analysis Contributions
- **Mathematical models** for threat probability
- **Data visualizations** of threat patterns
- **Statistical analyses** of correlations
- **Peer-reviewed research** summaries
- **Model improvements** with validation

### Documentation
- **Updates** to existing threat assessments
- **New threat categories** with supporting evidence
- **Corrections** to existing data
- **Better organization** of information

---

## Submission Guidelines

### For New Location Observations

Include the following information:

#### Required
1. **Precise Coordinates**: Use decimal degrees (e.g., 37.2353°N, 115.8113°W)
2. **Date of Observation**: When you found/observed this (YYYY-MM-DD)
3. **Description**: Clear description of the unusual feature
4. **Category**: Which threat category does this belong to?
   - Tectonic/geological
   - Magnetic anomaly
   - Ancient site
   - Google Earth anomaly
   - Extinct creature discovery
   - Other (specify)

#### Recommended
5. **Visual Evidence**: Screenshots, photos, or satellite imagery links
6. **Verification Status**: 
   - Confirmed (multiple independent sources)
   - Unverified (single observation)
   - Disputed (conflicting reports)
7. **Source Citations**: Where you found this information
8. **Measurements**: Quantitative data if available (magnetic field strength, dimensions, etc.)
9. **Access Restrictions**: Is the site restricted, remote, or accessible?

#### Example Submission

```markdown
**Location Name**: Mystery Peak, Antarctica
**Coordinates**: 75.0128°S, 0.0813°E
**Date Observed**: 2025-12-15
**Category**: Google Earth Anomaly / Ancient Site
**Description**: Pyramidal mountain formation with unusual geometric angles visible in satellite imagery.
**Verification Status**: Unverified (satellite imagery only, no ground verification)
**Visual Evidence**: [Google Earth link] or [Screenshot]
**Measurements**: 
  - Height: ~400m (from elevation data)
  - Base: ~300m × 300m (approximate)
  - Slope angles: 45-50° on visible faces
**Source**: Google Earth imagery dated 2024-03
**Access**: Extremely remote, no research stations nearby, requires Antarctic expedition
**Notes**: Natural erosion could produce this shape, but geometric regularity is notable.
```

---

### For Magnetic Field Data

If reporting magnetic field measurements:

#### Required
1. **Location**: Precise coordinates
2. **Measurement**: Total field intensity (nT - nanoteslas)
3. **Equipment**: Magnetometer make/model
4. **Calibration**: Date of last calibration
5. **Date/Time**: When measured (UTC preferred)

#### Recommended
6. **Background Expected**: What does IGRF (International Geomagnetic Reference Field) model predict for this location?
7. **Anomaly Magnitude**: Deviation from expected (measurement - IGRF)
8. **Multiple Readings**: Standard deviation if multiple measurements taken
9. **Environmental Conditions**: Solar activity (Kp index), nearby metal objects, power lines

#### Example

```markdown
**Location**: Patomskiy Crater area
**Coordinates**: 59.2835°N, 116.5847°E
**Measurement**: 52,340 nT ± 45 nT (n=5 readings)
**Equipment**: GSM-19T Overhauser Magnetometer
**Calibration**: 2025-11-01
**Date/Time**: 2025-12-10 14:30 UTC
**IGRF Prediction**: 52,100 nT
**Anomaly**: +240 nT
**Conditions**: Kp=2 (quiet), no obvious metal nearby, ~50m from nearest equipment
**Notes**: Consistent with reported anomaly in this area.
```

---

### For Mathematical Models

If proposing a new model or improvement:

#### Required
1. **Model Description**: What are you modeling?
2. **Equations**: Mathematical formulation (use LaTeX: `$$equation$$`)
3. **Parameters**: Define all variables
4. **Assumptions**: What are you assuming?
5. **Validation**: Test against historical data if possible

#### Recommended
6. **Code Implementation**: Python, R, or MATLAB code
7. **Sensitivity Analysis**: How sensitive to parameter changes?
8. **Uncertainty Quantification**: Confidence intervals
9. **Comparison**: How does it compare to existing models?

#### Example

```markdown
## Improved Earthquake Recurrence Model

**Purpose**: Better estimate time-dependent earthquake probability accounting for stress accumulation.

**Model**:
$$P(t) = 1 - \exp\left(-\int_0^t \lambda(s) ds\right)$$

Where:
$$\lambda(t) = \lambda_0 \left(1 + \alpha \frac{\Delta \sigma(t)}{\sigma_c}\right)$$

**Parameters**:
- $\lambda_0$ = background rate (from Gutenberg-Richter)
- $\alpha$ = stress sensitivity (default 2.0)
- $\Delta \sigma(t)$ = accumulated stress (from GPS)
- $\sigma_c$ = critical stress for failure

**Assumptions**:
1. Stress accumulates linearly between events
2. Complete stress drop at rupture
3. Homogeneous fault properties

**Validation**: 
Tested on Parkfield, CA segment (regular M6 events).
Prediction accuracy: 72% vs 65% for time-independent Poisson.

**Code**: [Link to Python implementation]
```

---

### For Research Updates

When citing new research:

#### Required
1. **Citation**: Full reference (authors, year, journal, DOI)
2. **Summary**: 2-3 sentence summary of findings
3. **Relevance**: How does this affect threat assessment?
4. **Grade**: Data quality (A, B, C, D - see below)

#### Example

```markdown
**Citation**: Smith, J. et al. (2024). "Accelerated magnetic pole migration and reversal indicators." *Nature Geoscience*, 17(3), 234-241. DOI: 10.1038/s41561-024-01234-5

**Summary**: Analysis of ESA Swarm data shows North Magnetic Pole acceleration has increased to 60 km/year (up from 55 km/year in 2020). New modeling suggests 20% probability of reversal onset within 500 years, higher than previous 10% estimate.

**Relevance**: Increases magnetic field reversal threat probability. Update to data/magnetic-anomalies/GLOBAL-MAP.md recommended.

**Grade**: A (peer-reviewed, multiple satellite confirmation, robust statistical analysis)
```

---

## Data Quality Standards

### Grading System

**Grade A**: Highest quality
- Multiple independent verifications
- Peer-reviewed publication or government data
- High precision measurements
- Reproducible methodology
- Recent (<2 years old)

**Grade B**: Good quality
- Single peer-reviewed source
- Good measurement precision
- Documented methodology
- Moderately recent (<5 years old)

**Grade C**: Acceptable with caveats
- Expert estimate or preliminary report
- Moderate uncertainty
- May be older data (5-10 years)
- Requires disclaimer

**Grade D**: Use with extreme caution
- Anecdotal or unverified
- High uncertainty
- Single observation
- Cannot drive critical decisions
- Must include disclaimer

### What NOT to Submit

❌ **Conspiracy theories without evidence**
- Unfalsifiable claims
- "Secret government projects" without documentation
- Anecdotal stories without coordinates or data

❌ **Numerology or pattern-matching without statistical validation**
- "I found the number 33 appears 33 times" (coincidence, not analysis)
- Arbitrary symbol-to-number assignments
- Cherry-picked data to fit predetermined conclusion

❌ **Plagiarized content**
- Always cite sources
- Don't copy-paste from other sites without attribution

❌ **Pseudoscience**
- Claims violating established physics (e.g., perpetual motion)
- "Ancient aliens" explanations without exploring conventional explanations first
- Paranormal claims without rigorous testing

---

## How to Submit

### Option 1: GitHub Pull Request (Preferred)

1. Fork the repository
2. Create a new branch: `git checkout -b new-threat-location`
3. Add your content to the appropriate file:
   - Magnetic anomalies → `data/magnetic-anomalies/GLOBAL-MAP.md`
   - Ancient sites → `data/ancient-sites/CATALOG.md`
   - Google Earth findings → `data/google-earth-anomalies/LOCATIONS.md`
   - Extinct creatures → `data/extinct-creatures/DE-EXTINCTION-TIMELINE.md`
   - Tectonic data → `data/tectonic-data/PLATE-MOVEMENTS.md`
4. Follow the existing format in the file
5. Commit: `git commit -m "Add [Location Name] observation"`
6. Push: `git push origin new-threat-location`
7. Open a Pull Request with description

### Option 2: GitHub Issue

If you're not familiar with Git:

1. Go to the repository's Issues tab
2. Click "New Issue"
3. Title: "[Category] New Observation: [Location Name]"
4. Body: Include all required information from submission guidelines above
5. Submit issue

Maintainers will review and add to appropriate file if approved.

### Option 3: Discussion

For general questions or proposals:

1. Use GitHub Discussions
2. Post in relevant category (Ideas, Q&A, etc.)

---

## Review Process

### Submission Review

Maintainers will:
1. Verify coordinates are correct
2. Check data quality grade
3. Validate sources if provided
4. Assess relevance to threat analysis
5. Check for duplicates

**Timeline**: Most submissions reviewed within 1 week.

### Acceptance Criteria

✅ **Will be accepted**:
- Accurate, verifiable data
- Follows submission guidelines
- Relevant to threat analysis
- Properly cited sources
- Grade B or higher (Grade C with disclaimer)

⚠️ **May need revision**:
- Missing required information
- Unclear description
- Poor data quality (Grade D) - may accept with strong disclaimer
- Needs better formatting

❌ **Will be rejected**:
- Duplicate information
- Violates data quality standards
- Pseudoscience or unfalsifiable claims
- Plagiarized content
- Off-topic

---

## Mathematical and Statistical Standards

All mathematical models and statistical analyses must:

1. **Use proper notation**
   - Define all variables
   - Use standard mathematical symbols
   - LaTeX formatting for equations: `$$E = mc^2$$`

2. **Include uncertainty**
   - Report confidence intervals
   - Document error propagation
   - Monte Carlo for complex models

3. **Validate when possible**
   - Backtest on historical data
   - Cross-validation for predictive models
   - Sensitivity analysis for parameters

4. **Follow framework**
   - Refer to [MATHEMATICAL-FRAMEWORK.md](MATHEMATICAL-FRAMEWORK.md)
   - Use standard risk formula: $R = P \times I \times (1-M)$
   - Document deviations from framework

---

## Code Contributions

If submitting code (Python, R, MATLAB, etc.):

### Requirements
- **Comments**: Document what code does
- **Inputs/Outputs**: Clearly defined
- **Dependencies**: List required libraries
- **Example**: Include sample usage
- **License**: Must be compatible (MIT, Apache, GPL, public domain)

### Python Example Structure

```python
"""
Earthquake probability calculator using time-dependent model.

Dependencies: numpy, scipy
Author: [Your name]
Date: 2025-12-19
"""

import numpy as np
from scipy.stats import poisson

def earthquake_probability(time_since_last, mean_recurrence, stress_ratio=1.0):
    """
    Calculate earthquake probability using Poisson process.
    
    Parameters:
    -----------
    time_since_last : float
        Years since last major earthquake
    mean_recurrence : float
        Mean time between earthquakes (years)
    stress_ratio : float, optional
        Stress accumulation factor (default 1.0)
        
    Returns:
    --------
    probability : float
        Probability of earthquake in next year
        
    Example:
    --------
    >>> p = earthquake_probability(325, 400, 1.2)
    >>> print(f"Annual probability: {p:.4f}")
    Annual probability: 0.0124
    """
    lambda_rate = stress_ratio / mean_recurrence
    probability = 1 - np.exp(-lambda_rate)
    return probability

if __name__ == "__main__":
    # Example: Cascadia subduction zone
    p_cascadia = earthquake_probability(325, 400, 1.1)
    print(f"Cascadia annual probability: {p_cascadia:.4%}")
```

---

## Attribution

Contributors will be acknowledged in:
- Commit history (automatic)
- Contributors section (major contributions)
- Inline citations where appropriate

**You retain**: Copyright to your original contributions
**You grant**: Right to use, modify, and distribute as part of this repository

---

## Questions?

- **General questions**: GitHub Discussions
- **Bug reports**: GitHub Issues
- **Security concerns**: [Private security contact if needed]

---

## Code of Conduct

### Expected Behavior
- **Respectful**: Treat all contributors with respect
- **Scientific**: Base arguments on evidence and logic
- **Constructive**: Offer solutions, not just criticism
- **Honest**: Cite sources, acknowledge uncertainty

### Unacceptable
- Harassment, discrimination, or personal attacks
- Intentional misinformation or data fabrication
- Spam or off-topic promotion
- Violation of scientific integrity

**Violations**: May result in contribution rejection or ban from repository.

---

## Getting Started Checklist

Ready to contribute? Here's your checklist:

- [ ] Read this contributing guide
- [ ] Review [MATHEMATICAL-FRAMEWORK.md](MATHEMATICAL-FRAMEWORK.md)
- [ ] Check existing data files for format examples
- [ ] Gather your data/observation with required information
- [ ] Choose submission method (PR, Issue, or Discussion)
- [ ] Submit!

---

**Thank you for helping document and analyze potential future threats!**

*Last Updated: December 2025*
