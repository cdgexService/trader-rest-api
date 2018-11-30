# CDGEX资产管理平台 API 文档

---

## URL: https://www.cdgex.com/
---

## 获取 ticker 列表

Name | Description
---|---
Method | GET

URL:
```json
/v1/tickers
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
            "buy":null		       	   #当前买入价
            ,"high":0,                 #最价高
            "high24h":0,               #24小时最高价
            "low":0,                   #最低价
            "low24h":0,                #24小时最低价
            "last":0,                  #最新成交价
            "last24h":0,               #24小时最新成交价
            "vol":0,                   #当前交易量
            "vol24h":0                 #24小时交易量
        },
		...
    ]
}
```

## 获取 ticker

Name | Description
---|---
Method | GET

URL:
```json
/v1/ticker?symbol=<symbol>
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
            "buy":null		       	   #当前买入价
            ,"high":0,                 #最价高
            "high24h":0,               #24小时最高价
            "low":0,                   #最低价
            "low24h":0,                #24小时最低价
            "last":0,                  #最新成交价
            "last24h":0,               #24小时最新成交价
            "vol":0,                   #当前交易量
            "vol24h":0                 #24小时交易量
        },
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
/v1/depth?symbol=<symbol>&size=<size>
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

## 获取实时成交列表
Name | Description
---|---
Method | GET


URL:
```json
/v1/trades?symbol=<symbol>&size=<size>
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

## 获取K线数据
Name | Description
---|---
Method | GET
period | latest/hr1/hr2/hr6/min1/min5/min15/min30/day1/day3/week

URL:
```json
/v1/candlestick?symbol=<symbol>&period=<period>&size=<size>
```

Return:
```json
{
    "success": true,
	"data":[
		[1543539600000,244000000,2748526,2750731,2740930,2750077],
		[1543543200000,255000000,2750077,2761029,2745581,2757926],
		[1543546800000,218000000,2757926,2771524,2757926,2767329],
		[1543550400000,224000000,2767329,2768773,2756580,2766876],
		...
	]
}
```
