### Set Position mode

`FUTURES` and `SWAP` support both `long/short` mode and `net` mode. In `net` mode, users can only have positions in one direction; In `long/short` mode, users can hold positions in long and short directions.

#### Rate Limit: 5 requests per 2 seconds

#### HTTP Request

`POST /api/v5/account/set-position-mode`


> Request Example

```wiki
POST /api/v5/account/set-position-mode
{"posMode":"long_short_mode"}

```

#### Request Parameters

| Parameter  | Type | Required | Description                                                       |
| :------ | :------- | :------- | :--------------------------------------------------------- |
| posMode | String   | Yes       | Position mode<br>`long_short_mode`: long/short, only applicable to `FUTURES/SWAP`<br/>`net_mode`: net |


> Example Response

```json
{
	"code": "0",
	"msg": "",
	"data": [{
		"posMode": "long_short_mode"
	}]
}
```


#### Response Parameters

| Parameter  | Type   | Description     |
| :------ | :----- | :------- |
| posMode | String | Position mode |



