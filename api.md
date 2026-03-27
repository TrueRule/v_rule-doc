#### 引擎核心接口
该接口通过动态参数来请求不同的决策引擎来获取对应场景的风控结果。

##### `URL`
```
http://localhost:8081/scene/line/{line}/field/{scene_field}
```

##### 请求方式
```
POST
```

##### 请求体
```json
{
    "basic_info": {
        "idNumber": "", // 必传
        "username": "", // 必传
        "mobile": "", // 必传
        "channelFrom": ""
    },
    "device_info": {
        "imei": ""
    },
    "extract_info": {
        "extract_field_1": "",
        "extract_field_2": 0,
    }
}
```

##### 响应体
```json
{
    "status": 200,
    "reqId": "4cdf07a2d6234c9e846756f976023d85", // 接口响应ID，需保存此值，后续功能有使用
    "msg": "",
    "data":
    {
        "code": 200, // 状态码
        "message": "", // 响应信息
        "finalDecision": "accept", // 最终风控结果
        "record": {}, // 场景运行记录
        "dataUsedMap":
        {
            "SJY26010500001": 82,
            "SJY26010500002": "extract"
        }, // 场景运行过程中使用到的数据源编码和对应的值
        "hitRuleList":
        [
            "GZ26010500002",
            "GZ26010500003",
            "GZJ26010500002"
        ], // 场景运行过程中命中的规则、规则集、规则树
        "hitStrategyList":
        [
            "CL26010500001",
            "CL26010500002"
        ], // 场景运行过程中命中的策略集
        "interest":
        {
            "unit": "‱",
            "interest": "35",
            "remark": "利率备注"
        }, // 利率产品
        "period":
        {
            "period": "14",
            "unit": "day",
            "remark": "账期备注"
        }, // 账期产品
        "limit":
        {
            "limit": "1500",
            "remark": "额度备注"
        }, // 额度产品
        "custom":
        {
        	"a": "1",
        	"b": "2"
        } // 自定义产品
    }
}
```

<hr>

#### 数据缓存接口
该接口可根据引擎核心接口的 `reqId` 参数实时返回引擎计算过程中使用到的所有数据。（该接口可用于模型计算时使用）

##### `URL`
```
http://localhost:8081/data/cache/{reqId}
```

##### 请求方式
```
POST
```

##### 响应体
```json
{
	"status": 200,
	"reqId": "135c27212f024898ba742e1410f93820",
	"msg": "success",
	"data": {
		"local": {
			"userInfo": {},
			"orderInfo": {},
			"deviceInfo": {
				"imei": ""
			},
			"extractInfo": {
				"extract_field_1": "",
				"extract_field_2": 0,
			},
			"basicInfo": {
				"reqId": "", // 与请求URL 的reqId 一致
				"channelFrom": "",
				"mobile": "",
				"idNumber": "",
				"username": "",
				"randomRealKey": 82, // 真随机数，引擎自带
				"randomKey": 278 // 假随机数，引擎自带
			}
		},
		"http": {
			"h1": {
				"code": 200
			}
		},
		"python": {
			"p1": {
				"a": 1,
				"b": "b"
			}
		}
	}
}
```