# RuDEX statistics API



## VERSION 1 (NEW) MANDATORY

https://ticker.rudex.org/api/v1/

(for:
https://docs.google.com/document/d/1S4urpzUnO2t7DmS_1dc4EL4tgnnbTObPYXvDeBnukCg
)


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
    "updated_at": "2019-10-28T15:51:27.000Z"
  },
  ...
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

## ENDPOINT 4
#### TRADES /trades/market_pair
The trades endpoint is to return data on all recently completed trades for a given market pair.

GET https://ticker.rudex.org/api/v1/trades/EOS_BTC

```

[
  {
    "tradeid": 27147,
    "price": "0.00035620",
    "base_volume": "0.00041747",
    "quote_volume": "1.17200000",
    "trade_timestamp": "1572269424000",
    "type": "sell"
  },
  {
    "tradeid": 27145,
    "price": "0.00035620",
    "base_volume": "0.00008687",
    "quote_volume": "0.24390000",
    "trade_timestamp": "1572269424000",
    "type": "sell"
  },
  {
    "tradeid": 27143,
    "price": "0.00035956",
    "base_volume": "0.31610000",
    "quote_volume": "0.00011366",
    "trade_timestamp": "1572248643000",
    "type": "buy"
  },
  
  ..
  
]

```



## VERSION 0 (OLD) DEPRECATED

## Tickers

GET https://ticker.rudex.org/api/v0/tickers

Retrieves array with summary information for each currency pair listed on the exchange. Fields include:

```
name - Name of pair <QUOTE>_<BASE>
updated_at - Time when data retrieved
latest - Execution price for the most recent trade for this pair
lowest_ask - Lowest current purchase price for this asset
highest_bid - Highest current sale price for this asset
percent_change - Price change percentage
base_volume - Base units traded in the last 24 hours
quote_volume - Quoted units traded in the last 24 hours
```
### Example

```
[
{
 "name": "BTS_ETH",
 "updated_at": "2019-08-20T17:21:42.000Z",
 "latest": "0.00020439",
 "lowest_ask": "0.00020440",
 "highest_bid": "0.00021419",
 "percent_change": "-0.04",
 "quote_volume": "1102.41508000",
 "base_volume": "0.22576780"
}, 
 {....},
 {....},
 ...
]
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
                   
