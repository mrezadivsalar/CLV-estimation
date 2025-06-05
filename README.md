# Customer Lifetime Value (CLV) Calculator

This repository provides a reproducible, data-driven implementation of a Customer Lifetime Value (CLV) calculation workflow, as described in the accompanying CLV calculation report. The approach requires no arbitrary parameter assumptions—each step is based on observed transaction and marketing‐contact data to derive an expected, discounted revenue per customer minus acquisition costs.

---

## Table of Contents

- [Overview](#overview)  
- [Features](#features)  
- [Prerequisites](#prerequisites)  


---

## Overview

This CLV Calculator implements a seven-step process to estimate the value of a customer over their entire relationship, including:

1. Estimating repeat purchase frequency per year.  
2. Converting an annual discount rate into a per-purchase discount factor.  
3. Sequencing each customer’s purchases to define a horizon.  
4. Computing mean order value at each transaction index.  
5. Estimating the conditional probability of repurchase at each transaction.  
6. Calculating average acquisition cost per customer from marketing touches.  
7. Summing discounted future revenues and subtracting acquisition cost to produce a single CLV figure.

This approach ensures that every parameter is driven by actual transaction and marketing data—no need to guess “average retention” or arbitrarily cap the horizon. A reference PDF describing the theory in detail is included in `/docs/CLV_calculation.pdf`.

---

## Features

- **Data-driven:** All inputs (frequency, mean order values, transition probabilities, acquisition costs) come directly from observed data.  
- **Flexible discounting:** Users supply an annual discount rate; the code automatically converts it to a per-purchase rate.  
- **Full transaction horizon:** Rather than truncating after a fixed number of years, the method sequences each customer’s purchase history to the maximum observed depth.  
- **Acquisition cost integration:** Counts of pre-purchase email and catalog touches are converted into an average acquisition cost.  
- **Modular codebase:** Each step of the calculation (frequency, Mₜ, rₜ, acquisition, discounting) is implemented as a separate, reusable function.  
- **Example dataset included:** A small anonymized transaction sample is provided to demonstrate end-to-end usage.

---

## Prerequisites

- Python **3.8+**  
- [pandas](https://pandas.pydata.org/) ≥ 1.2  
- [NumPy](https://numpy.org/) ≥ 1.20  
- [matplotlib](https://matplotlib.org/) (optional, for plotting intermediate results)  
- [Jupyter Notebook](https://jupyter.org/) (recommended for interactive exploration)  

You can install dependencies via `pip`:

```bash
pip install pandas numpy matplotlib
