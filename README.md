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
    "success": "true",
    "data": [
        {
            "market": <trading_pair>,  #交易对名称 
            "date": 1540360609022,     #当前时间 
            "sell":null,               #当前卖出价
            "buy":null		       #当前买入价
            ,"high":0,                 #最价高
            "high24h":0,               #24小时最高价
            "low":0,                   #最低价
            "low24h":0,                #24小时最低价
            "last":0,                  #最新成交价
            "last24h":0,               #24小时最新成交价
            "vol":0,                   #当前交易量
            "vol24h":0                 #24小时交易量
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
        "market":<trading_pair>,                #交易对名称
        "buy":[
			[
				3138900,        #价格
				15000000,       #数量
				15000000        #总数量
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
			"trader":<trader_api_key>,                  #交易对名称
			"assets":
			[
				{
					"asset":<asset>,            #币种名称
					"balance":"2000000000",     #余额
					"available":"1999900000"    #可用数量
					"frozen":"100000",          #冻结数量
					"state":"1"                 #状态默认为1正常
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
    "trading_pair":<trading_pair>,          #交易对名称
    "side":<BUY|SELL>,                      #方向 BUY 或 SELL
    "vol":<vol>,                            #下单数量
    "price":<price>,                        #下单价格
    "type":"limit"                          #下单类型，默认为 limit 限价
}
```

URL:
```json
/v1/order
```

Return:
```json
{
    "success": true,                       #状态
    "result": <order_id>                   #订单 ID
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
    "success": true,                #状态
    "data":
	[
		id1,                #订单 ID
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
    "trading_pair":<trading_pair>,         #交易对名称
    "order_ids":
	[
		id1,                       #订单 ID
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
    "success": true,                   #状态
    "data": <order_id>                 #最新的订单 ID
}
```
