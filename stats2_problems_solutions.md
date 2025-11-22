# STATS 2 Quiz 2: Best Problems with Detailed Solutions & Examples

---

## PROBLEM SET 1: Joint Distributions (PMF)

### Problem 1.1: Joint PMF Table (Discrete Random Variables)

**Question:**
The joint probability mass function of two discrete random variables X and Y is given by:

| X\Y | 0 | 1 | 2 |
|-----|-------|-------|-------|
| 0   | 1/12  | 1/6   | 1/12  |
| 1   | 1/6   | 1/4   | 1/6   |
| 2   | 1/12  | 1/6   | 1/12  |

(a) Find the marginal PMF of X and Y
(b) Are X and Y independent? Justify your answer.
(c) Calculate E[X], E[Y], and Cov(X, Y)

---

**DETAILED SOLUTION:**

**Part (a): Finding Marginal PMFs**

For marginal PMF of X, sum across rows (Y values):
```
P_X(0) = P(X=0, Y=0) + P(X=0, Y=1) + P(X=0, Y=2)
       = 1/12 + 1/6 + 1/12
       = 1/12 + 2/12 + 1/12 = 4/12 = 1/3

P_X(1) = P(X=1, Y=0) + P(X=1, Y=1) + P(X=1, Y=2)
       = 1/6 + 1/4 + 1/6
       = 2/12 + 3/12 + 2/12 = 7/12

P_X(2) = P(X=2, Y=0) + P(X=2, Y=1) + P(X=2, Y=2)
       = 1/12 + 1/6 + 1/12
       = 1/12 + 2/12 + 1/12 = 4/12 = 1/3
```

**Marginal PMF of X:**
```
P_X(0) = 1/3, P_X(1) = 7/12, P_X(2) = 1/3
```

For marginal PMF of Y, sum down columns (X values):
```
P_Y(0) = P(X=0, Y=0) + P(X=1, Y=0) + P(X=2, Y=0)
       = 1/12 + 1/6 + 1/12
       = 1/12 + 2/12 + 1/12 = 4/12 = 1/3

P_Y(1) = P(X=0, Y=1) + P(X=1, Y=1) + P(X=2, Y=1)
       = 1/6 + 1/4 + 1/6
       = 2/12 + 3/12 + 2/12 = 7/12

P_Y(2) = P(X=0, Y=2) + P(X=1, Y=2) + P(X=2, Y=2)
       = 1/12 + 1/6 + 1/12
       = 1/12 + 2/12 + 1/12 = 4/12 = 1/3
```

**Marginal PMF of Y:**
```
P_Y(0) = 1/3, P_Y(1) = 7/12, P_Y(2) = 1/3
```

---

**Part (b): Testing Independence**

For X and Y to be independent: P(X=x, Y=y) = P_X(x) × P_Y(y) for all x, y

Check at (X=0, Y=0):
```
P(X=0, Y=0) = 1/12
P_X(0) × P_Y(0) = 1/3 × 1/3 = 1/9 ≈ 0.111

1/12 ≈ 0.083 ≠ 1/9
```

**Conclusion: X and Y are NOT independent** because the product of marginals does not equal the joint probability.

---

**Part (c): Calculate E[X], E[Y], and Cov(X, Y)**

**Calculating E[X]:**
```
E[X] = ∑_x x × P_X(x)
     = 0 × (1/3) + 1 × (7/12) + 2 × (1/3)
     = 0 + 7/12 + 8/12
     = 15/12 = 5/4
```

**Calculating E[Y]:**
```
E[Y] = ∑_y y × P_Y(y)
     = 0 × (1/3) + 1 × (7/12) + 2 × (1/3)
     = 0 + 7/12 + 8/12
     = 15/12 = 5/4
```

