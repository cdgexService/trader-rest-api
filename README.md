# CDGEX资产管理平台 API 文档

---


---

## 获取 ticker 列表

Name | Description
---|---
Method | GET
Authorize | False

URL:
```json
/v1/ticker?trading_pair=<trading_pair>
```

Return:
```json

{
    "success": true | False,
    "data": [
        {
            "market": <trading_pair>,   
            "date": 1540360609022,      
            "sell":null,                
            "buy":null
            ,"high":0,
            "high24h":0,
            "low":0,
            "low24h":0,
            "last":0,
            "last24h":0,
            "vol":0,
            "vol24h":0
        }
    ]
}
```

## 获取深度列表

Name | Description
---|---
Method | GET
Authorize | False

URL:
```json
/v1/depth?trading_pair=<trading_pair>
```

Return:
```json
{
    "success": true || false,
    "data":{
        "market":<trading_pair>,
        "buy":[
			[
				3138900,
				15000000,
				15000000
			],
			[
				3139000,
				100000000,
				115000000
			],
			...
		],
        "sell":[
			[
				3138900,
				15000000,
				15000000
			],
			[
				3139000,
				100000000,
				115000000
			],
			...
		]
    }
}
```

## 获取用户余额

Name | Description
---|---
Method | GET
Authorize | True
Headers | True

Headers:
```json
{
    "api_key":<api_key>,
    "secret":<secret>
}
```

URL:
```json
/v1/user/balance
```

Return:
```json
{
    "success": true
    "data":
		{
			"trader":<trader_api_key>,
			"assets":
			[
				{
					"asset":<asset>,
					"balance":"2000000000",
					"available":"1999900000"
					"frozen":"100000",
					"state":"1"
				},
				...
			]
		}
}
```

## 创建订单

Name | Description
---|---
Method | POST
Authorize | True
Body | True
Headers | True

Headers:
```json
{
    "api_key":<api_key>,
    "secret":<secret>
}
```

Body:
```json
{
    "trading_pair":<trading_pair>,
    "side":<BUY|SELL>,
    "vol":<vol>,
    "price":<price>,
    "type":"limit"
}
```

URL:
```json
/v1/order
```

Return:
```json
{
    "success": true,
    "result": <order_id>
}
```

## 获取当前活动订单
Name | Description
---|---
Method | GET
Authorize | True

Headers:
```json
{
    "api_key":<api_key>,
    "secret":<secret>
}
```

URL:
```json
/v1/orders?trading_pair=<trading_pair>
```

Return:
```json
{
    "success": true,
    "data":
	[
		id1,
		id2,
		id3,
		...
	]
}
```

## 撤销订单
Name | Description
---|---
Method | DELETE
Authorize | True
Body | True
Headers | True

Headers:
```json
{
    "api_key":<api_key>,
    "secret":<secret>
}
```

Body:
```json
{
    "trading_pair":<trading_pair>,
    "order_ids":
	[
		id1,
		id2,
		id3,
		...
	]
}
```

URL:
```json
/v1/order
```

Return:
```json
{
    "success": true,
    "data": <order_id>
}
```
