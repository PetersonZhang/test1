### Get the maximum loan of instrument

#### Rate Limit: 20 requests per 2 seconds

#### HTTP Request

`GET /api/v5/account/max-loan`

> Request Example

```wiki
Max loan of isolated `MARGIN` in `Single-currency margin`
GET  /api/v5/account/max-loan?instId=BTC-USDT&mgnMode=isolated

Max loan of cross `MARGIN` in `Single-currency margin` (Margin Currency is BTC)
GET  /api/v5/account/max-loan?instId=BTC-USDT&mgnMode=cross&mgnCcy=BTC

Max loan of cross `MARGIN` in `Multi-currency margin`
GET  /api/v5/account/max-loan?instId=BTC-USDT&mgnMode=cross

```

#### Request Parameters

| Parameter | Type   | Required | Description                                                                      |
| :-------- | :----- | :------- | :------------------------------------------------------------------------------- |
| instId    | String | Yes      | Instrument ID                                                                    |
| mgnMode   | String | Yes      | Margin mode<br>`isolated` `cross`                                                |
| mgnCcy    | String | Optional | Margin currency<br>Only applicable to cross `MARGIN` in `Single-currency margin` |

> Example Response

```json
{
  "code": "0",
  "msg": "",
  "data": [
    {
      "instId": "BTC-USDT",
      "mgnMode": "isolated",
      "mgnCcy": "",
      "maxLoan": "0.1",
      "ccy": "BTC",
      "side": "sell"
    },
    {
      "instId": "BTC-USDT",
      "mgnMode": "isolated",
      "mgnCcy": "",
      "maxLoan": "0.2",
      "ccy": "USDT",
      "side": "buy"
    }
  ]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                    |
| :------------ | :------- | :------------------------------------------------------------------------------------------------- |
| instId        | String   | Instrument ID                                                                                      |
| mgnMode       | String   | Margin mode                                                                                        |
| mgnCcy        | String   | Margin currency<br>Only applicable to cross `MARGIN` in `Single-currency margin`, if not return "" |
| maxLoan       | String   | Max loan                                                                                           |
| ccy           | String   | Currency                                                                                           |
| side          | String   | Order side<br>`buy` `sell`                                                                         |