**Calculating E[XY]:**
```
E[XY] = ∑_x ∑_y xy × P(X=x, Y=y)

E[XY] = 0×0×(1/12) + 0×1×(1/6) + 0×2×(1/12)
      + 1×0×(1/6) + 1×1×(1/4) + 1×2×(1/6)
      + 2×0×(1/12) + 2×1×(1/6) + 2×2×(1/12)
      
      = 0 + 0 + 0 + 0 + 1/4 + 2/6 + 0 + 2/6 + 4/12
      = 1/4 + 1/3 + 1/3 + 1/3
      = 3/12 + 4/12 + 4/12 + 4/12 = 15/12 = 5/4

Wait, let me recalculate more carefully:
      = 0 + 0 + 0 + 0 + 1/4 + 2/6 + 0 + 2/6 + 4/12
      = 1/4 + 1/3 + 1/3 + 1/3
      = 3/12 + 4/12 + 4/12 + 4/12 = 15/12 = 5/4
```

**Calculating Cov(X, Y):**
```
Cov(X, Y) = E[XY] - E[X]×E[Y]
          = 5/4 - (5/4)×(5/4)
          = 5/4 - 25/16
          = 20/16 - 25/16
          = -5/16
```

**Answer: Cov(X, Y) = -5/16** (Negative covariance indicates inverse relationship)

---

## PROBLEM SET 2: Joint PDF (Continuous)

### Problem 2.1: Uniform Distribution Over a Region

**Question:**
Let X and Y be uniformly distributed over the region D, where D is defined as:
- Region 1: 0 ≤ x ≤ 1, 0 ≤ y ≤ 1 (Square)
- Region 2: 1 ≤ x ≤ 2, 0 ≤ y ≤ 0.5 (Rectangle)

(a) Find the joint PDF f(x, y)
(b) Find the marginal PDFs f_X(x) and f_Y(y)
(c) Are X and Y independent?

---

**DETAILED SOLUTION:**

**Part (a): Finding the Joint PDF**

First, calculate the area of region D:
```
Area(Region 1) = 1 × 1 = 1
Area(Region 2) = 1 × 0.5 = 0.5
Area(D) = 1 + 0.5 = 1.5
```

For uniform distribution: f(x,y) = 1/Area(D)

```
         | 1/1.5 = 2/3,  if (x,y) ∈ Region 1
f(x,y) = | 1/1.5 = 2/3,  if (x,y) ∈ Region 2
         | 0,             otherwise
```

**Or more explicitly:**
```
         | 2/3,  if 0 ≤ x ≤ 1 and 0 ≤ y ≤ 1
f(x,y) = | 2/3,  if 1 ≤ x ≤ 2 and 0 ≤ y ≤ 0.5
         | 0,    otherwise
```

---

**Part (b): Finding Marginal PDFs**

**Marginal PDF of X:**

For 0 ≤ x ≤ 1:
```
f_X(x) = ∫₀¹ f(x,y) dy = ∫₀¹ (2/3) dy = (2/3)×[y]₀¹ = 2/3
```

For 1 ≤ x ≤ 2:
```
f_X(x) = ∫₀^0.5 f(x,y) dy = ∫₀^0.5 (2/3) dy = (2/3)×[y]₀^0.5 = 1/3
```

**Therefore:**
```
        | 2/3,  if 0 ≤ x ≤ 1
f_X(x) = | 1/3,  if 1 ≤ x ≤ 2
        | 0,    otherwise
```

**Marginal PDF of Y:**

For 0 ≤ y ≤ 0.5:
```
f_Y(y) = ∫₀¹ f(x,y) dx + ∫₁² f(x,y) dx
       = ∫₀¹ (2/3) dx + ∫₁² (2/3) dx
       = (2/3)×1 + (2/3)×1
       = 2/3 + 2/3 = 4/3
```

For 0.5 < y ≤ 1:
```
f_Y(y) = ∫₀¹ f(x,y) dx = ∫₀¹ (2/3) dx = 2/3
```

**Therefore:**
```
        | 4/3,  if 0 ≤ y ≤ 0.5
f_Y(y) = | 2/3,  if 0.5 < y ≤ 1
        | 0,    otherwise
```

---

**Part (c): Testing Independence**

Check if f(x,y) = f_X(x) × f_Y(y):

For (x,y) in Region 1 (0 ≤ x ≤ 1, 0 ≤ y ≤ 0.5):
```
f(x,y) = 2/3
f_X(x) × f_Y(y) = (2/3) × (4/3) = 8/9 ≠ 2/3
```

