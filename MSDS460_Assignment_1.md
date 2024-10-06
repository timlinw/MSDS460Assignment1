```python
#pip install pulp
```

    Collecting pulp
      Downloading PuLP-2.9.0-py3-none-any.whl.metadata (5.4 kB)
    Downloading PuLP-2.9.0-py3-none-any.whl (17.7 MB)
    [2K   [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m17.7/17.7 MB[0m [31m21.3 MB/s[0m eta [36m0:00:00[0m00:01[0m00:01[0m
    [?25hInstalling collected packages: pulp
    Successfully installed pulp-2.9.0
    Note: you may need to restart the kernel to use updated packages.



```python
from pulp import *
```


```python
lp = LpProblem("Diet_Problem", LpMinimize)
```


```python
x1 = LpVariable(name="Chobani_Yogurt", lowBound=0)
x2 = LpVariable(name="Protein Shake", lowBound=0)
x3 = LpVariable(name="Cobb Salad", lowBound=0)
x4 = LpVariable(name="Chicken Noodle Soup", lowBound=0)
x5 = LpVariable(name="Clif Bar", lowBound=0)

```


```python
lp += 1.69 * x1 + 3.89 * x2 + 3.67 * x3 +6.49 *x4 +1.599*x5
```


```python
#sodium,5000mg
lp += 65 * x1 + 260 * x2 + 680*x3 + 1360*x4 + 230*x5 <= 5000*7
#energy/calories 2000 calories
lp += 140*x1 + 170*x2 + 350*x3 + 240*x4 + 260*x5 >= 2000*7
#protein, 50grams
lp += 11*x1 + 26*x2 + 14*x3 + 21*x4+ 10*x5 >=50*7
#vitamin d, 20 micrograms
lp += 0*x1 + 20*x2 + .04*20*x3 + 0*x4 + 0*x5 >=20*7
#calcium, 1300 mg
lp += .10 * 1300*x1 + .6*1300*x2 + .06*1300*x3 + 40*x4 + 40*x5 >=1300*7
#iron, 18 mg
lp += 0*x1 +.1*18*x2 + .08*18*x3 + 1.6*x4 + 2*x5 >=18*7
#potassium, 4700 mg
lp += .04*4700*x1 + 870*x2 + .08*4700*x3 + 570*x4 + 267*x5 >=4700*7
```


```python
status = lp.solve()
print("Status:", status)
```

    Welcome to the CBC MILP Solver 
    Version: 2.10.3 
    Build Date: Dec 15 2019 
    
    command line - /opt/anaconda3/lib/python3.12/site-packages/pulp/solverdir/cbc/osx/64/cbc /var/folders/p4/prvgygc14vd8rmhsv2qx4rxc0000gn/T/aeeb1ca1c65841aa96933dc38198859c-pulp.mps -timeMode elapsed -branch -printingOptions all -solution /var/folders/p4/prvgygc14vd8rmhsv2qx4rxc0000gn/T/aeeb1ca1c65841aa96933dc38198859c-pulp.sol (default strategy 1)
    At line 2 NAME          MODEL
    At line 3 ROWS
    At line 12 COLUMNS
    At line 49 RHS
    At line 57 BOUNDS
    At line 58 ENDATA
    Problem MODEL has 7 rows, 5 columns and 31 elements
    Coin0008I MODEL read with 0 errors
    Option for timeMode changed from cpu to elapsed
    Presolve 7 (0) rows, 5 (0) columns and 31 (0) elements
    0  Obj 0 Primal inf 330.26512 (6)
    4  Obj 163.31922
    Optimal - objective value 163.31922
    Optimal objective 163.3192155 - 4 iterations time 0.002
    Option for printingOptions changed from normal to all
    Total time (CPU seconds):       0.00   (Wallclock seconds):       0.01
    
    Status: 1



```python
for var in lp.variables():
    print(var, "=", value(var))
print("OPT = ", value(lp.objective))
```

    Chicken_Noodle_Soup = 0.0
    Chobani_Yogurt = 0.0
    Clif_Bar = 40.019057
    Cobb_Salad = 0.0
    Protein_Shake = 25.534381
    OPT =  163.319214233



```python
#https://www.target.com/p/core-power-chocolate-26g-protein-shake-14-fl-oz-bottle/-/A-78824043#lnk=sametab
#https://www.marianos.com/p/clif-bar-peanut-butter-banana-with-dark-chocolate-energy-bars/0072225206881
#https://www.marianos.com/p/kroger-cobb-salad-kit-for-one/0001111063065
#https://www.marianos.com/p/panera-bread-ready-to-heat-chicken-noodle-soup-cup/0007795869041?searchType=default_search
#https://www.marianos.com/p/chobani-mixed-berry-low-fat-greek-yogurt-cup/0081829001466?searchType=default_search

```


```python
lp = LpProblem("Diet_Problem", LpMinimize)
```


```python
x1 = LpVariable(name="Chobani_Yogurt", lowBound=1)
x2 = LpVariable(name="Protein Shake", lowBound=1)
x3 = LpVariable(name="Cobb Salad", lowBound=1)
x4 = LpVariable(name="Chicken Noodle Soup", lowBound=1)
x5 = LpVariable(name="Clif Bar", lowBound=1)
```


```python
lp += 1.69 * x1 + 3.89 * x2 + 3.67 * x3 +6.49 *x4 +1.599*x5
```


```python
#sodium,5000mg
lp += 65 * x1 + 260 * x2 + 680*x3 + 1360*x4 + 230*x5 <= 5000*7
#energy/calories 2000 calories
lp += 140*x1 + 170*x2 + 350*x3 + 240*x4 + 260*x5 >= 2000*7
#protein, 50grams
lp += 11*x1 + 26*x2 + 14*x3 + 21*x4+ 10*x5 >=50*7
#vitamin d, 20 micrograms
lp += 0*x1 + 20*x2 + .04*20*x3 + 0*x4 + 0*x5 >=20*7
#calcium, 1300 mg
lp += .10 * 1300*x1 + .6*1300*x2 + .06*1300*x3 + 40*x4 + 40*x5 >=1300*7
#iron, 18 mg
lp += 0*x1 +.1*18*x2 + .08*18*x3 + 1.6*x4 + 2*x5 >=18*7
#potassium, 4700 mg
lp += .04*4700*x1 + 870*x2 + .08*4700*x3 + 570*x4 + 267*x5 >=4700*7
```


```python
status = lp.solve()
print("Status:", status)

```

    Welcome to the CBC MILP Solver 
    Version: 2.10.3 
    Build Date: Dec 15 2019 
    
    command line - /opt/anaconda3/lib/python3.12/site-packages/pulp/solverdir/cbc/osx/64/cbc /var/folders/p4/prvgygc14vd8rmhsv2qx4rxc0000gn/T/769a64ef8504427682fbd3837eb929fc-pulp.mps -timeMode elapsed -branch -printingOptions all -solution /var/folders/p4/prvgygc14vd8rmhsv2qx4rxc0000gn/T/769a64ef8504427682fbd3837eb929fc-pulp.sol (default strategy 1)
    At line 2 NAME          MODEL
    At line 3 ROWS
    At line 12 COLUMNS
    At line 49 RHS
    At line 57 BOUNDS
    At line 63 ENDATA
    Problem MODEL has 7 rows, 5 columns and 31 elements
    Coin0008I MODEL read with 0 errors
    Option for timeMode changed from cpu to elapsed
    Presolve 7 (0) rows, 5 (0) columns and 31 (0) elements
    0  Obj 17.339 Primal inf 297.78499 (6)
    3  Obj 169.90461
    Optimal - objective value 169.90461
    Optimal objective 169.9046124 - 3 iterations time 0.002
    Option for printingOptions changed from normal to all
    Total time (CPU seconds):       0.00   (Wallclock seconds):       0.03
    
    Status: 1



```python
for var in lp.variables():
    print(var, "=", value(var))
print("OPT = ", value(lp.objective))
```

    Chicken_Noodle_Soup = 1.0
    Chobani_Yogurt = 1.0
    Clif_Bar = 39.539781
    Cobb_Salad = 1.0
    Protein_Shake = 24.378021
    OPT =  169.904611509



```python

```


```python

```
