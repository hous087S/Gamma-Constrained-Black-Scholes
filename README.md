# Black–Scholes Equation with Gamma Constraint

Numerical solution of the Black–Scholes PDE under a curvature (Gamma) constraint on the option price, implemented as part of the *Numerical Methods for PDEs in Finance* course at ENSTA Paris / IP Paris.

**Authors:** Houssem Bouabid & Tingjia Zhang · **Supervisor:** Alessandro Zilio

---

## Problem

Classical Black–Scholes assumes unconstrained hedging. This project considers a market where the option's curvature is capped:

$$s \, v_{ss}(t,s) \leq \Gamma, \quad \Gamma > 0$$

This leads to a **nonlinear variational inequality** rather than a linear PDE, solved via finite differences and Howard's policy iteration.

---

## Structure

```
├── gamma_constrained_BS.ipynb   # Full numerical implementation
└── gamma_constrained_B&S.pdf    # Project report
```

---

## Methods

| Question | Content |
|---|---|
| **Q1** | Analytic free-boundary solution for the Gamma-constrained put envelope $\hat{g}$; Newton verification |
| **Q2** | Finite-difference solver (implicit Euler / Crank–Nicolson / Rannacher) with Howard policy iteration |
| **Q3** | Comparison of the constrained price $v$ against the classical Black–Scholes benchmark $u$ |
| **Q4** | Extension to the **Leland (1985)** transaction-cost model via a modified diffusion coefficient |

---

## Key Results

- The Gamma-constrained envelope $\hat{g}$ is computed analytically with explicit free boundaries $\alpha$, $\beta$ and verified numerically (Newton convergence to machine precision).
- Howard's algorithm solves the variational inequality efficiently at each time step using a tridiagonal policy-evaluation step.
- For a **put payoff**, the constraint premium $v - u$ is small ($\sim 10^{-3}$); for a **triangle payoff**, it reaches $\sim 0.23$, consistent with the sharper terminal curvature.
- The **Leland model** shows that increasing the Leland number $\text{Le}$ inflates option prices monotonically as transaction costs dominate.

---

## Parameters (all experiments)

```
K = 100,  σ = 0.1,  r = 0.1,  T = 0.1,  Γ = 1
```

---

## Dependencies

```bash
pip install numpy scipy matplotlib
```

Run the notebook top-to-bottom — no additional setup required.