**Conclusion: X and Y are NOT independent** because the product of marginals does not equal the joint PDF everywhere.

---

## PROBLEM SET 3: Covariance and Correlation

### Problem 3.1: Calculate Covariance and Correlation

**Question:**
Given two random variables with the following joint distribution:

| X\Y | 0   | 1   |
|-----|-----|-----|
| -1  | 1/4 | 1/4 |
| 1   | 1/4 | 1/4 |

Calculate:
(a) E[X] and E[Y]
(b) Cov(X, Y)
(c) Correlation coefficient ρ(X, Y)

---

**DETAILED SOLUTION:**

**Part (a): Calculate E[X] and E[Y]**

First, find marginal distributions:
```
P_X(-1) = P(X=-1, Y=0) + P(X=-1, Y=1) = 1/4 + 1/4 = 1/2
P_X(1) = P(X=1, Y=0) + P(X=1, Y=1) = 1/4 + 1/4 = 1/2

P_Y(0) = P(X=-1, Y=0) + P(X=1, Y=0) = 1/4 + 1/4 = 1/2
P_Y(1) = P(X=-1, Y=1) + P(X=1, Y=1) = 1/4 + 1/4 = 1/2
```

Calculate expectations:
```
E[X] = (-1)×(1/2) + (1)×(1/2) = -1/2 + 1/2 = 0
E[Y] = (0)×(1/2) + (1)×(1/2) = 0 + 1/2 = 1/2
```

---

**Part (b): Calculate Cov(X, Y)**

First calculate E[XY]:
```
E[XY] = (-1)×(0)×(1/4) + (-1)×(1)×(1/4) + (1)×(0)×(1/4) + (1)×(1)×(1/4)
      = 0 - 1/4 + 0 + 1/4
      = 0
```

Using the formula:
```
Cov(X, Y) = E[XY] - E[X]×E[Y]
          = 0 - (0)×(1/2)
          = 0
```

