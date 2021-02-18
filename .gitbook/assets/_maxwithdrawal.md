### Get Maximum Withdrawals

Retrieve the maximum transferable amount.

#### Rate Limit: 20 requests per 2 seconds

#### HTTP Request

`GET /api/v5/account/max-withdrawal`


> Request Example

```wiki
GET /api/v5/account/max-withdrawal

```


#### Request Parameters

| Parameter | Type   | Required | Description           |
| :----- | :----- | :------- | :------------- |
| ccy    | String | No       | Currency, e.g. `BTC` |

> Example Response

```json
{
	"code": "0",
	"msg": "",
	"data": [{
			"ccy": "BTC",
			"maxWd": "124"
		},
		{
			"ccy": "ETH",
			"maxWd": "10"
		}
	]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**       |
| :--------- | :------- | :------------- |
| maxWd      | String   | Max withdrawal |
| ccy        | String   | Currency   |
