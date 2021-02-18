### Get Account Configuration

Retrieve current account configuration.

#### Rate Limit: 5 requests per 2 seconds

#### HTTP Request

`GET /api/v5/account/config`

> Request Example

```wiki
GET /api/v5/account/config

```

#### Request Parameters

none

> Example Response

```json
{
  "code": "0",
  "msg": "",
  "date": [
    {
      "uid": "43812",
      "acctLv": "2",
      "posMode": "long_short_mode",
      "autoLoan": true,
      "greeksType": "BS"
    }
  ]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                                                                     |
| :------------ | :------- | :------------------------------------------------------------------------------------------------------------------ |
| uid           | String   | Account ID                                                                                                          |
| acctLv        | String   | Account level <br>`1`: Simple `2`: Single-currency margin `3`: Multi-currency margin                                |
| posMode       | String   | Position mode<br>`long_short_mode`: long/short, only applicable to `FUTURES/SWAP` <br/>`net_mode`: net              |
| autoLoan      | Boolean  | Whether to borrow coins automatically<br>`true`: borrow coins automatically `false`: not borrow coins automatically |
| greeksType    | String   | Current display type of Greeks<br>`PA`: Greeks in coins `BS`: Black-Scholes Greeks in dollars                       |
