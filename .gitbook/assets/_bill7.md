### Get Bills Details (last 7 days)

Retrieve the bills of the account. The bill refers to all transaction records that result in changing the balance of an account. Pagination is supported, and the response is sorted with the most recent first. This endpoint can retrieve data from the last 7 days.

#### Rate Limit: 6 requests per second

#### HTTP Request

`GET /api/v5/account/bills`


> Request Example

```wiki
GET /api/v5/account/bills

GET /api/v5/account/bills?instType=MARGIN

```

#### Request Parameters

| Parameter   | Type   | Required | Description                                                         |
| :------- | :----- | :------- | :----------------------------------------------------------- |
| instType | String | No      | Instrument type<br/>`SPOT` <br/>`MARGIN`<br />`SWAP`<br>`FUTURES` <br/>`OPTION` |
| ccy      | String | No      | Currency                                                |
| mgnMode  | String | No      | Margin mode<br>`isolated`<br />`cross`     |
| ctType | String | No      | Contract type<br />`linear`<br />`inverse`<br />Only applicable to `FUTURES/SWAP` |
| type     | String | No      | Bill type<br>`1`: Transfer `2`: Trade `3`: Delivery `4`: Forced token conversion `5`: Liquidation `6`: Margin transfer `7`: Interest deduction `8`: Funding rate `9`: ADL `10`: Clawback |
| subType  | String | No      | Bill subtype<br>`1`: Buy `2`: Sell `3`: Open long `4`: Open short `5`: Close long `6`: Close short `9`: Interest deduction `11`: Transfer in `12`: Transfer out `160`: Manual margin increase `161`: Manual margin decrease `162`: Auto margin increase `110`: Forced buy `111`: Forced sell `100`: Partial liquidation close long `101`: Partial liquidation close short `102`: Partial liquidation buy `103`: Partial liquidation sell `104`: Liquidation long `105`: Liquidation short `106`: Liquidation buy `107`: Liquidation sell `109`: Liquidation fees `110`: Liquidation transfer in `111`: Liquidation transfer out `125`: ADL close long `126`: ADL close short `127`: ADL buy `128`: ADL sell `170`: Exercised `171`: Counterparty exercised `172`: Expired OTM `112`: Delivery long `113`: Delivery short `117`: Delivery/Exercise clawback  |
| after    | String | No      | Pagination of data to return records earlier than the requested bill ID. |
| before   | String | No      | Pagination of data to return records newer than the requested bill ID. |
| limit    | String | No      | Number of results per request. The maximum is `100`. The default is `100`. |


> Example Response

```json
{
	"code": "0",
	"msg": "",
	"data": [{
			"instType": "FUTURES",
			"instId": "BTC-USD-180216",
			"billId": "1234",
			"type": "1",
			"subType": "1",
			"balChg": "0.2",
			"bal": "0.3",
			"sz": "0.23",
			"ccy": "BTC",
			"mgnMode": "isolated",
			"pnl": "1",
			"fee": "0.01",
			"ts": "1597026383085",
			"ordId": "332233",
			"from": "",
			"to": "",
			"notes": ""
		}
	]
}
```


#### Response Parameters

| Parameter  | Type   | Description                                                         |
| :------ | :----- | :----------------------------------------------------------- |
| instType | String | Instrument type                                                     |
| billId  | String | Bill ID                                             |
| type    | String | Bill type                                              |
| subType | String | Bill subtype                                      |
| ts      | String | Creation time, Unix timestamp format in milliseconds, e.g.`1597026383085` |
| balChg  | String | Change in balance amount at the account level |
| posBalChg | String | Change in balance amount at the position level |
| bal     | String | Balance at the account level                          |
| posBal | String | Balance at the position level |
| sz      | String | Quantity                                            |
| ccy     | String | Account balance currency                   |
| pnl     | String | Profit and loss                                     |
| fee     | String | Fee<br>Negative number represents the user transaction fee charged by the platform. <br />Positive number represents rebate. |
| mgnMode | String | Margin mode<br>`isolated` `cross`<br>When bills are not generated by position changes, the field returns "" |
| instId  | String | Instrument ID, e.g. `BTC-USD-190927-5000-C`      |
| ordId   | String | Order ID<br />When bill type is not `trade`, the field returns "" |
| from      | String | The remitting account<br>`1`: SPOT  `3`: FUTURES `5`: MARGIN  `6`: FUNDING   `9`: SWAP `12`: OPTION `18`: Portfolio Margin<br>When bill type is not `transfer`, the field returns "". |
| to        | String | The beneficiary account<br>`1`: SPOT  `3`: FUTURES `5`: MARGIN  `6`: FUNDING   `9`: SWAP `12`: OPTION `18`: Portfolio Margin<br>When bill type is not `transfer`, the field returns "". |
| notes     | String | Notes<br>When bill type is not `transfer`, the field returns "". |