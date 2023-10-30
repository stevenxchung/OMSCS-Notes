# Lesson 16

In this lesson we will examine how to evaluate a company and its worth.

## Why Company Value Matters

Company value matters if we are trying to determine the best time to sell stock. We could estimate the value of a company through their _true value_ by using the following metrics:

- **Intrinsic value**: the value of a company based on future dividends
- **Book value**: the value of all assets the company owns
- **Market cap**: the value of the stock on the market and shares outstanding

## The Value Of A Future Dollar

To calculate the value of a dollar we may use the following formula:

`PV = FV / (1 + IR) ** i`

Where `PV` is the present value, `FV` is the future value (payment at regular intervals), `IR` is the interest rate, and `i` is the time (usually years) into the future.

## Intrinsic Value

Generally, _interest_ and _discount_ rate are terms that refer to the same quantity, but are used to distinguish two slightly different use cases:

- **Interest rate**: is used with a given PV, to figure out what the FV would be
- **Discount rate**: is used when we have a known or desired FV, and want to compute the corresponding PV

Generally the discount rate has an _direct_ relationship with risk of a particular company (i.e., discount rate is lower if the company is less risky but higher if the company is more risky).

To determine the intrinsic value (`IV`) of a company we may use:

$IV = \sum_{i = 1}^{\infty} \frac{FV}{(1 + IR)^i} = FV/DR$

Where `DR` is the discount rate.

## Book Value

How do we calculate the book value of a company? We take the total assets (e.g., real estate) minus intangible assets (e.g., brand) and liabilities (e.g., loans). Note that we usually do **not** count intangible assets.

## Market Capitalization

Market cap is calculated by `market_cap = n_shares * price`.

## Why Information Affects Stock Price

News about a company could increase or decrease the intrinsic value of a company. Information may affect a company in the following ways:

- **Company-specific**: news that affects a specific company
- **Sector-specific**: news that affects a specific sector
- **Market-specific**: news that affects a specific market

## What Is A Company Worth Summary

Knowing what a company is worth will allow us to determine proper action. A hedge fund might evaluate the intrinsic value and market cap of a company to determine a buy or sell (_buy_ when intrinsic value is _high_ but prices are _low_ and _sell_ when intrinsic value is _low_ but prices are _high_).

Generally, the market cap of a particular company would not go below book value. Otherwise a predatory company would buy it and sell all assets at book value to pocket the difference.

## Section Quizzes

### What Is A Company Worth Quiz

_Given that a company can generate $1 every year, what is a company worth_? Between $10 and $25 depending on interest rates.

### The Balch Bond Quiz

_Rank the below options (given) from 1 to 3 where 1 is the most preferred and 3 the least. When comparing these different options, assume that they cost you the same today. Say, you have 80 cents to invest, and these are the 3 options you can get for that money_.

1. $1 right now
2. US government bond $1 in 1 year
3. Tucker Balch bond

### Intrinsic Value Quiz

_What's the intrinsic value given the following (provided)_? $50

### Compute Company Value Quiz

_Calculate the following for a company_:

1. _What is the book value given the following_? $80M
2. _What is the intrinsic value given the following_? $20M
3. _What is the market capitalization given the following_? $75M

### Would You Buy This Stock Quiz

_Given the following company values (provided), would you buy this stock_? Yes, since we can sell and profit $5M right away.