**Answer: Cov(X, Y) = 0** (No covariance, but this doesn't mean independence!)

---

**Part (c): Calculate Correlation ρ(X, Y)**

Since Cov(X, Y) = 0:
```
ρ(X, Y) = Cov(X, Y) / (σ_X × σ_Y) = 0 / (σ_X × σ_Y) = 0
```

**Answer: ρ(X, Y) = 0**

**Important Note:** Even though covariance is 0, X and Y are NOT independent! Let's verify:
```
P(X=-1, Y=0) = 1/4
P_X(-1) × P_Y(0) = 1/2 × 1/2 = 1/4 ✓

P(X=-1, Y=1) = 1/4
P_X(-1) × P_Y(1) = 1/2 × 1/2 = 1/4 ✓

Actually, they ARE independent!
```

**Correction:** In this case, X and Y ARE independent with zero covariance.

---

## PROBLEM SET 4: Sampling and Linearity of Expectation

### Problem 4.1: Sample Mean Distribution

**Question:**
A random sample of size n = 10 is taken from a population with mean μ = 20 and standard deviation σ = 5. Let X₁, X₂, ..., X₁₀ be the sample values.

(a) What is E[X₁ + X₂ + ... + X₁₀]?
(b) If the sample values are independent, what is Var(X₁ + X₂ + ... + X₁₀)?
(c) What is E[X̄] where X̄ = (X₁ + X₂ + ... + X₁₀)/10?

---

**DETAILED SOLUTION:**

**Part (a): Calculate E[X₁ + X₂ + ... + X₁₀]**

Using **Linearity of Expectation** (holds even without independence):
```
E[X₁ + X₂ + ... + X₁₀] = E[X₁] + E[X₂] + ... + E[X₁₀]
                        = 10 × E[X] (since each sample comes from same distribution)
                        = 10 × μ
                        = 10 × 20
                        = 200
```

---

**Part (b): Calculate Var(X₁ + X₂ + ... + X₁₀)**

Since samples are independent:
```
Var(X₁ + X₂ + ... + X₁₀) = Var(X₁) + Var(X₂) + ... + Var(X₁₀)
                          = 10 × Var(X)
                          = 10 × σ²
                          = 10 × 5²
                          = 10 × 25
                          = 250
```

---

**Part (c): Calculate E[X̄]**

```
E[X̄] = E[(X₁ + X₂ + ... + X₁₀)/10]
      = (1/10) × E[X₁ + X₂ + ... + X₁₀]
      = (1/10) × 200
      = 20
```

**Answer: E[X̄] = 20** (Sample mean is unbiased estimator of population mean)

---

## PROBLEM SET 5: Mixed Continuous Distribution

### Problem 5.2: Exponential Distribution Example

**Question:**
Let X and Y be independent random variables where:
- X ~ Exponential(λ = 1/2)
- Y ~ Exponential(λ = 1/2)

Calculate:
(a) The joint PDF f(x, y)
(b) P(X > 2, Y > 1)
(c) E[X + Y] and Var(X + Y)

---

**DETAILED SOLUTION:**

**Part (a): Joint PDF**

For Exponential distribution: f(x) = λe^(-λx) for x ≥ 0

Since X and Y are independent:
```
f(x,y) = f_X(x) × f_Y(y)
       = (1/2)e^(-x/2) × (1/2)e^(-y/2)
       = (1/4)e^(-(x+y)/2),  for x ≥ 0, y ≥ 0
```

---

**Part (b): Calculate P(X > 2, Y > 1)**

```
P(X > 2, Y > 1) = ∫₂^∞ ∫₁^∞ (1/4)e^(-(x+y)/2) dy dx

Since X and Y are independent:
= P(X > 2) × P(Y > 1)

For Exponential(λ): P(X > a) = e^(-λa)

P(X > 2) = e^(-1/2 × 2) = e^(-1)
P(Y > 1) = e^(-1/2 × 1) = e^(-1/2)

P(X > 2, Y > 1) = e^(-1) × e^(-1/2) = e^(-3/2) ≈ 0.223
```

---

**Part (c): Calculate E[X + Y] and Var(X + Y)**

For Exponential(λ): E[X] = 1/λ and Var(X) = 1/λ²

```
E[X] = 1/(1/2) = 2
E[Y] = 1/(1/2) = 2

E[X + Y] = E[X] + E[Y] = 2 + 2 = 4
```

```
Var(X) = 1/(1/2)² = 1/(1/4) = 4
Var(Y) = 1/(1/2)² = 4

Since X and Y are independent: Cov(X,Y) = 0

Var(X + Y) = Var(X) + Var(Y) = 4 + 4 = 8
```

---

## EXAM-TIPS & COMMON MISTAKES

| Mistake | Why It's Wrong | Correct Approach |
|---------|----------------|-----------------|
| Cov = 0 means independent | Covariance only measures linear dependence | Check P(X,Y) = P(X)P(Y) |
| Forgot 2×Cov in variance | Standard formula includes the cross term | Var(X+Y) = Var(X) + Var(Y) + 2Cov |
| Wrong integration limits | Limits define the support of the distribution | Carefully trace region D boundaries |
| Forgot to normalize PDF | PDFs must integrate to 1 | Always verify ∫∫ f(x,y) = 1 |
| Used discrete formula for continuous | Different integration vs summation | Check if problem says "discrete" or "continuous" |

---

## PRACTICE QUESTION PATTERNS FOR QUIZ 2

**Pattern 1: Joint PMF → Marginals → Independence**
- Given: Table of joint probabilities
- Find: P_X(x), P_Y(y), and verify independence

**Pattern 2: Joint PDF Over Region**
- Given: Region D and "uniform distribution"
- Find: f(x,y), f_X(x), f_Y(y)
- Calculate: Probabilities using double integration

**Pattern 3: Covariance and Correlation**
- Given: Data or joint distribution
- Find: E[X], E[Y], Cov(X,Y), ρ(X,Y)

**Pattern 4: Functions of Random Variables**
- Given: X, Y and their distribution
- Find: E[g(X,Y)] using LotUS

**Pattern 5: Sampling Applications**
- Given: Population parameters and sample size
- Find: E[Σ X_i], Var(Σ X_i), E[X̄]

---

**All formulas are in the study guide. Practice these 5 problems first!**
