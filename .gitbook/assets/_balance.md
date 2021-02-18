### Get Balance

Retrieve a list of assets (with non-zero balance), remaining balance, and available amount in the account.

<aside class="notice">
Interest-free quota and discount rates are public data and not displayed on the account interface.
</aside>

#### Rate Limit: 20 requests per 2 seconds

#### HTTP Requests

`GET /api/v5/account/balance`

> Request Example

```wiki
Get the balance of all assets in the account
GET /api/v5/account/balance

Get the balance of BTC and ETH assets in the account
GET /api/v5/account/balance?ccy=BTC,ETH

```

##### Request Parameters

| **Parameters** | **Types** | **Required** | **Description**                                                                                         |
| :------------- | :-------- | :----------- | :------------------------------------------------------------------------------------------------------ |
| ccy            | String    | No           | Single currency or multiple currencies (no more than 20) separated with comma, e.g. `BTC` or `BTC,ETH`. |

> Example Response

```json
{
  "code": "0",
  "msg": "",
  "data": [
    {
      "uTime": "1597026383085",
      "totalEq": "41624.32",
      "isoEq": "3624.32",
      "adjEq": "41624.32",
      "imr": "4162.33",
      "mmr": "4",
      "mgnRatio": "41624.32",
      "details": [
        {
          "ccy": "BTC",
          "eq": "123",
          "isoEq": "",
          "availEq": "1234",
          "availBal": "",
          "frozenBal": "14",
          "ordFrozen": "12",
          "upl": "124",
          "uplLiab": "0",
          "mgnRatio": "",
          "interest": "12",
          "liab": "1"
        },
        {
          "ccy": "ETH",
          "eq": "223",
          "isoEq": "",
          "availEq": "2234",
          "availBal": "",
          "frozenBal": "141",
          "ordFrozen": "12",
          "upl": "124",
          "uplLiab": "0",
          "mgnRatio": "",
          "interest": "0",
          "liab": "0"
        }
      ]
    }
  ]
}
```

##### Response Parameters

| **Parameters** | **Types** | **Description**                                                                                                   |
| -------------- | --------- | ----------------------------------------------------------------------------------------------------------------- |
| uTime          | String    | The latest time to get account information, millisecond format of Unix timestamp, e.g. `1597026383085`            |
| totalEq        | String    | Total equity in USD level                                                                                         |
| isoEq          | String    | Isolated margin equity in USD level<br/>Applicable to `Single-currency margin` and `Multi-currency margin`        |
| adjEq          | String    | Adjusted/Effective equity in USD level<br/>Applicable to `Multi-currency margin`                                  |
| imr            | String    | Initial margin requirement in USD level<br/>Applicable to `Multi-currency margin`                                 |
| mmr            | String    | Maintenance margin requirement in USD level <br/>Applicable to `Multi-currency margin`                            |
| mgnRatio       | String    | Margin ratio in USD level <br/>Applicable to `Multi-currency margin`                                              |
| details        | Array     | Detailed asset information in all currencies                                                                      |
| > ccy          | String    | Currency                                                                                                          |
| > eq           | String    | Equity of the currency                                                                                            |
| > isoEq        | String    | Isolated margin equity of the currency<br/>Applicable to `Single-currency margin` and `Multi-currency margin`     |
| > availEq      | String    | Available equity of the currency<br/>Applicable to `Single-currency margin` and `Multi-currency margin`           |
| > availBal     | String    | Available balance of the currency<br/>Applicable to `Simple`                                                      |
| > frozenBal    | String    | Frozen balance of the currency                                                                                    |
| > ordFrozen    | String    | Margin frozen for open orders                                                                                     |
| > liab         | String    | Liabilities of the currency<br/>Applicable to `Multi-currency margin`                                             |
| > upl          | String    | Unrealized profit and loss of the currency<br/>Applicable to `Single-currency margin` and `Multi-currency margin` |
| > uplLib       | String    | Liabilities due to Unrealized loss of the currency<br/>Applicable to `Multi-currency margin` |
| > mgnRatio     | String    | Margin ratio of the currency<br/>Applicable to `Single-currency margin`                                           |
| > interest     | String    | Interest of the currency<br>Applicable to `Multi-currency margin`                                                 |

<aside class="notice">
"" will be returned for inapplicable fields under the current account level.
</aside>

Distribution of applicable fields under each account level are as follows:

| **Parameters** | Simple | Single-currency margin | Multi-currency margin |
| :------------- | :------------- | :--------------------- | :-------------------- |
| uTime          | Yes            | Yes                    | Yes                   |
| totalEq        | Yes            | Yes                    | Yes                   |
| isoEq          |                | Yes                    | Yes                   |
| adjEq          |                |                        | Yes                   |
| imr            |                |                        | Yes                   |
| mmr            |                |                        | Yes                   |
| mgnRatio       |                |                        | Yes                   |
| details        |                |                        |                       |
| > ccy          | Yes            | Yes                    | Yes                   |
| > eq           | Yes            | Yes                    | Yes                   |
| > isoEq        |                | Yes                    | Yes                   |
| > availEq      |                | Yes                    | Yes                   |
| > availBal     | Yes            |                        |                       |
| > frozenBal    | Yes            | Yes                    | Yes                   |
| > ordFrozen    | Yes            | Yes                    | Yes                   |
| > liab         |                |                        | Yes                   |
| > upl          |                | Yes                    | Yes                   |
| > upl          |                |                        | Yes                   |
| > mgnRatio     |                | Yes                    |                       |
| > interest     |                |                        | Yes                   |
