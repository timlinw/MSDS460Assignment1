# MSDS460Assignment1
Our decision variables are the food items: Mixed fruit yogurt, chicken noodle soup, cobb salad, protein shake, Clif protein bar. The objective function is based on the costs of each food item, we will be minimizing this function because we want the least cost while satisfying the eighth nutritional constraints. 

Nutritional Requirements, Daily
Sodium-Maximum-5,000 milligrams (mg)

Energy-Minimum-2,000 Calories (kilocalories, kcal)

Protein-Minimum-50 grams (g)

Vitamin D-Minimum-20 micrograms (mcg)

Calcium-Minimum-1,300 milligrams (mg)

Iron-Minimum-18 milligrams (mg)

Potassium-Minimum-4,700 milligrams (mg)

Constraints Based on my food items
Sodium Constraint
65 * x1 + 260 * x2 + 680*x3 + 1360*x4 + 230*x5 <= 5000*7
Calorie Constraint
140*x1 + 170*x2 + 350*x3 + 240*x4 + 260*x5 >= 2000*7
Protein Constraint
11*x1 + 26*x2 + 14*x3 + 21*x4+ 10*x5 >=50*7
Vitamin D Constraint
0*x1 + 20*x2 + .04*20*x3 + 0*x4 + 0*x5 >=20*7
Calcium Constraint
.10 * 1300*x1 + .6*1300*x2 + .06*1300*x3 + 40*x4 + 40*x5 >=1300*7
Iron Constraint
0*x1 +.1*18*x2 + .08*18*x3 + 1.6*x4 + 2*x5 >=18*7
Potassium Constraint
.04*4700*x1 + 870*x2 + .08*4700*x3 + 570*x4 + 267*x5 >=4700*7
Where x1 is yogurt, x2 protein shake, x3 cobb salad, x4 chicken noodle soup, x5 clif bar
We want to spend the least amount of money that we need to while still following each of these constraints.
