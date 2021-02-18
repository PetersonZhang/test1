### Set Greeks (PA/BS)

Set the display type of Greeks.

#### Rate Limit: 5 requests per 2 seconds

#### HTTP Request

`POST /api/v5/account/set-greeks`


> Request Example

```wiki
POST /api/v5/account/set-greeks 
body {"greeksType":"PA"}

```


#### Request Parameters

| Parameter     | Type   | Required | Description                                           |
| :--------- | :----- | :------- | :--------------------------------------------- |
| greeksType | String | Yes       | Display  type of Greeks.<br>`PA`: Greeks in coins<br />`BS`: Black-Scholes Greeks in dollars |


> Example Response

```json
{
	"code": "0",
	"msg": "",
	"data": [{
		"greeksType": "PA"
	}]
}
```

#### Response Parameters

| Parameter     | Type   | Description                 |
| :--------- | :----- | :------------------- |
| greeksType | String | Display type of Greeks. |

