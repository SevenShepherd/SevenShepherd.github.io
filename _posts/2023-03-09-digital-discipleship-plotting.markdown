---
layout: post
title: "📈 Exercises In Digital Discipleship, Part IV: Plotting Ichimoku Cloud"
date: 2023-03-09 01:00:00 -0500
categories: python plotting graphing crypto
published: true
---

⚠️ This ministry does not take any stances on cryptocurrencies. This article is for **educational purposes only** and not intended as financial advice.

> The toil of a fool wearies him, for he does not know the way to the city. &mdash; Ecclesiastes 10:15

This is an **intermediate** exercise written 01/21/2022 on a separate blog, and repurposed for the digital discipleship program created by SevenShepherd. If you are new or haven't gone through our fundamentals course, you may want to check that out before attempting this exercise.

![cloud](/assets/images/trade/cloud.png)

## **Extracting Data From Binance.US**

We need to create an account somewhere that will allow us API access to the data we need to feed to our python program. It's been awhile since I've used a centralized exchange so let's walk through this process together.

Let's register with the United States based [Binance.US](https://accounts.binance.us/en/register) exchange. Once you've completed the registration. Navigate to the [API Management](https://www.binance.us/en/usercenter/settings/api-management) page. Follow the prompts until you've been presented with your `API key` and `Secret Key`. You'll likely want to keep these safeguarded in a password database like [KeyPassXC](https://keepassxc.org/).

## Directory Structure

Create the following directory structure.

```
crypto/
├─ analysis/
│  ├─ __init__.py
│  └─ ichimoku.py
├─ binance/
│  ├─ __init__.py
│  ├─ api.py
│  ├─ binance.py
│  └─ market.py
└─ main.py
```

## **Exploring The Binance.US API**

```
crypto/
└─ binance/
   └─ api.py
       Ⓒ BinanceAPI()
          Ⓢ error_handler()
          Ⓢ deserialize()
```

We will be making heavy use of the [Binance.US API Documentation](https://docs.binance.us/). 

- The base endpoint is: **https://api.binance.us** 
- All endpoints return either a JSON object or array. 
- Data is returned in ascending order. Oldest first, newest last. 
- All time and timestamp related fields are in milliseconds.

```py
from requests.exceptions import HTTPError
from functools           import wraps

class BinanceAPI:

    API_KEY    = "YOUR API KEY GOES HERE"
    API_SECRET = "YOUR API SECERT GOES HERE"
    HEADER     = {
        'get' : {"X-MBX-APIKEY": API_KEY},
    }

    # Base + Version
    __baseEndpoint = 'https://api.binance.us'
    ENDPOINT       = __baseEndpoint + '/api/v3/'
    
    @staticmethod
    def error_handler(func):
        @wraps(func)
        def logic(*args, **kwargs):
            resp = func(*args, **kwargs)
            
            if not resp.ok:
                raise HTTPError(f"[!] Error: {resp.status_code} {resp.reason} {resp.json()}")
                
            if resp.status_code != 200:
                print(f"[!] Warning: {resp.status_code} {resp.reason}")
            
            return resp
        return logic
    
    @staticmethod
    def deserialize(func):
        @wraps(func)
        def transform(*args, **kwargs):
            try:
                resp = func(*args, **kwargs)
            except HTTPError as error:
                print(error)
                return False

            return resp.json()
        return transform
```

## The BinanceAPI Method Decorators

The `@error_handler` decorator is a simple function that tests the response object for an HTTP status code of 400 or higher, indicated by the negation of resp.ok. If this is triggered the decorator will raise requests.exception.HTTPError with the response objects textual reason as the error. You can expand this on your own with resp.status_code.

```py
@staticmethod
def error_handler(func):
    @wraps(func)
    def logic(*args, **kwargs):
        resp = func(*args, **kwargs)
        
        if not resp.ok:
            raise HTTPError(f"[!] Error: {resp.status_code} {resp.reason} {resp.json()}")
            
        if resp.status_code != 200:
            print(f"[!] Warning: {resp.status_code} {resp.reason}")
        
        return resp
    return logic
```

The final decorator we will be making use of is our deserializer. Essentially this function will handle the result of the previous decorator as we will be stacking these decorators over the various class methods. If the `@error_handler` decorator raises an exception, the try except block will be executed, returning `False`. If all goes as planned, the requests response object is passed into the `@deserialize` decorator, which will take an stringified json object from the server and "deserialize" it into a dictionary object manipulatable by our program.

```py
@staticmethod
def deserialize(func):
    @wraps(func)
    def transform(*args, **kwargs):
        try:
            resp = func(*args, **kwargs)
        except HTTPError as error:
            print(error)
            return False

        return resp.json()
    return transform
```

## Extracting Candlestick Data

![cs](/assets/images/trade/candle.png)

```
crypto/
└─ binance/
   └─ market.py
        Ⓒ MarketData(BinanceAPI)
            Ⓜ klines()
```

The primary role this class plays is that of the retrieval of actionable data from the Binance.US REST server. Through inheritance of its parent BinanceAPI class, each method’s returned data will be deserialized into useable data structures for use in our bot.

- For GET endpoints, parameters must be sent as a query string.
- [Candlestick Kline Documentation](https://docs.binance.us/?python#get-candlestick-data)

```py
from binance.api import BinanceAPI

import requests

class MarketData(BinanceAPI):
    
    @BinanceAPI.deserialize
    @BinanceAPI.error_handler
    def ping(self):
        """ 
        GET /api/v3/ping

        Test connectivity to the Rest API.

        Weight: 1

        Parameters: NONE

        Response: {}
        """  
        return requests.get(url = BinanceAPI.ENDPOINT + 'ping')
        
    @BinanceAPI.deserialize
    @BinanceAPI.error_handler
    def klines(self, symbol="BTCUSDT", interval="1d", startTime=None, endTime=None, limit=500):
        """ 
        GET /api/v3/klines

        Kline/candlestick bars for a symbol. 
        Klines are uniquely identified by their open time.

        Weight: 1

        | Name      | Type   | Mandatory | Description             |
        |-----------|--------|-----------|-------------------------|
        | symbol    | STRING | YES       |                         |
        | interval  | ENUM   | YES       |                         |
        | startTime | LONG   | NO        |                         |
        | endTime   | LONG   | NO        |                         |
        | limit     | INT    | NO        | Default: 500; max 1000. |

        If startTime and endTime are not sent, the most recent klines are returned.

        Response: 
        
        [
            [
                1499040000000, // Open time
                "0.00386200",  // Open
                "0.00386200",  // High
                "0.00386200",  // Low
                "0.00386200",  // Close
                "0.47000000",  // Volume
                1499644799999, // Close time
                "0.00181514",  // Quote asset volume
                1,             // Number of trades
                "0.47000000",  // Taker buy base asset volume
                "0.00181514",  // Taker buy quote asset volume
                "0" // Ignore.
            ]
        ]

        m -> minutes; h -> hours; d -> days; w -> weeks; M -> months
        """
        return requests.get(
            url     = BinanceAPI.ENDPOINT + 'klines',
            params  = {
                'symbol'    : symbol, 
                'interval'  : interval,
                'startTime' : startTime,
                'endTime'   : endTime,
                'limit'     : limit 
            }
        )
```

## Formatting Candlestick Data

```
crypto/
└─ binance/
    └─ binance.py
        Ⓒ Binance(MarketData)
            Ⓜ candles()
        Ⓓ say()
```

```py
from binance.market import MarketData
from datetime       import datetime

import numpy  as np
import pandas as pd

import time

class Binance(MarketData):
    """
    The purpose of this class is to make sense of the data provided by its inherited methods.
    """

    def test_connection(self):
        return self.ping()

    def candles(self, symbol="BTCUSDT", interval="1d", startTime=None, endTime=None, limit=500):
        """
        Returns kline data in a pandas DataFrame.

                                    open      high       low     close      volume
        date
        2022-01-07 23:59:59.999  41813.06  42003.24  41763.62  41877.37    3.722429
        2022-01-08 03:59:59.999  41953.26  42199.05  41775.61  41936.91   16.839122
        2022-01-08 07:59:59.999  41932.70  42044.44  41395.90  41610.62   34.417348
        2022-01-08 11:59:59.999  41616.50  41724.13  40502.75  40802.00   74.394267
        2022-01-08 15:59:59.999  40871.32  42318.07  40726.98  41691.66   37.362512
        ...                           ...       ...       ...       ...         ...
        2022-01-21 03:59:59.999  39120.92  39279.94  38682.95  38880.04   25.458106
        2022-01-21 07:59:59.999  38903.98  39030.43  37706.69  38849.32  121.282145
        2022-01-21 11:59:59.999  38866.64  39057.23  37857.95  37954.55  115.010300
        2022-01-21 15:59:59.999  37967.73  38508.49  35450.11  36474.82  350.844053
        2022-01-21 19:59:59.999  36445.31  36832.05  36157.48  36368.72   52.074380

        [84 rows x 5 columns]
        """

        data    = self.klines( symbol, interval, startTime, endTime, limit )
        dateObj = lambda x: datetime.fromtimestamp(x/1000)

        df = pd.DataFrame(
            # Open / High / Low / Close / Volume / Datetime Object
            data    = [ [dateObj(i[6])] + i[1:6] for i in data ],
            columns = ['date', 'open', 'high', 'low', 'close', 'volume'],
            dtype   = np.double
        )
        df.set_index('date', inplace=True)

        return df

def say(string):
    t = time.strftime("%Y%m%d %I:%M:%S", time.localtime())
    print(f"[{t}] {string.title()} ...")
```

## **Plotting Technical Indicators**

- [Mplfinance Styles](https://github.com/matplotlib/mplfinance/blob/master/examples/styles.ipynb)

## Ichimoku Cloud (Ichimoku Kinko Hyo)

```
crypto/
└─ analysis/
   └─ ichimoku.py
        Ⓒ IchimokuKinkoHyo
            Ⓜ __tenkan_sen()
            Ⓜ __kijun_sen()
            Ⓜ __senkou_span_a()
            Ⓜ __senkou_span_b()
            Ⓜ __kumo()
            Ⓜ __chikou_span()
            Ⓜ _ichimoku_cloud()
            Ⓜ plot()
```

The Ichimoku Kinko Hyo indicator, better known as `Ichimoku cloud`, is best when used for trend determination, entry signals, exit signal, re-entry signals. Do not use when the market is clearly trend less and sideways. In these instances, use Bollinger Bands or Chart Patterns instead. The best settings for Ichimoku Cloud are as follows

<!-- - Default: 9 / 26 / 52 / 26 / 26
- Crypto: 10 / 30 / 60 / 30 / 30
- Double: 20 / 60 / 120 / 30 / 30 -->

|:-:|
|Default|9 / 26 / 52 / 26 / 26|
|Crypto|10 / 30 / 60 / 30 / 30|
|Double|20 / 60 / 120 / 30 / 30|

<!-- - [Ichimoku Trader](https://www.ichimokutrader.com/signals.html)
- [‘Toshimoku’s Trading Tips & Tricks](https://medium.com/@CarpeNoctom/toshimokus-trading-tips-tricks-f0ff5cc38cc8) -->

- `Altcoins`: For altcoins, backtesting has shown that on the 1D time frame, 10/30/60/30 gives a superior entry and exit signal compared to the doubled settings. The altcoin markets are more explosive relative to the more stable Bitcoin market, which has a larger market capitalization.

- `Bitcoin`: The doubled settings are best for most all other cases, and are the setting I used the most. If you are looking at the 1h time frame you're looking at the 2h cloud. If you look at the 4h time frame, you're looking at the 8h cloud. This decreases the false positives and increases the profitable trades you take. 

|Entry Signals||
|:-:|:-:|
|Trend|Is the price above or below the **Cloud**? This is the Gold Standard in determining whether or not the current market state is bullish or bearish.|
|Future|Is the **Cloud** bullish or bearish? Pay attention to the **Kumo twist**.|
|TK Cross|Has the **Tenkan** crossed above the **Kijun**? This is very similar to EMA crosses.|
|Fence|If you're on the fence about what to do, check the **Chikou** Lagging Span position. Is the Chikou above or below the **Price** and/or **Cloud**. Can save you from taking a suboptimal position, especially when price is essentially sideways.|

<!-- - **`Entry Signals`** (order of importance):
    - `Trend`: Is the price above or below the **Cloud**? This is the Gold Standard in determining whether or not the current market state is bullish or bearish.
    - `Future`: Is the **Cloud** bullish or bearish? Pay attention to the **Kumo twist**.
    - `TK Cross`: Has the **Tenkan** crossed above the **Kijun**? This is very similar to EMA crosses.
    - `Fence`: If you're on the fence about what to do, check the **Chikou** Lagging Span position. Is the Chikou above or below the **Price** and/or **Cloud**. Can save you from taking a suboptimal position, especially when price is essentially sideways. -->

|Exit Signals||
|:-:||
|TK Cross|Has the **Tenkan** crossed below the **Kijun**?|
|Bill Williams Fractals|Fractals are useful as a stop-loss with many indicators|
|HA candlesticks||
|Horizontal Levels||

|Re-entry Signals||
|:-:|:-:|
|TK Cross/Recross|Has the **Tenkan** crossed below the **Kijun** and then above again? A TK recross above **Cloud** is an extremely bullish predictor of future price action and should be seen as a high probability long re-entry.|
|Kijun Bounce|The **Kijun** bounce occurs when price returns to equilibrium and then continues the current trend. This can also be thought of as a correction or a test of support. I always consider orders on or around the **Kijun** a safe entry. No matter how far price is from **Kijun**, it is likely to return and test that level at some point. If I miss an ideal entry, or miss a trade entirely, my default entry for a trend is always the **Kijun**.|
|Edge to Edge (E2E) Trades|when a candle close occurs inside the **Cloud**, you can, with reasonably high probability, expect price to reach the other end of the **Cloud**. The larger the **Cloud**, the larger the payoff.|

<!-- - **`Re-entry Signals`**
    - `TK Cross/Recross`: Has the **Tenkan** crossed below the **Kijun** and then above again? A TK recross above **Cloud** is an extremely bullish predictor of future price action and should be seen as a high probability long re-entry.

    - `Kijun Bounce`: The **Kijun** bounce occurs when price returns to equilibrium and then continues the current trend. This can also be thought of as a correction or a test of support. I always consider orders on or around the **Kijun** a safe entry. No matter how far price is from **Kijun**, it is likely to return and test that level at some point. If I miss an ideal entry, or miss a trade entirely, my default entry for a trend is always the **Kijun**.

    - `Edge to Edge (E2E) Trades`: when a candle close occurs inside the **Cloud**, you can, with reasonably high probability, expect price to reach the other end of the **Cloud**. The larger the **Cloud**, the larger the payoff.  -->
    

```py
from datetime import timedelta
from numpy    import nan

import mplfinance as mpf


class IchimokuKinkoHyo:

    def __tenkan_sen(self, df, period=20):
        """
        Tenkan-sen (Conversion Line): (20-period high + 20-period low)/2))
            The default setting is 9 periods and can be adjusted. On a daily chart, 
            this line is the midpoint of the 9-day high-low range, which is almost two weeks.  
        """
        high = df['high'].rolling(period).max()
        low  = df['low'].rolling(period).min()
        return (high + low)/2

    def __kijun_sen(self, df, period=60):
        """
        Kijun-sen (Base Line): (60-period high + 60-period low)/2))
            The default setting is 26 periods and can be adjusted. On a daily chart, 
            this line is the midpoint of the 26-day high-low range, which is almost one month).  
        """
        high = df['high'].rolling(period).max()
        low  = df['low'].rolling(period).min()
        return (high + low)/2

    def __senkou_span_a(self, df, future=30):
        """
        Senkou Span A (Leading Span A): (Conversion Line + Base Line)/2))
            This is the midpoint between the Conversion Line and the Base Line. The Leading Span A forms one of the two cloud boundaries. 
            It is referred to as "Leading" because it is plotted 26 periods in the future and forms the faster cloud boundary.
        """
        return ((self.__tenkan_sen(df) + self.__kijun_sen(df))/2).shift(future)

    def __senkou_span_b(self, df, period=120, future=30):
        """
        Senkou Span B (Leading Span B): (120-period high + 120-period low)/2))
            On the daily chart, this line is the midpoint of the 52-day high-low range, which is a little less than 3 months. 
            The default calculation setting is 52 periods, but can be adjusted. This value is plotted 26 periods in the future
            and forms the slower cloud boundary.
        """
        high = df['high'].rolling(period).max()
        low  = df['low'].rolling(period).min()
        # return high.add(low).divide(2).shift(future)
        return ((high + low)/2).shift(future)

    def __kumo(self, df):
        """
        Senkou Span A & Senkou Span B
        """
        return self.__senkou_span_a(df), self.__senkou_span_b(df)

    def __chikou_span(self, df, offset=30):
        """
        Chikou Span (Lagging Span): Close plotted 30 days in the past
            The default setting is 26 periods, but can be adjusted. 
        """
        return df['close'].shift(-30)

    def _ichimoku_cloud(self, df, t=20, k=60, b=120, c=30, future=30):
        """
        Settings: 20/60/120/30
        """
        # lastDate = datetime.strptime(lastDate, "%Y-%m-%d %H:%M:%S.%f")
        lastDate = df.index[-1].to_pydatetime()
        
        for i in range(1, future+1):
            df.loc[lastDate+timedelta(days=i)] = [nan]*5

        return self.__tenkan_sen(df, t),            \
               self.__kijun_sen(df, k),             \
               self.__senkou_span_a(df, future),    \
               self.__senkou_span_b(df, b, future), \
               self.__chikou_span(df, c)

    def plot(self, df):

        t, k, a, b, c = self._ichimoku_cloud(df)

        apds = [
            mpf.make_addplot(t, panel=0, type='line', ylabel='tenkan'  , color='r'),
            mpf.make_addplot(k, panel=0, type='line', ylabel='kijun'   , color='#0050B5'), #Blue
            mpf.make_addplot(a, panel=0, type='line', ylabel='senkou_a', color='#00873E'), #Green
            mpf.make_addplot(b, panel=0, type='line', ylabel='senkou_b', color='tomato'),
            mpf.make_addplot(c, panel=0, type='line', ylabel='chikou'  , color='grey'),
        ]

        # CUSTOM STYLE
        stylish = mpf.make_mpf_style( 
            marketcolors = mpf.make_marketcolors(
                up     = 'palegreen',
                down   = 'tomato',
                wick   = {'up':'blue','down':'red'},
                volume = 'in'
            ),
            base_mpl_style="seaborn"
        )

        mpf.plot(
            df, 
            type         = 'candle', 
            fill_between = dict(
                y1    = a.values, 
                y2    = b.values,
                alpha = 0.5
            ), 
            volume       = True, 
            addplot      = apds, 
            style        = stylish,
            volume_panel = 1,
            title        = 'Ichimoku Cloud'
        )
```


## **The Main Program**

```
crypto/
└─ main.py
```

```py
from binance.binance    import Binance, say
from analysis.ichimoku  import IchimokuKinkoHyo

TICKER = "BTCUSDT"

def main():
    # Initialize Class Instance to Handle
    say("initializing binance class instance")
    bi = Binance()

    # Retrieve candlestick data for fractal calculations
    say("retrieving candlestick data")
    df = bi.candles(
        symbol    = TICKER,
        interval  = '1d',
    )

    if bi.test_connection():
        raise ConnectionError("[!] Connect to the internet!".title())
    
    say("connectivity established")
    
    say("plotting ichimoku kinko hyo")
    cloud = IchimokuKinkoHyo()
    cloud.plot(df)

if __name__ == "__main__":
    main()
```