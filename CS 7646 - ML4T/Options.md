# Options

In this lecture we will examine **exchange-traded stock options** (commonly referred to as options).

## What Is An Option

An option is a _contract_ which gives the buyer the right (but not obligation) to buy or sell the underlying stock at a specific price (or strike price) on or before the expiration date. Note that in Europe, options can only be executed on the expiration date.

When buying _call_ options we are buying the right to _buy_ a stock at a certain price. Conversely, when buying _put_ options we are buying the right to _sell_ a stock at a certain price.

Buying _calls_ or _puts_ have the following scenarios (referring to the profit/loss chart in lecture):

- **Calls**:
  - Best-case: max profit is theoretically unlimited after the breakeven profit/loss point
  - Worst-case: max loss is limited to the premium paid
- **Puts**:
  - Best-case: max profit is limited to a share price of $0.00
  - Worst-case: max loss is limited to the premium paid

However, buying an options contract is not the only feature of options, we can also _write_ (or sell) an options contract.

When selling a _call_ option we are selling the right for someone to _buy_ a stock at a certain price. Conversely, when selling a _put_ option we are selling the right to _sell_ a stock at a certain price.

How do the profit/loss curves transform for selling options? They are flipped on the x-axis:

- **Calls**:
  - Best-case: max profit is limited to the premium paid
  - Worst-case: max loss is theoretically unlimited after the breakeven profit/loss point
- **Puts**:
  - Best-case: max profit is limited to the premium paid
  - Worst-case: max loss is limited to a share price of $0.00

If the best-case scenarios are capped at a premium then why would we want to sell options? Because most of the options bought are **not** exercised (around 90%), meaning that in most cases, the seller will pocket the premium.

## Pros And Cons Of Buying (Simple) Options

Some pros and cons of buying _call_ options include:

- **Pros**:
  - Can't lose more than the premium paid up-front
  - Leverage since we can get most upside potential and cap downside to premium paid
- **Cons**:
  - Expiration dates
  - The premium is lost money
  - You don't own the stock unless contract is executed

## Option Prices

Why are some option contracts priced differently? They are priced based on _intrinsic value_ and _time value_ of the option.

In options the **intrinsic value** is the difference between the option strike price and the underlying spot price for an _in-the-money_ option. The terms _in-the-money_ and _out-of-the-money_ correspond to:

- **In-the-money**: an option which has a non-negative intrinsic value since money can be made immediately buy buying that option and exercising it
- **Out-of-the-money**: an option which has a negative intrinsic value since money **cannot** be made immediately buy buying that option and exercising it

Option traders also care about the **time value** which is the excess premium cost of an option beyond its intrinsic value, attributed to time-to-expiration. Generally, the further an option is from expiration, the greater the time value.

Consequently, if traders typically do not want to hold on to options for too long as there is a **time decay** (also known as $\theta$, the rate at which an option is currently losing it's time value) on the value of the option.

Options prices at any given moment may be determined by the [BSM (Black-Scholes Model)](https://www.investopedia.com/terms/b/blackscholes.asp). Note that the standard BSM is used to price European options.

## Option Strategies

The power of options is that we can combine multiple options to create a trading strategy. Below are some option strategies worth mentioning.

**Covered call** is where a trader buys a stock and writes a call on that same stock. There are three possibilities of interest for this strategy:

1. Stock ends above strike price:
   - We no longer own the stock
   - $Profit = strike - purchase + premium$
2. Stock ends up but below strike price:
   - Option not exercised
   - Made money on the stock and still have it
   - $Profit = current - purchase + premium$
3. Stock ends down:
   - Option not exercised and still own stock
   - Premium partially offsets loss
   - $Loss = current - purchase + premium$

A similar strategy to the covered call is a **married put** whereby an investor buys a stock and buys a put. This strategy offers hedging against downside moves as follows:

- If stock goes up we lose the premium
- If the stock goes down then losses are capped since the put gains at the same rate as the stock loses value

Why go with a married put strategy over selling a stock? Because selling a stock could have tax implications (capital gain/loss) where selling options do not.

What if a security has low volatility and is expected to flat line for a while? We can use the _butterfly_ strategy.

**Butterfly** is a strategy for when the market goes sideways. It works as follows:

1. Write two calls as close to the current price of the security (one above above and below the current price)
2. Then buy two calls a price between the two previous calls which we may use as a _bracket_

The benefits of using the butterfly strategy is that our losses are capped at the first two calls we bought and used as a _bracket_. We may adjust the bracket by buying calls further away from the current security price but we will have a pay a premium as a result.
