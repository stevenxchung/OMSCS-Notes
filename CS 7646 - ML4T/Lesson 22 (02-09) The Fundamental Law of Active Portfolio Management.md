# Lesson 22

In this lesson we examine how investment performance relates to investor skill and breadth (number of investments). We will see that diversification is necessary if investors are uncertain.

## IR, IC, And Breadth

The fundamental law of active portfolio management relies on three key terms:

1. **IR (information ratio)** - investor skill which may be determined by the Sharpe ratio of $\alpha$ calculated as: `IR = mean(alpha_port[t]) / std(alpha_port[t])` we may also determine `alpha_port[t] = return_port[t] - (beta_port * return_market[t])`
2. **IC (information coefficient)** - correlation of investor forecast to returns
3. **BE (breadth)** - number of trading opportunities per year

## Grinold's Fundamental Law

**Grinold's fundamental law** is defined as:

$IR = IC * \sqrt{BR}\\$

Where $IR$ is information ratio (the performance of a portfolio), $IC$ is information coefficient (investor skill) and $BR$ is trading opportunities available to an investor (breadth). For more information see [Grinold's Fundamental Law](https://newfrontieradvisors.com/media/1376/fundamental-law-june-2017.pdf).

## Coin-Flip Casino: Risk 1

Why is it less risky to place 1000 individual bets on each respective table instead of placing 1000 bets on a single table? Given our coin-flip casino scenario with 51% chance to win and 49% chance to lose:

- Single bet has a 49% chance of losing all our money
- Multi-bet (placing 1000 individual bets on each respective table) has a $0.49^{1000}$ (essentially 0% chance) of losing all our money

## Coin-Flip Casino: Risk 2

Additionally, examining the standard deviation of the two scenarios:

- Single bet has a standard deviation of about 31.62 (outcome is much more volatile and unpredictable)
- Multi-bet has a standard deviation of 1 (we either win or lose a coin flip for each game)

## Coin-Flip Casino: Observations

It turns out that we may use Grinold's fundamental law to determine the number of bets it would take for the single bet performance to equal the multi-bet performance:

$SR_{multi-bet} = SR_{single-bet}  * \sqrt{Bets}\\$

Where $SR$ is the Sharpe ratio of either strategies. Therefore, we would need to play the single bet strategy 1000 more times to equal the performance of the multi-bet strategy.

## Coin-Flip Casino: Lessons

In terms of investing, we may take away three lessons from the coin-flip casino activity:

1. Higher $\alpha$ generates higher Sharpe ratio
2. More execution opportunities increases the Sharpe ratio
3. Sharpe ratio grows according to $\sqrt{breadth}$

## Section Quizzes

### Which Bet Is Better Quiz

_Given the information from lecture on betting on coin flips, which bet is better_? One token in each of the 1000 tables (diversifying) so all our money is not lost with any subsequent coin toss.

### Reward Quiz

_Given that a single bet with 1000 coin flips has an expected return of $20, calculate the expected return for 1000 individual bets with 1 coin flip each_ The expected return is still $20 (`1000 * (0.51 * 1 + 0.49 * -1) = 20`).

### Reward/Risk Quiz

_Fill in the reward vs. risk for a multi-bet scenario_: `20 / 1 = 20`

### Simons Vs. Buffet Quiz

_Given the following scenario (provided), how many trades must Simons execute_? 120M trades to be equivalent to Buffet's IR.
