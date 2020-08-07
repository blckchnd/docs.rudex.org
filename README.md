# RuDEX statistics API



## VERSION 1 (NEW) MANDATORY

https://ticker.rudex.org/api/v1/

(for:
https://docs.google.com/document/d/1S4urpzUnO2t7DmS_1dc4EL4tgnnbTObPYXvDeBnukCg
)

## Summary ENDPOINT 0
#### ASSETS   /summary
The summary endpoint is to provide an overview of market data for all tickers and all market pairs on the exchange.
GET https://ticker.rudex.org/api/v1/summary

```
[
  {
    "trading_pairs": "EOS_BTS",
    "last_price": "111.00479306",
    "lowest_ask": "114.14482696",
    "highest_bid": "117.75577362",
    "base_volume": "9254.04171000",
    "quote_volume": "78.23180000",
    "price_change_percent_24h": "-5.73000000",
    "highest_price_24h": "122.51455417",
    "lowest_price_24h": "108.82822814",
    "timestamp": "1596821592"
  },
  ...
]
```

```
trading_pairs - Identifier of a ticker with delimiter to separate base/quote, eg. BTC-USD (Price of BTC is quoted in USD)
last_price - Last transacted price of base currency based on given quote currency
lowest_ask - Lowest Ask price of base currency based on given quote currency
highest_bid - Highest bid price of base currency based on given quote currency
base_volume - 24-hr volume of market pair denoted in BASE currency
quote_volume - 24-hr volume of market pair denoted in QUOTE currency
price_change_percent_24h - 24-hr % price change of market pair
highest_price_24h - Highest price of base currency based on given quote currency in the last 24-hrs
lowest_price_24h - Lowest price of base currency based on given quote currency in the last 24-hrs
timestamp - Unix timestamp in milliseconds for when the last updated time occurred.

```



## ENDPOINT 1
#### ASSETS   /assets
The assets endpoint is to provide a detailed summary for each currency available on the exchange.

GET https://ticker.rudex.org/api/v1/assets

```
{
  "BTC": {
    "name": "bitcoin",
    "unified_cryptoasset_id": "1",
    "can_withdraw": "true",
    "can_deposit": "true",
    "min_withdraw": "0.0018",
    "max_withdraw ": "1000000.00",
    "maker_fee": "0.10",
    "taker_fee": "0.10"
  },
  
  ...
```

```
name - Name of cryptocurrency
unified_cryptoasset_id - Unique ID of cryptocurrency assigned by Unified Cryptoasset ID.
can_withdraw - Identifies whether withdraws are enabled or disabled.
can_deposit - Identifies whether deposits are enabled or disabled.
min_withdraw - Identifies the single minimum withdraw amount of a cryptocurrency.
max_withdraw - Identifies the single maximum withdraw amount of a cryptocurrency.
maker_fee - Fees applied when liquidity is added to the order book.
taker_fee - Fees applied when liquidity is removed from the order book.
```


## ENDPOINT 2
#### TICKER /ticker
The ticker endpoint is to provide a 24-hour pricing and volume summary for each market pair available on the exchange.

GET https://ticker.rudex.org/api/v1/ticker

```
{
  "EOS_BTC": {
    "base_id": 1,
    "quote_id": 7,
    "last_price": "0.00035620",
    "quote_volume": "185.11860000",
    "base_volume": "0.06564715",
    "isfrozen": 1,
    "lowest_ask": "0.00036178",
    "highest_bid": "0.00035462",
    "percent_change": "4.25",
    "updated_at": "1596821592"
  },
  ...
```


```
base_id - The quote pair Unified Cryptoasset ID.
quote_id - The base pair Unified Cryptoasset ID.
last_price - The price of the last executed order
base_volume - 24 hour trading volume in base pair volume
quote_volume - 24 hour trading volume in quote pair volume
isFrozen - Indicates if the market is currently enabled (0) or disabled (1).
lowest_ask - Lowest current purchase price for this asset
highest_bid - Highest current sale price for this asset
percent_change - Price change percentage
updated_at - Unix timestamp in milliseconds for when the last updated time occurred.

```


## ENDPOINT 3
#### ORDERBOOK /orderbook/market_pair
The order book endpoint is to provide a complete level 2 order book (arranged by best asks/bids) with full depth returned for a given market pair.

GET https://ticker.rudex.org/api/v1/orderbook/EOS_BTC

```

{
    "timestamp": 1572275706126,
    "bids": [
      [
        "0.000354321",
        "20"
      ],
      [
        "0.00035432094391099457888",
        "14.1115"
      ],
      [
        "0.00035233433239690697434",
        "42.5732"
      ],
      ...
    ],  
    "asks": [
    [
      "0.0003614775",
      "20"
    ],
    [
      "0.00036147801129257307277",
      "13.8321"
    ],
    [
      "0.00036357290363863761961",
      "41.2572"
    ],
    ...
    ]

}
```

```
timestamp - Unix timestamp in milliseconds for when the last updated time occurred.
bids - An array containing 2 elements. The offer price and quantity for each bid order.
asks - An array containing 2 elements. The ask price and quantity for each ask order.

```

## ENDPOINT 4
#### TRADES /trades/market_pair
The trades endpoint is to return data on all recently completed trades for a given market pair.

GET https://ticker.rudex.org/api/v1/trades/EOS_BTC

```

[
  {
    "tradeid": 27149,
    "price": "0.00035319",
    "base_volume": "0.00175976",
    "quote_volume": "4.98240000",
    "trade_timestamp": "1572285279",
    "type": "buy"
  },
  {
    "tradeid": 27147,
    "price": "0.00035620",
    "base_volume": "0.00041747",
    "quote_volume": "1.17200000",
    "trade_timestamp": "1572269424",
    "type": "sell"
  },
  {
    "tradeid": 27145,
    "price": "0.00035620",
    "base_volume": "0.00008687",
    "quote_volume": "0.24390000",
    "trade_timestamp": "1572269424",
    "type": "sell"
  },
  
  ..
  
]

```

```
trade_id - A unique ID associated with the trade for the currency pair transaction
price - Transaction price in base pair volume
base_volume - Transaction amount in base pair volume.
quote_volume - Transaction amount in quote pair volume.
trade_timestamp - Unix timestamp in milliseconds for when the transaction occurred.
type - 
Used to determine whether or not the transaction originated as a buy or sell.
  Buy – Identifies an ask was removed from the order book.
  Sell – Identifies a bid was removed from the order book.
```


## ENDPOINT 5
#### Market Link /market/market_pair
Opens market page as link to market (our tokens on bitshares dex has prefix, this endpoint will redirect to right place


### Example

```
GET https://ticker.rudex.org/api/v1/market/EOS_BTC
```



## Asset Details

GET https://ticker.rudex.org/asset/<ASSET\> 

Opens asset details page

### Example

```
GET https://ticker.rudex.org/asset/EOS 
```

## Market

GET https://ticker.rudex.org/market/<QUOTE\>_<BASE\>

Opens market page as link to market (our tokens on bitshares dex has prefix, this endpoint will redirect to right place

### Example

```
GET https://ticker.rudex.org/market/EOS_BTS
```
                   
