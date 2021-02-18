### Set Leverage

The following are the setting leverage cases for an instrument:

Set leverage for isolated MARGIN at pairs level.

Set leverage for `cross` `MARGIN` in `Single-currency margin` at pairs level.

Set leverage for `cross` `MARGIN` in `Multi-currency margin` at currency level.

Set leverage for `cross/isolated` `FUTURES/SWAP` at underlying/contract level.

#### Rate Limit: 5 requests per 2 seconds

#### HTTP Request

`POST /api/v5/account/set-leverage`

> Request Example

```wiki
set leverage for isolated `MARGIN` at pairs level
POST /api/v5/account/set-leverage
body {"instId":"BTC-USDT","lever":"5","mgnMode":"isolated"}

set leverage for cross `MARGIN` in Single-currency margin at pairs level
POST /api/v5/account/set-leverage
body {"instId":"BTC-USDT","lever":"5","mgnMode":"cross"}

set leverage for cross `MARGIN` in Multi-currency margin at currency level
POST /api/v5/account/set-leverage
body {"ccy":"BTC","lever":"5","mgnMode":"cross"}

set leverage on long BTC-USDT-200802 for isolated `FUTURES`
POST /api/v5/account/set-leverage
body {"instId":"BTC-USDT-200802","lever":"5","posSide":"long","mgnMode":"isolated"}

set leverage for cross `FUTURES/SWAP` at underlying level
POST /api/v5/account/set-leverage
body {"instId":"BTC-USDT-200802","lever":"5","mgnMode":"cross"}
```

#### Request Parameters

| Parameter | Type   | Required | Description                                                                                                                                                                                                                              |
| :-------- | :----- | :------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| instId    | String | Optional | Instrument ID<br>Either `instId` or `ccy` is required; if both are passed, `instId` will be used by default.                                                                                                                             |
| ccy       | String | Optional | Currency used for margin<br />Only applicable to `cross` `MARGIN` of `Multi-currency margin`<br>                                                                                                                                         |
| lever     | String | Yes      | Leverage                                                                                                                                                                                                                                 |
| mgnMode   | String | Yes      | Margin mode<br>`isolated` `cross`<br /> Only can be `cross` if `ccy` is passed.                                                                                                                                                          |
| posSide   | String | Optional | Position side<br/>`long` `short` `net` <br/>Required in `long/short` mode and when margin mode is `isolated`, only `long` or `short` can be passed.<br /> Only `net` can be passed in other cases.<br/>Only applicable to `FUTURES/SWAP` |

> Example Response

```json
{
  "code": "0",
  "msg": "",
  "data": [
    {
      "lever": "30",
      "mgnMode": "isolated",
      "instId": "BTC-USDT-SWAP",
      "posSide": "long"
    }
  ]
}
```

#### Response Parameters

| Parameter | Type   | Description                       |
| :-------- | :----- | :-------------------------------- |
| lever     | String | Leverage                          |
| mgnMode   | String | Margin mode<br>`cross` `isolated` |
| instId    | String | Instrument ID                     |
| posSide   | String | Position side                     |

<aside class="notice">
When you want to set leverage for `cross` `FUTURES/SWAP` at the underlying level, you can pass in any instId and mgnMode(`cross`).
</aside>
