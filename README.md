# ETHSF_univ3

84% rule for new LPs in Uniswap v3

TLDR: providing passive liquidity on Uniswap v3 in the range of +/- 84% from current price balances yield and risk.

The formula for capital efficiency improvement in uniswap between providing liquidity for the entire range (uni v2) versus a fixed range (uni v3) is given by:


$$ Capital Efficiency = \frac{1}{1-(\frac{P_a}{P_b})^\frac{1}{4}} $$


We modify this formula by making $P_a$ (lower price) and $P_b$ (upper price) move away from each other by an equal amount $x:

$$ P_a = 1-x ;  P_b = 1+x$$

This gives us: 


$$ f(x) = \frac{1}{1-(\frac{1-x}{1+x})^\frac{1}{4}} $$

Where $x$ can be viewed as a percent move in both directions (we are widening the price range).

If the price of a token is <span>$</span> 100 and $x$ is $1$ percent, then $P_a$ is offset to $99$ and $P_b$ is offset to $101$.<br>
If the price of a token is <span>$</span> 100 and $x$ is $20$ percent, then $P_a$ is offset to $80$ and $P_b$ is offset to $120$

When we graph this function with respect to $x$ from 10% to 100%, notice closely how it starts to drop off at the tail.

![efficiency_frontier](https://user-images.githubusercontent.com/111250982/200159784-0fe56693-d78a-49ad-bcae-1d8e5e66e54b.jpg)

Closer look at 40% to 100% range:

![efficiency_frontier2](https://user-images.githubusercontent.com/111250982/200159841-b95a40dd-a1b1-45d6-b6ea-0df6d5b60864.jpg)


As we widen the price range in which we provide liquidity, the slope of our capital efficiency rapidly drops (we have to deposit more and more dollars to get the same yield), it then starts to flatten after every increase in our range, but at 84% and beyond, we start to tip over. Looking at the behavior of the slope, we find the tipping point:

![slope](https://user-images.githubusercontent.com/111250982/200160039-2ba03e94-d630-4c93-a821-1471627e098a.png)


This means that, if we have to pick as wide a range as possible in uniswap v3 while not knowing what can happen to the price movement, and minimize rebalancing, +/- 84% allows us to use twice as little capital (or if you want to take more risk, it allows us to deploy the same capital, but double the yield).

The downside can be that the price can move +/- 84%. In order to counter that, it's best to pick tokens that correlate with one another (ETH/ENS, ETH/OP instead of ETH/USD).

The python code is used to query the uniswap subgraph in GraphQL and extract the price range necessary to provide liquidity in uni v3 pool. I provide liquidity to ETH/OP and ETH/MATIC and register an ENS domain, conveniently named "84percent.eth" for demo purposes.

Conclusion:

From the standpoint of a public service, if you're an LP and are worried about risk, want to use as little money as possible (be capital efficient), and have no clue where the price of your token may diverge, then +/- 84% could be the optimal range.



