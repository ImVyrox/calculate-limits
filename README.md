# Lua Calculus Toolkit for Calculators

Welcome! This repository features custom Lua scripts designed for graphic calculators to streamline and automate multi-step mathematical procedures.

🚀 Overview
This toolkit was originally developed to assist with Calculus 2 exams by breaking down complex problems into manageable, step-by-step solutions. Feel free to use it, test it, and contribute to its development!

> ⚠️ **IMPORTANT (WIP):** This script is currently a work in progress. It is not 100% complete and may contain logic or runtime errors. Use it as a guide, but always double-check your results!

---

## 🛠️ Features

The toolkit currently implements several basic mathematical functions designed to output step-by-step procedures rather than just the final answer. It is optimized to work with **CAS (Computer Algebra System)** engines to process variables analytically:

| Function | Description | Status |
| :--- | :--- | :--- |
| **Algebraic Simplification** | Breaks down fractions and roots. | ⚠️ Beta |
| **Step-by-Step Derivatives** | Applies chain, product, and quotient rules. | ⚠️ Beta |
| **Multivariable Limits** | Evaluates $\lim_{(x,y) \to (0,0)} f(x,y)$ using 4 simultaneous paths (Axes, $y=mx$, $y=ax^2$, and Polares). | 🔄 Testing |
| **Basic Integration** | Handles standard anti-derivatives. | 🚧 WIP |

---

## 📐 Multivariable Limits Module

One of the core features of this toolkit is the **Simultaneous 4-Path Limit Solver**. Instead of giving a simple numerical approximation, the script forces the CAS engine to evaluate the limit through four distinct analytical trajectories to test for existence:

*   **a) Ejes Coordenados:** Evaluates successive/reiterated limits (first $x \to 0$, then $y \to 0$ and vice versa).
*   **b) Rectas ($y = mx$):** Substitutes the linear family to analyze dependence on the slope $m$.
*   **c) Parábolas ($y = ax^2$):** Substitutes the quadratic family to detect higher-degree dependencies.
*   **d) Coordenadas Polares:** Performs the symbolic substitution $x = r \cos(t)$, $y = r \sin(t)$ and simplifies $r \to 0^+$ analytically.

### Sample Linear Output (TI-Nspire CX CAS Compatible)
Since calculator screens often have limited rendering capabilities for complex LaTeX, the script formats the output into clean, continuous algebraic text strings:

```text
d) Polares:
x = r*cos(t), y = r*sin(t)

Sustitucion:
(r*cos(t))^2 / ((r*cos(t)) + (r*sin(t)))

Simplificacion:
r * cos(t)^2 / (cos(t) + sin(t)) -> 0

Resultado:
lim = 0
