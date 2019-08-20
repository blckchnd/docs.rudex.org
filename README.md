# RuDEX statistics API

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
 "lowest_ask": "0.00021419",
 "highest_bid": "0.00020440",
 "percent_change": "-0.04",
 "base_volume": "1102.41508000",
 "quote_volume": "0.22576780"
}, 
 ...
]
```
## Asset Details

GET https://ticker.rudex.org/asset/<ASSET> 

Opens asset details page

## Market

GET https://ticker.rudex.org/market/<QUOTE\>_<BASE\>

Opens market page as link to market (our tokens on bitshares dex has prefix, this endpoint will redirect to right place).
                   
