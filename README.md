# ETHSF_univ3

84% rule for new LPs in Uniswap v3

TLDR: providing passive liquidity on Uniswap v3 in the range of +/- 84% from current price can balance yield and risk.

The formula for capital efficiency improvement in uniswap between providing liquidity for the entire range (uni v2) versus a fixed range (uni v3) is given by:


$$ Capital Efficiency = \frac{1}{1-(\frac{P_a}{P_b})^\frac{1}{4}} $$


We modify this formula by making $P_a$ (lower price) and $P_b$ (upper price) move away from each other by an equal amount $x:

$$ P_a = 1-x ;  P_b = 1+x$$

This gives us: 


$$ f(x) = \frac{1}{1-(\frac{1-x}{1+x})^\frac{1}{4}} $$

Where $x$ can be viewed as a percent move in both directions (we are widening the price range).

If the price of a token is <span>$</span> 100 and $x$ is $1$, then $P_a$ is offset to $99$ and $P_b$ is offset to $101$.<br>
If the price of a token is <span>$</span> 100 and $x$ is $20$, then $P_a$ is offset to $80$ and $P_b$ is offset to $120$

When we graph this function from 1% to 100% we find an interesting point at a range of +/- 84%

As we widen the price range in which we provide liquidity, the slope of our capital efficiency rapidly drops (we have to deposit more dollars to get the same yield), it then starts to flatten after every increase, but at 84% and beyond, we start to tip over.

This means that, if we have to pick as wide a range as possible in uniswap v3 while not knowing what can happen to the price movement, +/- 84% allows us to use twice as little capital (or if you want to take more risk, it allows us to deploy the same capital, but double the yield).

The downside can be that the price can move +/- 84%, in order to counter that, it's best to pick tokens that correlate with one another (ETH/ENS, ETH/OP instead of ETH/USD).

