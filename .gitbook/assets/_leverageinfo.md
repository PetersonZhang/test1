### Get Leverage


#### Rate Limit: 20 requests per 2 seconds

#### HTTP Request

`GET /api/v5/account/leverage-info`


> Request Example

```wiki
GET /api/v5/account/leverage-info?instId=BTC-USDT-200626&mgnMode=cross

```

#### Request Parameters

| Parameter  | Type   | Required | Description                                       |
| :------ | :----- | :------- | :----------------------------------------- |
| instId  | String | Yes       | Instrument ID                                 |
| mgnMode | String | Yes       | Margin mode<br>`cross` `isolated`|


> Example Response

```json
{
	"code": "0",
	"msg": "",
	"data": [{
		"instId": "BTC-USDT-200626",
		"mgnMode": "cross",
		"posSide": "long",
		"lever": "10"
	},{
		"instId": "BTC-USDT-200626",
		"mgnMode": "cross",
		"posSide": "short",
		"lever": "10"
	}]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                     |
| :--------- | :------- | :----------------------------------------------------------- |
| instId     | String   | Instrument ID                                                   |
| mgnMode    | String   | Margin mode                                                   |
| posSide    | String   | Position side<br/>`long`<br />`short`<br />`net`<br>Only applicable to `FUTURES/SWAP`<br>In `long/short` mode, the leverage in both directions `long` `short` will be returned. |
| lever      | String   | Leverage                                       |

