### Get Positions

Retrieve information on your positions. When the account is in `net` mode, `net` positions will be displayed, and when the account is in `long/short` mode, `long` or `short` positions will be displayed.

#### Rate Limit: 20 requests per 2 seconds

#### HTTP Request

`GET /api/v5/account/positions`

> Request Example

```wiki
Query BTC-USDT position information
GET /api/v5/account/positions?instId=BTC-USDT

```

##### Request Parameters

| **Parameter** | **Type** | **Required** | **Description**                                                                                                                                                                                                     |
| :------------ | :------- | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| instType      | String   | No           | Instrument type<br>`MARGIN`<br />`SWAP`<br />`FUTURES`<br />`OPTION`<br>`instId` will be checked against `instType` when both parameters are passed, and the position information of the `instId` will be returned. |
| instId        | String   | No           | Instrument ID, e.g. `BTC-USD-190927-5000-C`                                                                                                                                                                         |
| posId         | String   | No           | Single position ID or multiple position IDs (no more than 20) separated with comma                                                                                                                                  |

> Example Response

```json
{
  "code": "0",
  "msg": "",
  "data": [
    {
      "instId": "BTC-USDT",
      "instType": "MARGIN",
      "mgnMode": "cross",
      "posId": "1111234112",
      "posSide": "net",
      "pos": "10",
      "ccy": "BTC",
      "posCcy": "BTC",
      "availPos": "2",
      "avgPx": "3320",
      "upl": "0.00020928",
      "uplRatio": "0.00020928",
      "lever": "2",
      "liqPx": "0.00020928",
      "imr": "2",
      "margin": "",
      "mgnRatio": "",
      "mmr": "2",
      "liab": "0.00020928",
      "liabCcy": "USDT",
      "interest": "2",
      "tradeId": "2",
      "optVal": "",
      "adl": "2",
      "last": "12353.5",
      "cTime": "1597026383085",
      "uTime": "1597026383085"
    }
  ]
}
```

##### Request Parameters

| **Parameter** | **Type** | **Description**                                                                                                                                                                                                                                                      |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| instType      | String   | Instrument type                                                                                                                                                                                                                                                      |
| mgnMode       | String   | Margin mode<br>`cross` <br />`isolated`                                                                                                                                                                                                                              |
| posId         | String   | Position ID                                                                                                                                                                                                                                                          |
| posSide       | String   | Position side<br>`long`<br />`short`<br />`net` (`FUTURES/SWAP/OPTION`: positive `pos` means long position and negative `pos` means short position. `MARGIN`: `posCcy` being base currency means long position, `posCcy` being quote currency means short position.) |
| pos           | String   | Quantity of positions                                                                                                                                                                                                                                                |
| posCcy        | String   | Position currency, only applicable to `MARGIN` positions.                                                                                                                                                                                                            |
| availPos      | String   | Position that can be closed<br /> Only applicable to `MARGIN`, `FUTURES/SWAP` in the `long-short` mode, OPTION in `Simple` and `isolated` `OPTION` in margin Account.                                                                                                |
| avgPx         | String   | Average open price                                                                                                                                                                                                                                                   |
| upl           | String   | Unrealized profit and loss                                                                                                                                                                                                                                           |
| uplRatio      | String   | Unrealized profit and loss ratio                                                                                                                                                                                                                                     |
| instId        | String   | Instrument ID, e.g. `BTC-USD-180216`                                                                                                                                                                                                                                 |
| lever         | String   | Leverage, not applicable to `OPTION` seller                                                                                                                                                                                                                          |
| liqPx         | String   | Estimated liquidation price<br>Not applicable to `cross` `FUTURES/SWAP` in `Multi-currency margin` <br />Not applicable to `OPTION`                                                                                                                                  |
| imr           | String   | Initial margin requirement, only applicable to `cross`.                                                                                                                                                                                                              |
| margin        | String   | Margin, can be added or reduced. Only applicable to `isolated` `Margin`.                                                                                                                                                                                             |
| mgnRatio      | String   | Margin ratio, only applicable to `isolated`.                                                                                                                                                                                                                         |
| mmr           | String   | Maintenance margin requirement                                                                                                                                                                                                                                       |
| liab          | String   | Liabilities, only applicable to `MARGIN`.                                                                                                                                                                                                                            |
| liabCcy       | String   | Liabilities currency, only applicable to `MARGIN`.                                                                                                                                                                                                                   |
| interest      | String   | Interest. Interest that has been incurred.                                                                                                                                                                                                                           |
| tradeId       | String   | Last trade ID                                                                                                                                                                                                                                                        |
| optVal        | String   | Option Value, only applicable to `OPTION`.                                                                                                                                                                                                                           |
| adl           | String   | Auto-deleveraging (ADL) indicator<br>Divided into 5 levels, from 1 to 5, the smaller the number, the weaker the adl intensity.                                                                                                                                       |
| ccy           | String   | Currency used for margin                                                                                                                                                                                                                                             |
| last          | String   | Latest traded price                                                                                                                                                                                                                                                  |
| cTime         | String   | Creation time, Unix timestamp format in milliseconds, e.g. `1597026383085`                                                                                                                                                                                           |
| uTime         | String   | Latest time position was adjusted, Unix timestamp format in milliseconds, e.g. `1597026383085`                                                                                                                                                                       |
