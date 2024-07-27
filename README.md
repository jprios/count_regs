# Regression Combinations Generator

This project provides a Python function `count_regs` that generates all possible regression formulas given a dependent variable and a list of independent variables. It also calculates and prints the number of possible combinations for each number of independent variables and the total number of generated regression formulas.

## Features

- **Generate Regression Formulas:** Generates all possible regression formulas given a list of independent variables.
- **Combination Count:** Calculates and prints the number of combinations for each subset of independent variables.
- **Extra Regressions:** Optionally includes a specified number of extra regressions in the total count.

## Requirements

- Python 3.x

## Installation

No installation is required for this script. Simply ensure you have Python 3.x installed on your system.

## Usage

### Function Definition

```python
import math
from itertools import combinations

def count_regs(y, xvars, n_extras=None):
    """
    Generates all possible regression formulas and prints the number of combinations for each subset of independent variables.

    Parameters:
    y (str): The dependent variable.
    xvars (list of str): A list of independent variables.
    n_extras (int, optional): The number of extra regressions to include in the total count.

    Returns:
    None
    """
    # Lista de fórmulas
    fmla_list = []
    total_combinations = 0  # Inicialize total_combinations com 0

    for k in range(1, len(xvars) + 1):
        combs = combinations(xvars, k)
        for x in combs:
            regr = " + ".join(x)
            fmla = f"{y} ~ {regr}"
            if regr:
                fmla = f"{y} ~ {regr}"
                fmla_list.append(fmla)

    combinations_sum = sum([math.comb(len(xvars), k) for k in range(1, len(xvars) + 1)])

    for k in range(1, len(xvars) + 1):
        combinations_count = math.comb(len(xvars), k)
        total_combinations += combinations_count
        print(f"Combinations for k = {k}: {combinations_count}")
        
    print("-" * 40)
    print(f"Number of vars to combine: {len(xvars)}")
    print(f"Number of extra vars: {n_extras}")
    print("-" * 40)
    if n_extras != None:
        print(f"Number of regressions generated: {len(fmla_list) + n_extras}")
        print(f"Sum of possible combinations: {combinations_sum + n_extras}")
    else:
        print(f"Number of regressions generated: {len(fmla_list)}")
        print(f"Sum of possible combinations: {combinations_sum}")


