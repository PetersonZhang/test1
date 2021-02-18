### Increase/Decrease margin

Increase or decrease the margin of the isolated position.

#### Rate Limit: 20 requests per 2 seconds

#### HTTP Request

`POST /api/v5/account/position/margin-balance`


> Request Example

```wiki
POST /api/v5/account/position/margin-balance 
body {"instId":"BTC-USDT-200626","posSide":"short","type":"add","amt":"1"}

```


#### Request Parameters

| Parameter  | Type   | Required | Description                                                         |
| :------ | :----- | :------- | :----------------------------------------------------------- |
| instId  | String | Yes       | Instrument ID                                                       |
| posSide | String | Yes       | Position side, the default is `net`<br/>`long`<br />`short`<br />`net` |
| type    | String | Yes       | Type<br>`add`   `reduce`          |
| amt     | String | Yes       | Amount to be increased or decreased.   |


> Example Response

```json
{
	"code": "0",
	"msg": "",
	"data": [{
		"instId": "BTC-USDT-200626",
		"posSide": "short",
		"amt": "1",
		"type": "add"
	}]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                |
| :--------- | :------- | :-------------------------------------- |
| instId     | String   | Instrument ID                              |
| posSide    | String   | Position side, `long`  `short` |
| amt        | String   | Amount to be increase or decrease |
| type       | String   | Type                      |

