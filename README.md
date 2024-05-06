# Problem
Source: from Brilliant's May rundown email.

![image](./crops.png)

It’s Spring—the perfect time to start a farm. You have $100 to get your operation off the ground, and can plant any of the crops below that you can afford, at any time. 

| Crop        | Cost | Selling Price | Time to grow |
| ----------- | ---- | ------------- | ------------ |
| Peas        | $10  | $12           | 2 months     |
| Potatoes    | $5   | $8            | 4 months     |
| Raspberries | $15  | $25           | 4 months     |
| Saffron     | $175 | $500          | 6 months     |

**In 5 years, what's the most money you can make selling your crops?**

# Provided Solution
Set up a linear program to approximate solution.

These are the variables we have control over:

$\text{peas}_i = \text{number of peas to plant in the beginning of month } i$ 

$\text{potatoes}_i = \text{number of potatoes to plant in the beginning of month } i$ 

$\text{raspberries}_i = \text{number of raspberries to plant in the beginning of month } i$ 

$\text{saffron}_i = \text{number of saffron to plant in the beginning of month } i$ 

If we have the following variables, then the balance would be easy to calculate:
$\text{grown peas}_i = \text{number of peas to sell in the beginning of month } i$ 
$\text{grown potatoes}_i = \text{number of potatoes to sell in the beginning of month } i$ 
$\text{grown raspberries}_i = \text{number of raspberries to grow in the beginning of month } i$ 
$\text{grow saffron}_i = \text{number of saffron to sell in the beginning of month } i$ 

Because balance, if defined as follows, is as simple as:
$$
\begin{align*}
\text{balance}_i &= \text{balance at the beginning of month } i \text{ after purchasing and selling the crops} \\
&= \text{balance}_{i-1} - \text{cost of purchasing crops this month} + \text{revenue from selling crops this month}
\end{align*}
$$
Then we maximize for $balance_{61}$ and apply non-negativity constraints on all the variables.

[CVXPY](https://www.cvxpy.org/) and [a spreadsheet solver](https://help.libreoffice.org/latest/en-US/text/scalc/01/solver.html) were used to solve this optimization problem with very similar answers.

Additionally, the provided answers from the spreadsheet solver constrained the purchases from the first month to be integers. This change the optimal value from ~$300k to $200k, suggesting that the linear program may not be a good approximation of the problem.

# Next Steps
- Constrain to integers
- Sensitivity analysis


