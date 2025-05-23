![header-cheetah](https://user-images.githubusercontent.com/79997186/184224088-de4f3003-0c22-4a17-8cc7-b341b8e5b55d.png)

&nbsp;
&nbsp;
&nbsp;


## Introduction

This repository hosts the Alpaca Brokerage Plugin Integration with the QuantConnect LEAN Algorithmic Trading Engine. LEAN is a brokerage agnostic operating system for quantitative finance. Thanks to open-source plugins such as this [LEAN](https://github.com/QuantConnect/Lean) can route strategies to almost any market.

[LEAN](https://github.com/QuantConnect/Lean) is maintained primarily by [QuantConnect](https://www.quantconnect.com), a US based technology company hosting a cloud algorithmic trading platform. QuantConnect has successfully hosted more than 200,000 live algorithms since 2015, and trades more than $1B volume per month.


### About Alpaca

<p align="center">
<picture >
  <source media="(prefers-color-scheme: dark)" srcset="https://github.com/user-attachments/assets/5ae043e7-ee44-4fa4-820a-2d948ef9ad9d">
  <source media="(prefers-color-scheme: light)" srcset="https://github.com/user-attachments/assets/82d9657d-86a4-4c6c-acc2-efdf184a2026">
  <img alt="introduction" width="25%">
</picture>
<p>

[Alpaca](https://alpaca.markets/) was founded by Yoshi Yokokawa and Hitoshi Harada in 2015 as a database and machine learning company. In 2018, Alpaca Securities LLC (Alpaca Securities) became a registered US broker-dealer with the Financial Industry Regulatory Authority ([FINRA](https://www.finra.org/)) with the mission to "open financial services to everyone on the planet". In 2022, Alpaca Crypto LLC (Alpaca Crypto) became a registered Money Services Business (MSB) with the Financial Crimes Enforcement Network ([FinCEN](https://www.fincen.gov/)). Alpaca provides access to trading Equities, Options, and Crypto for clients in over 30 countries. Alpaca also delivers custody, clearing, execution, and billing on behalf of registered advisors.

For more information about the Alpaca brokerage, see the [QuantConnect-Alpaca Integration Page](https://www.quantconnect.com/docs/v2/our-platform/live-trading/brokerages/alpaca).

## Using the Brokerage Plugin
  
### Deploying Alpaca with VSCode User Interface

  You can deploy using a visual interface in the QuantConnect cloud. For instructions, see the [QuantConnect-Alpaca Integration Page](https://www.quantconnect.com/docs/v2/our-platform/live-trading/brokerages/alpaca). 
  
 ![alpaca-deployment](https://github.com/user-attachments/assets/6c21eb08-7185-4716-9ddb-6f18904e2ceb)

  In the QuantConnect Cloud Platform, you can harness the QuantConnect Live Data Feed, the Alpaca Live Data Feed, or both. For most users, this is substantially cheaper and easier than self-hosting.
  
### Deploying Alpaca with LEAN CLI

Follow these steps to start local live trading with the Alpaca brokerage:

1.  Open a terminal in your [CLI root directory](https://www.quantconnect.com/docs/v2/lean-cli/initialization/directory-structure#02-lean-init).
2.  Run `lean live "<projectName>"` to start a live deployment wizard for the project in `./<projectName>` and then enter the brokerage number.

	```
    $ lean live "My Project"
    Select a brokerage:
    1) Paper Trading
    2) Interactive Brokers
    3) Tradier
    4) OANDA
    5) Bitfinex
    6) Coinbase Advanced Trade
    7) Binance
    8) Zerodha
    9) Samco
    10) Terminal Link
    11) Trading Technologies
    12) Kraken
    13) TD Ameritrade
    14) Bybit
    15) TradeStation
    16) Alpaca 
    Enter an option: 16
	```


3.  In the browser window that automatically opens, click Allow.

    ```
    $ lean live "My Project"
    Please open the following URL in your browser to authorize the LEAN CLI.
    https://www.quantconnect.com/api/v2/live/auth0/authorize?brokerage=alpaca
    Will sleep 5 seconds and retry fetching authorization...
    ```

4.  Enter the environment to use.
    ```
    $ lean live "My Project"
    Live or Paper environment? (live, paper): live
    ```

5.  Enter the number of the live data provider(s) to use and then follow the steps required for the data connection.

    ```
    $ lean live "My Project"
    Select a data feed:
    1) Interactive Brokers
    2) Tradier
    3) Oanda
    4) Bitfinex
    5) Coinbase Advanced Trade
    6) Binance
    7) Zerodha
    8) Samco
    9) Terminal Link
    10) Trading Technologies
    11) Kraken
    12) TDAmeritrade
    13) IQFeed
    14) Polygon
    15) IEX
    16) CoinApi
    17) ThetaData
    18) Custom data only
    19) Bybit
    20) TradeStation
    21) Alpaca
    To enter multiple options, separate them with comma: 21
    ```

    If you select IQFeed, see [IQFeed](https://www.quantconnect.com/docs/v2/lean-cli/live-trading/other-data-feeds/iqfeed) for set up instructions.  
    If you select Polygon Data Feed, see [Polygon](https://www.quantconnect.com/docs/v2/lean-cli/live-trading/other-data-feeds/polygon) for set up instructions.

7.  In the browser window that automatically opens, click Allow.

    ```
    $ lean live "My Project"
    Please open the following URL in your browser to authorize the LEAN CLI.
    https://www.quantconnect.com/api/v2/live/auth0/authorize?brokerage=alpaca
    Will sleep 5 seconds and retry fetching authorization...
    ```

8.  Enter [your API key and API secret](https://www.quantconnect.com/docs/v2/cloud-platform/live-trading/brokerages/alpaca#02-Account-Types).
    ```
    $ lean live "My Project"
    Alpaca Api Key: PKEFXE36AR5OEG5K5KNQ
    Alpaca Api Secret: ****************************************
    ```

## Account Types

Alpaca supports cash and margin accounts.

## Order Types and Asset Classes

The following table describes the available order types for each asset class that our Alpaca integration supports.

| Order Type / Security Type | Equity | Equity Options | Crypto  |
|:--------------------------:|:------:|:--------------:|:-------:|
|         MarketOrder        |   Yes  |       Yes      |   Yes   |
|         LimitOrder         |   Yes  |       Yes      |   Yes   |
|       StopMarketOrder      |   Yes  |       Yes      |   Yes   |
|       StopLimitOrder       |   Yes  |       Yes      |   Yes   |
|        MarketOnOpen        |   Yes  |                |         |
|        MarketOnClose       |   Yes  |                |         |


## Downloading Data

For local deployment, the algorithm needs to download the following datasets:

- [US Equities Security Master](https://www.quantconnect.com/datasets/quantconnect-us-equity-security-master) provided by QuantConnect
- [US Equities](https://www.quantconnect.com/datasets/algoseek-us-equities)
- [US Coarse Universe](https://www.quantconnect.com/datasets/quantconnect-us-coarse-universe-constituents)
- [US Equity Options](https://www.quantconnect.com/datasets/algoseek-us-equity-options)
- Crypto (e.g. [Coinbase](https://www.quantconnect.com/datasets/coinbase-crypto-price-data))

## Brokerage Model

Lean models the brokerage behavior for backtesting purposes. The margin model is used in live trading to avoid placing orders that will be rejected due to insufficient buying power.

You can set the Brokerage Model with the following statements

    SetBrokerageModel(BrokerageName.Alpaca, AccountType.Cash);
    SetBrokerageModel(BrokerageName.Alpaca, AccountType.Margin);

[Read Documentation](https://www.quantconnect.com/docs/v2/writing-algorithms/reality-modeling/brokerages/supported-models/alpaca#01-Introduction)

### Fees

The Alpaca trading for Equity and Equity Options is commission-free. To view the Alpaca trading fees for Crypto, see the [Crypto Fees](https://docs.alpaca.markets/docs/crypto-fees) page on the Alpaca website. To view how we model their fees, see [Fees](https://www.quantconnect.com/docs/v2/writing-algorithms/reality-modeling/brokerages/supported-models/alpaca#06-Fees).

### Margin

We model buying power and margin calls to ensure your algorithm stays within the margin requirements.

[Read Documentation](https://www.quantconnect.com/docs/v2/our-platform/live-trading/brokerages/alpaca#07-Margin)

#### Buying Power

In the US, Alpaca allows up to 2x leverage on Equity trades for margin accounts. In other countries, Alpaca may offer different amounts of leverage. To figure out how much leverage you can access, check with your local legislation or contact an Alpaca representative. We model the US version of Alpaca leverage by default.

#### Margin Calls

Regulation T margin rules apply. When the amount of margin remaining in your portfolio drops below 5% of the total portfolio value, you receive a [warning](https://www.quantconnect.com/docs/v2/writing-algorithms/reality-modeling/margin-calls#08-Monitor-Margin-Call-Events). When the amount of margin remaining in your portfolio drops to zero or goes negative, the portfolio sorts the generated margin call orders by their unrealized profit and executes each order synchronously until your portfolio is within the margin requirements.

#### Pattern Day Trading

If all of the following statements are true, you are classified as a pattern day trader:

- You reside in the United States.
- You trade in a margin account.
- You execute 4+ intraday US Equity trades within 5 business days.
- Your intraday US Equity trades represent more than 6% of your total trades.

Pattern day traders must maintain a minimum equity of $25,000 in their margin account to continue trading. For more information about pattern day trading, see [Am I a Pattern Day Trader?](https://www.finra.org/investors/learn-to-invest/advanced-investing/day-trading-margin-requirements-know-rules) on the FINRA website.

The `PatternDayTradingMarginModel` doesn't enforce minimum equity rules and doesn't limit your trades, but it adjusts your available leverage based on the market state. During regular market hours, you can use up to 4x leverage. During extended market hours, you can use up to 2x leverage.

```
security.MarginModel = new PatternDayTradingMarginModel();
```

### Slippage

Orders through Alpaca do not experience slippage in backtests. In paper trading and live trading, your orders may experience slippage.

### Fills

We fill market orders immediately and completely in backtests. In live trading, if the quantity of your market orders exceeds the quantity available at the top of the order book, your orders are filled according to what is available in the order book.

### Settlements

If you trade with a margin account, trades settle immediately. If you trade with a cash account, Equity trades settle 2 days after the transaction date (T+2) and Option trades settle on the business day following the transaction (T+1).


### Deposits and Withdraws

You can deposit and withdraw cash from your brokerage account while you run an algorithm that's connected to the account. We sync the algorithm's cash holdings with the cash holdings in your brokerage account every day at 7:45 AM Eastern Time (ET).


&nbsp;
&nbsp;
&nbsp;

![whats-lean](https://user-images.githubusercontent.com/79997186/184042682-2264a534-74f7-479e-9b88-72531661e35d.png)

&nbsp;
&nbsp;
&nbsp;

LEAN Engine is an open-source algorithmic trading engine built for easy strategy research, backtesting, and live trading. We integrate with common data providers and brokerages, so you can quickly deploy algorithmic trading strategies.

The core of the LEAN Engine is written in C#, but it operates seamlessly on Linux, Mac and Windows operating systems. To use it, you can write algorithms in Python 3.8 or C#. QuantConnect maintains the LEAN project and uses it to drive the web-based algorithmic trading platform on the website.

## Contributions

Contributions are warmly very welcomed but we ask you to read the existing code to see how it is formatted, commented and ensure contributions match the existing style. All code submissions must include accompanying tests. Please see the [contributor guide lines](https://github.com/QuantConnect/Lean/blob/master/CONTRIBUTING.md).

## Code of Conduct

We ask that our users adhere to the community [code of conduct](https://www.quantconnect.com/codeofconduct) to ensure QuantConnect remains a safe, healthy environment for
high quality quantitative trading discussions.

## License Model

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You
may obtain a copy of the License at

<http://www.apache.org/licenses/LICENSE-2.0>

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language
governing permissions and limitations under the License.
