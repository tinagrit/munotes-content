![[Tutorial 3 - Questions .pdf]]

## Q1

| Work hours | Total Product | Average Product<br>$\dfrac{\text{total product}}{\text{work hour}}$ | Marginal Product<br>$\dfrac{\Delta\text{ total product}}{\Delta\text{ work hour}}$ |
| ---------- | ------------- | ------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| 1          | 20            | 20                                                                  | 20                                                                                 |
| 2          | 38            | 19                                                                  | 18                                                                                 |
| 3          | 54            | 18                                                                  | 16                                                                                 |
| 4          | 68            | 17                                                                  | 14                                                                                 |
| 5          | 80            | 16                                                                  | 12                                                                                 |
| 6          | 90            | 15                                                                  | 10                                                                                 |
| 7          | 98            | 14                                                                  | 8                                                                                  |
| 8          | 104           | 13                                                                  | 6                                                                                  |
| 9          | 108           | 12                                                                  | 4                                                                                  |
| 10         | 110           | 11                                                                  | 2                                                                                  |
```desmos-graph
left=0; right=12;
top=120; bottom=0;

---
(0,0)|red
(1,20)|red
(2,38)|red
(3,54)|red
(4,68)|red
(5,80)|red
(6,90)|red
(7,98)|red
(8,104)|red
(9,108)|red
(10,110)|red
```

If Max values his leisure as **$15/hour**, he would compare the cost of marginal product. This means that juggling after hour 3 is not worth it anymore.


## Q2

$\displaystyle f(x)=100\cdot x^{\frac{1}{2}}$

| Peasants | Total Product | Average Product<br>$\dfrac{\text{total product}}{\text{peasant}}$ | Marginal Product<br>$\dfrac{\Delta\text{ total product}}{\Delta\text{ peasant}}$ |
| -------- | ------------- | ----------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| 100      | 1,000.00      | 10.00                                                             | 10.00                                                                            |
| 200      | 1,414.21      | 7.07                                                              | 4.14                                                                             |
| 300      | 1,732.05      | 5.77                                                              | 3.18                                                                             |
| 400      | 2,000.00      | 5.00                                                              | 2.68                                                                             |
| 500      | 2,236.07      | 4.47                                                              | 2.36                                                                             |
| 600      | 2,449.49      | 4.08                                                              | 2.13                                                                             |
| 700      | 2,645.75      | 3.78                                                              | 1.96                                                                             |
| 800      | 2,828.43      | 3.53                                                              | 1.83                                                                             |
| 900      | 3,000.00      | 3.33                                                              | 1.71                                                                             |
| 1000     | 3,162.28      | 3.16                                                              | 1.62                                                                             |
```desmos-graph
left=0; right=1100;
top=3478; bottom=0;

---
100*\sqrt{x}|x<1000|red

```

If each peasant needs 5 to survive, then $f(x)\geq5x$

```desmos-graph
left=0; right=1100;
top=3478; bottom=0;

---
f(x)=100*\sqrt{x}|x<1000|red
y>5x|y<f(x)|red
y=5x|y<f(x)|blue
y=5x|y>f(x)|dashed|blue

```


When productivity is increased by 50%:
```desmos-graph
left=0; right=1100;
top=5500; bottom=0;

---
f(x)=150*\sqrt{x}|x<1000|red
y>5x|y<f(x)|red
y=5x|y<f(x)|blue
y=5x|y>f(x)|dashed|blue

```
