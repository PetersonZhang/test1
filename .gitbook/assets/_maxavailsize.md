### Get Maximum Available Tradable Amount

#### Rate Limit: 20 requests per 2 seconds

#### HTTP Request

`GET /api/v5/account/max-avail-size`

> Request Example

```wiki
Query maximum available transaction amount when cross MARGIN BTC-USDT use BTC as margin
GET /api/v5/account/max-avail-size?instId=BTC-USDT&tdMode=cross&ccy=BTC

Query maximum available transaction amount for SPOT BTC-USDT
GET /api/v5/account/max-avail-size?instId=BTC-USDT&tdMode=cash

```

#### Request Parameters

| **Parameter** | **Type** | Required | Description                                                                                   |
| :------------ | :------- | :------- | :-------------------------------------------------------------------------------------------- |
| instId        | String   | Yes      | Instrument ID, e.g. `BTC-USDT-200802`                                                         |
| ccy           | String   | Optional | Currency used for margin<br/>Only applicable to `cross` `MARGIN` of `Single-currency margin`. |
| tdMode        | String   | Yes      | Trade mode<br>`cross` `isolated` `cash`                                                       |
| reduceOnly    | Boolean  | No       | Whether to reduce position only<br />Only applicable to `MARGIN`                              |

> Example Response

```json
{
  "code": "0",
  "msg": "",
  "data": [
    {
      "instId": "BTC-USDT-200802",
      "availBuy": "1",
      "availSell": "1"
    }
  ]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**          |
| :------------ | :------- | :----------------------- |
| instId        | String   | Instrument ID            |
| availBuy      | String   | Amount available to buy  |
| availSell     | String   | Amount available to sell |

<aside class="notice">
In the case of SPOT/MARGIN, availBuy is in the quote currency, and availSell is in the base currency.<br/>
In the case of MARGIN with cross tdMode, both availBuy and availSell are in the currency passed in <strong>ccy</strong>.
</aside>
