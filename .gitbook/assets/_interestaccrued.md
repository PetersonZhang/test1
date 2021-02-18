### Get interest-accrued


#### Rate Limit: 5 requests per 2 seconds

#### HTTP Request

`GET /api/v5/account/interest-accrued`


> Request Example

```wiki
GET /api/v5/account/interest-accrued

```



#### Request Parameters

| Parameter  | Type   | Required | Description                                                   |
| :------ | :----- | :------- | :----------------------------------------------------- |
| instId  | String | No       | Instrument ID, e.g. `BTC-USDT`<br />Only applicable to `MARGIN` |
| ccy     | String | No       | Currency, e.g. `BTC`                                 |
| mgnMode | String | No       | Margin mode<br>`cross`  `isolated`           |
| after   | String | No       | Pagination of data to return records earlier than the requested ts, Unix timestamp format in milliseconds, e.g. `1597026383085` |
| before  | String | No       | Pagination of data to return records newer than the requested ts, Unix timestamp format in milliseconds, e.g. `1597026383085` |
| limit   | String | No       | Number of results per request. The maximum is `100`; The default is `100`     |


> Example Response

```json
{
	"code": "0",
	"msg": "",
	"data": [{
			"instId": "BTC-USDT",
			"ccy": "USDT",
			"mgnMode": "cross",
			"interest": "0.02",
			"ts": "1597026383085"
		},
		{
			"instId": "BTC-USDT",
			"ccy": "USDT",
			"mgnMode": "cross",
			"interest": "0.02",
			"ts": "1597026383085"
		}
	]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                              |
| :--------- | :------- | :---------------------------------------------------- |
| instId     | String   | Instrument ID |
| ccy        | String   | Currency                                          |
| mgnMode    | String   | Margin mode                                  |
| interest   | String   | Interest                                         |
| ts         | String   | Interest calculation time, Unix timestamp format in milliseconds, e.g. `1597026383085`     |
