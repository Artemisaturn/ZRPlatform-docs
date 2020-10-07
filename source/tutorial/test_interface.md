# 测试数据库接口文档

### 说明：

所有url前面省略[__http://127.0.0.1:8000/api/v1__](http://127.0.0.1:8000/api/v1)

### 导出测试数据库中所有表名

- `**请求方法**`：POST

- `**接口地址**`/measuringData/getIndexes

- 入参：

无需入参

- 出参：

// 自动遍历数据库所有表，获取其中所有表名

```json
{
    "code": 200,
    "message": "",
    "data": [
        {
            "value": "material",
            "label": "材料主表"
        },
        {
            "value": "elastic_parameter",
            "label": "弹性参数表"
        },
        {
            "value": "physical_parameter",
            "label": "物理参数表"
        },
        {
            "value": "tensile_property",
            "label": "拉伸性能表"
        },
        {
            "value": "creep_property",
            "label": "蠕变性能表"
        },
        {
            "value": "low_cycle_fatigue_parameter",
            "label": "低周疲劳参数表"
        },
        {
            "value": "hill_stress_coefficient",
            "label": "Hill应力系数表"
        },
        {
            "value": "hcf",
            "label": "Hcf表"
        },
        {
            "value": "cyclic_stress_strain_curve",
            "label": "循环应力应变曲线表"
        },
        {
            "value": "crack_propagation",
            "label": "裂纹扩展表"
        },
        {
            "value": "oxidation_resistance",
            "label": "抗氧化性能表"
        },
        {
            "value": "stress_amplitude",
            "label": "应力幅值表"
        }
    ]
}
```

备注：表名的value可以用来继续post到/measuringData/tableContents接口，获取某材料牌号的相关数据

### 按材料牌号和表名查询数据

- `**请求方法**`：POST

- `**接口地址**`/measuringData/tableContents

- 入参：

```json
{
	"brand_name":"材料牌号",
	"search_attribute":"表名"
}
```

- 出参：

```json
{
	"code": 200,
	"message":"",
	// **table_name** 显示请求表的中文名称
	"table_name":"table name Chinese",
	// **title_mapping** 用于做表头名称映射
	"title_mapping":{ // 表头变量名：中文名称
		"title1":"verbose_name1",
		"title2":"verbose_name2",
		...
	},
	// **data** 所对应数组为每一条被查询到的数据
	"data":[
		{ // 第一条数据
			"title1":"value1of1",
			"title2":"value2of1",
			...
		},
		{ // 第二条数据
			"title1":"value1of2",
			"title2":"value2of2",
			...

		},
			... // 其余条目
	]
}

```

- 备注：

### 按材料牌号和表名查询数据-多级表头

- `**请求方法**`：POST

- `**接口地址**`/measuringData/tableContents

- 入参：

```json
{
	"brand_name":"材料牌号",
	"search_attribute":"表名"
}
```

- 出参：

```json
{
	"code": 200,
	"message":"",
	// **table_name** 显示请求表的中文名称
	"table_name":"table name Chinese",
	// **title_mapping** 用于做表头名称映射
	"title_mapping":{ // 遍历 一级表头
		"title1":
		{
			"verbose_name": "verbose_name1"，
			"children":[ // 遍历 二级表头
			{
				"title1of1":{
					"verbose_name":"verbose_name1of1",
					"children":[...] // 遍历 三级表头
				},
				"title2of1":{...}
			},
				...
			],
		},
		"title2":{...},
		...
	},
	// **data** 所对应数组为每一条被查询到的数据
	"data":[
		{ // 第一条数据
			"title1":"value1of1",
			"title2":"value2of1",
			...
		},
		{ // 第二条数据
			"title1":"value1of2",
			"title2":"value2of2",
			...

		},
		... // 其余条目
	]
}

```

- 备注：

### 获取材料主表中所有信息

- `**请求方法**`：POST

- `**接口地址**`/measuringData/getAll

- 入参：

无需入参

- 出参：

// 自动遍历材料主表，获得材料主表中的所有信息，并且有title_mapping

```json
{
    "code": 200,
    "message": "",
    "title_mapping": [
        "材料基本信息",
        {
            "name": "材料牌号",
            "parts": "部件",
            "category": "材料类别",
            "intensity_grade": "强度等级",
            "direction": "材料方向",
            "standard": "材料标准",
            "remarks": "备注"
        }
    ],
    "data": [
        {
            "id": 1,
            "name": "DZ101",
            "parts": null,
            "category": null,
            "intensity_grade": null,
            "direction": null,
            "standard": null,
            "remarks": null
        },
        {
            "id": 2,
            "name": "DZ102",
            "parts": null,
            "category": null,
            "intensity_grade": null,
            "direction": null,
            "standard": null,
            "remarks": null
        },
        {
            "id": 3,
            "name": "DZ103",
            "parts": null,
            "category": null,
            "intensity_grade": null,
            "direction": null,
            "standard": null,
            "remarks": null
        },
        {
            "id": 4,
            "name": "DZ104",
            "parts": null,
            "category": null,
            "intensity_grade": null,
            "direction": null,
            "standard": null,
            "remarks": null
        },
        {
            "id": 5,
            "name": "DZ106",
            "parts": null,
            "category": null,
            "intensity_grade": null,
            "direction": null,
            "standard": null,
            "remarks": null
        }
    ]
}
```

备注：如果只想获取材料牌号，那么通过该接口获得数据后，自行处理即可


### TODO:增加数据



