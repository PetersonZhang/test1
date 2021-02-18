### Get maximum buy/sell amount or open amount

#### Rate Limit: 20 requests per 2 seconds

#### HTTP Request

`GET /api/v5/account/max-size`

> Request Example

```wiki
GET /api/v5/account/max-size?instId=BTC-USDT&mgnMode=isolated

```

#### Request Parameters

| **Parameter** | **Type** | Required | Description                                                                                      |
| :------------ | :------- | :------- | :----------------------------------------------------------------------------------------------- |
| instId        | String   | Yes      | Instrument ID, e.g. `BTC-USDT-200802`                                                            |
| tdMode        | String   | Yes      | Trade mode<br>`cross` `isolated` `cash`                                                          |
| ccy           | String   | Optional | Currency used for margin<br />Only applicable to `MARGIN` of `Single-currency margin`.           |
| px            | String   | No       | Price<br>When the price is not passed, it will be calculated according to the last traded price. |

> Example Response

```json
{
  "code": "0",
  "msg": "",
  "data": [
    {
      "instId": "BTC-USDT-200802",
      "maxBuy": "1",
      "maxSell": "1"
    }
  ]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                                          |
| :------------ | :------- | :--------------------------------------------------------------------------------------------------------------------------------------- |
| instId        | String   | Instrument ID                                                                                                                            |
| maxBuy        | String   | `SPOT`: The maximum number of coins that you can buy<br />`FUTURES`/`SWAP`/`OPTIONS`: The maximum number of contracts that you can buy   |
| maxSell       | String   | `SPOT`: The maximum number of coins that you can sell<br />`FUTURES`/`SWAP`/`OPTIONS`: The maximum number of contracts that you can sell |
