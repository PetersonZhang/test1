### Get Fee Rates


#### Rate Limit: 5 requests per 2 seconds

#### HTTP Request

`GET /api/v5/account/trade-fee`


> Request Example

```wiki 
Query trade fee rate of SPOT BTC-USDT
GET /api/v5/account/trade-fee?instType=SPOT&instId=BTC-USDT
  
Query trade fee rate in Tier 1
GET /api/v5/account/trade-fee?instType=SWAP&category=1

```


#### Request Parameters

| Parameter   | Type   | Required | Description                                                         |
| :------- | :----- | :------- | :----------------------------------------------------------- |
| instType | String | Yes       | Instrument type<br/>`SPOT `<br />`MARGIN`<br />`SWAP`<br />`FUTURES`<br />`OPTION` |
| instId   | String | Optional     | Instrument ID, e.g. `BTC-USDT`<br>only applicable to`FUTURES/SWAP/OPTION` |
| uly        | String | Optional     | Underlying, e.g. `BTC-USD`<br>only applicable to`FUTURES/SWAP/OPTION` |
| category | String | Optional     | Fee Schedule<br />`1`: Tier 1<br />`2`: Tier 2 <br />`3`: Tier 3<br />`4`: Tier 4 |



<aside class="notice">
At least and only one of instId, uly, and category is allowed to be passed.
</aside>



> Example Response

```json
{
	"code": "0",
	"msg": "",
	"data": [{
            "category": "1",
            "delivery": "",
            "exercise": "",
            "instType": "SPOT",
            "level": "101",
            "maker": "-0.001",
            "taker": "-0.0015",
            "ts": "1608623351857"
        }
	]
}
```

#### Response Parameters

| **Parameter** | **Type** | **Description**                                                 |
| ---------- | -------- | -------------------------------------------------------- |
| category   | String   | Fee Schedule                                   |
| taker      | String   | Taker fee rate                              |
| maker      | String   | Maker fee rate                                 |
| delivery   | String   | Delivery fee rate                              |
| exercise   | String   | Fee rate for exercising the option             |
| level      | String   | Fee rate Level           |
| instType   | String   | Instrument type                                     |
| ts         | String   | Data return time, Unix timestamp format in milliseconds, e.g. `1597026383085` |

