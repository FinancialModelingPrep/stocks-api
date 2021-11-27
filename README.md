# Stock API on https://site.financialmodelingprep.com.
This describes how to use stock API's on financialmodelingprep.com. 

1. **[Real-time price](#real-time-price)**
2. **[Stock price list](#stock-price-list)**
3. **[Stock historical prices](#stock-historical-prices)**

## Real-time price

### GET /v3/quote-short/{symbol}
This is a quick endpoint that only returns the stock price. If you only need a price, this endpoint is preferable to the profile endpoint or quote because it is faster and lighter. The price returned is the current price at the time you made your request.

**Documentation:** https://site.financialmodelingprep.com/developer/docs/realtime-stock-quote-api#Stock-Real-time-Price

**Request Parameters:**

```solidity
symbol : Company Symbol, ex. AAPL
```
**Response Example:**

```json
{
  "symbol" : "AAPL",
  "price" : 318.68
}
```

## Stock price list

### GET /v3/quotes/{exchange}
All Real-time stock prices.

**Documentation:** https://site.financialmodelingprep.com/developer/docs/realtime-stock-quote-api#Stock-Price-list

**Request Parameters:**

```solidity
exchange : String, ex. nyse
```
**Response Example:**

```json
[{
  "symbol" : "AAPL",
  "price" : 318.68
  "volume": 332607163
}]
```

## Stock historical prices
These endpoints provides access to historical prices that can be used to create charts. It's updated every day and can go back 15 years in time. You can also get a more than one stock with a single request, for example: historical-price-full/AAPL,FB.

**Request Parameters:**

```solidity
symbol : Company Symbol, ex. AAPL
```

**Response Example:**

```json
{
  "symbol" : "AAPL",
  "historical" : [ {
      "date" : "2021-10-08",
      "open" : 144.03,
      "high" : 144.17,
      "low" : 142.56,
      "close" : 142.9,
      "adjClose" : 142.9,
      "volume" : 5.545036E7,
      "unadjustedVolume" : 5.545036E7,
      "change" : -1.13,
      "changePercent" : -0.785,
      "vwap" : 143.21,
      "label" : "October 08, 21",
      "changeOverTime" : -0.00785
    }, {
      "date" : "2021-10-07",
      "open" : 143.06,
      "high" : 144.215,
      "low" : 142.73,
      "close" : 143.29,
      "adjClose" : 143.29,
      "volume" : 6.1863761E7,
      "unadjustedVolume" : 6.1863761E7,
      "change" : 0.23,
      "changePercent" : 0.161,
      "vwap" : 143.41167,
      "label" : "October 07, 21",
      "changeOverTime" : 0.00161
    }, { "...": "..." }
  ]
}
```

### GET /v3/historical-chart/1min/{symbol}
Stock one minute historical stock prices.

**Documentation:** https://site.financialmodelingprep.com/developer/docs/historical-stock-data-free-api#1-minute-historical-stock-prices-with-volume

### GET /v3/historical-chart/5min/{symbol}
Stock five minutes historical stock prices.

**Documentation:** https://site.financialmodelingprep.com/developer/docs/historical-stock-data-free-api#5-minutes-historical-stock-prices-with--volume

### GET /v3/historical-chart/15min/{symbol}
Stock fifteen minutes historical stock prices.

**Documentation:** https://site.financialmodelingprep.com/developer/docs/historical-stock-data-free-api#15-minutes-historical-stock-prices-with-volume

### GET /v3/historical-chart/30min/{symbol}
Stock thirty minutes historical stock prices.

**Documentation:** https://site.financialmodelingprep.com/developer/docs/historical-stock-data-free-api#30-minutes-historical-stock-prices-with-volume

### GET /v3/historical-chart/1hour/{symbol}
Stock hour historical stock prices.

**Documentation:** https://site.financialmodelingprep.com/developer/docs/historical-stock-data-free-api#Hour-historical-stock-prices-with-volume

### GET /v3/historical-chart/4hour/{symbol}
Stock four hours historical stock prices.

**Documentation:** https://site.financialmodelingprep.com/developer/docs/historical-stock-data-free-api#4-Hours-historical-stock-prices-with-volume

### GET /v3/historical-price-full/{symbol}
Stock daily historical prices.

You may pass more parameters here:

```solidity
to : YYYY-MM-DD, ex. 2020-08-15
from : YYYY-MM-DD, ex. 2020-08-14
timeseries : Number (return last x days), ex. 5
```
And also you may pass more than one company, ex: AAPL,GOOGL, FB. Limited to 3.

**Documentation:** https://site.financialmodelingprep.com/developer/docs/historical-stock-data-free-api#Historical-Daily-Prices

