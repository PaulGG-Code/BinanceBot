# Binance Trader (RC 2) 
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)
[![Build Status](https://img.shields.io/badge/binance-exchange-yellow.svg?style=flat)](https://binance.com)
This is an experimental bot for auto trading the binance.com exchange.

![Screenshot](https://github.com/paulgg-code/binance-trader/blob/master/img/screenshot.png)

## Configuration

1. [Signup](https://www.binance.com/?ref=42789662) for Binance
2. Enable Two-factor Authentication
3. Go API Center, [Create New](https://www.binance.com/en/my/settings/api-management?ref=42789662) Api Key

        [✓] Read Info [✓] Enable Trading [X] Enable Withdrawals

4. Rename **config.sample.py** to `config.py` / **orders.sample.db** to `orders.db`
5. Get an API and Secret Key, insert into `config.py`

        API key for account access
        api_key = ''
        Secret key for account access
        api_secret = ''

        [API Docs](https://www.binance.com/restapipub.html)

6. Optional: Modify recv_window value (not recommended)

7. Optional: run as an excutable application in Docker containers

## Support

[https://www.binance.com/?ref=42789662](https://www.binance.com/?ref=42789662)

## Requirements

    sudo pip install requests

    Python 3
        import os
        import sys
        import time
        import config
        import argparse
        import threading
        import sqlite3

## Usage (trading module)

    python trader.py --symbol CAKEBUSD

    Example parameters

    # Profit mode (default)
    python trader.py --symbol CAKEBUSD --quantity 50 --profit 1.3
    or by amount
    python trader.py --symbol CAKEBUSD --amount 30 --profit 3

    # Range mode
    python trader.py --symbol CAKEBUSD --mode range --quantity 50 --buyprice 2 --sellprice 2.7
    or by amount
    python trader.py --symbol CAKEBUSD --mode range --amount 30 --buyprice 2.4 --sellprice 2.6

    --quantity     Buy/Sell Quantity (default 0) (If zero, auto calc)
    --amount       Buy/Sell BUSD Amount (default 0)
    --symbol       Market Symbol (default CAKEBUSD or CAKEBNB)
    --profit       Target Profit Percentage (default 1.3)
    --stop_loss    Decrease sell price at loss Percentage (default 0)
    --orderid      Target Order Id (default 0)
    --wait_time    Wait Time (seconds) (default 0.7)
    --increasing   Buy Price Increasing  +(default 0.01)
    --decreasing   Sell Price Decreasing -(default 0.01)
    --prints       Scanning Profit Screen Print (default True)
    --loop         Loop (default 0 unlimited)

    --mode         Working modes profit or range (default profit)
                   profit: Profit Hunter. Find defined profit, buy and sell. (Ex: 1.3% profit)
                   range: Between target two price, buy and sell. (Ex: <= 2.1 buy - >= 2.3 sell )

    --buyprice     Buy price (Ex: 2.1)
    --sellprice    Buy price (Ex: 2.3)

    Symbol structure;
        XXXBUSD  (Bitcoin)
        XXXETH  (Ethereum)
        XXXBNB  (Binance Coin)
        XXXUSDT (Tether)

    All binance symbols are supported.

    Every coin can be different in --profit and --quantity.
    If quantity is empty --quantity is automatically calculated to the minimum qty.

    Variations;
        trader.py --symbol TBNBUSD --quantity 50 --profit 3
        trader.py --symbol NEOBUSD --amount 0.1 --profit 1.1
        trader.py --symbol ETHUSDT --quantity 0.3 --profit 1.5
        ...

## Usage (balances module)

    python balance.py

## Run in a Docker container

    docker build -t trader .

    docker run trader

## DISCLAIMER

    I am not responsible for anything done with this bot.
    You use it at your own risk.
    There are no warranties or guarantees expressed or implied.
    You assume all responsibility and liability.

## Contributing

    Fork this Repo
    Commit your changes (git commit -m 'Add some feature')
    Push to the changes (git push)
    Create a new Pull Request

    Thanks all for your contributions...

    Contributors
        @WeSpeakCrypto
        @afoke
        @omerfarukz
        @plgonzalezrx8
		@paulgg-code

## Troubleshooting

    Filter failure: MIN_NOTIONAL
    https://support.binance.com/hc/en-us/articles/115000594711-Trading-Rule

    Filter failure: PRICE_FILTER
    https://github.com/binance-exchange/binance-official-api-docs/blob/master/rest-api.md

    Timestamp for this request was 1000ms ahead of the server's time.
    https://github.com/yasinkuyu/binance-trader/issues/63#issuecomment-355857901

## Roadmap

    - MACD indicator (buy/sell)
    - Stop-Loss implementation
    - Working modes
      - profit: Find defined profit, buy and sell. (Ex: 1.3% profit)
      - range:  Between target two price, buy and sell. (Ex: <= 0.00100 buy - >= 0.00150 sell )
    - Binance/Bittrex/HitBUSD Arbitrage  

    ...

    - October  7, 2017 Beta
    - January  6, 2018 RC
    - January 15, 2018 RC 1
    - January 20, 2018 RC 2
    - March    2, 2021
## License

Code released under the [MIT License](https://opensource.org/licenses/MIT).

---
