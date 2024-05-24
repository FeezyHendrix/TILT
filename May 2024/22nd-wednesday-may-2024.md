A binomial random walk
This is mathematical model that describes a path consisting of series of random steps. 

It is a type of random walk where each step is determined by a binomial process. At each step, there are two possible outcomes, typically up and down. 


Xt+1​=Xt​+u with probability 𝑝p \\


𝑋𝑡+1=𝑋𝑡+𝑑Xt+1​=Xt​+d with probability 1−𝑝1−p \\


If 𝑢=1 and 𝑑 =−1, the process becomes:


Gamblers Ruin Problem:

This is a classical problem in probability theory and statistics that describes a scenario where a gamble with a finite amount of wealth participates in a series of bets. The problem investigates the likelihood of the gambler going bankrupt or reach a certain wealth goal. 

Let say:

Initial Wealth: k

In each round of betting which is a binomial random walk where the gambler either win or lose. 

The probability of winning a single bet is p while the probability of loosing a bet is q = 1 - p

The objective:
Gambler keeps betting until k = 0 or k = N which is target wealth. 


What is the probability of ruin
 
P(q)  if p = q  = 0.5 thus a fair game
Then P(q) = N - K / N

if (p != q) thus a biased game where the house always wins then the probability of ruin is

$$


If ( p \neq q ):


P_k = \frac{1 - \left( \frac{q}{p} \right)^k}{1 - \left( \frac{q}{p} \right)^N} 

$$
$$
If ( p = q = 0.5 ):


P_k = \frac{N - k}{N} 

$$

What is the expected number of bets before the gambler propers or goes bankrupt?

For a fair game (p = q = 0.5)

$$
Ek​=k(N−k)
$$
For a biased game: (p != q)

$$
Ek​=1−(pq​)N1−(pq​)k​⋅(q−p1​)⋅(1−(pq​)N−k)
$$