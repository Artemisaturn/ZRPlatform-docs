# 推荐材料数据库接口文档

### 返回推荐材料数据库中的所有公司及其所有推荐材料（拼接牌号）
- `**请求方法**`: POST

- `**接口地址**`: api/v1/rec_material/company-material

- 入参(无需入参)：

- 出参：
```json
{
    "code": 200,
    "msg": "",
    "data": [
        {
            "company-name": "aen",
            "company-name-to-show": "AEN",
            "company-material-num": 2,
            "company-materials": [
                "1_1_1",
                "2_2_2"
            ]
        },
        {
            "company-name": "siemens",
            "company-name-to-show": "Siemens",
            "company-material-num": 0,
            "company-materials": []
        }
    ]
}
```
