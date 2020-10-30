# 意见反馈接口测试

### 获取意见反馈表中的id，标题，用户名，状态，时间等基本信息

```请求方法```：GET

```接口地址```：/feedback/traversal

入参：无需入参

出参：遍历表中所有数据，获取基本信息

```json
[
    {
        "id": 3,
        "title": "1",
        "username": "Artemisaturn",
        "status": 0,
        "time": "2020-10-29T10:32:07.138000+08:00"
    },
    {
        "id": 4,
        "title": "2",
        "username": null,
        "status": 0,
        "time": "2020-10-29T10:31:17.460000+08:00"
    },
    {
        "id": 5,
        "title": "feedback",
        "username": "ZR",
        "status": 0,
        "time": "2020-10-29T13:33:59.717000+08:00"
    },
    {
        "id": 6,
        "title": "6",
        "username": null,
        "status": 0,
        "time": "2020-10-29T16:35:59.118000+08:00"
    }
]
```

### 获取详细内容和附件

```请求方法```：POST

```接口地址```：/feedback/getmore

入参：反馈意见的id

```json
{
    "id" : 3
}
```

出参：该反馈意见的详情和附件

```content```：意见详情

```files```：附件list

```url```：附件路径

```filename```：附件名

```json
{
    "code": 200,
    "message": "",
    "data": {
        "title": "1",
        "username": "Artemisaturn",
        "status": 0,
        "time": "2020-10-29T02:32:07.138000Z",
        "content": "<p>try</p>",
        "files": [
            {
                "filename": "工业智能方向.docx",
                "url": "/media/feedback/file/2020-10-29/工业智能方向.docx"
            },
            {
                "filename": "采矿组修改中文.docx",
                "url": "/media/feedback/file/2020-10-29/采矿组修改中文.docx"
            },
            {
                "filename": "人机交互组研究方向2.docx",
                "url": "/media/feedback/file/2020-10-29/人机交互组研究方向2.docx"
            }
        ]
    }
}
```

没有附件的情况：

入参：

```json
{
    "id" : 6
}
```

出参：

```json
{
    "code": 200,
    "message": "",
    "data": {
        "title": "6",
        "username": null,
        "status": 0,
        "time": "2020-10-29T08:35:59.118000Z",
        "content": "<p>try</p>",
        "files": []
    }
}
```

若反馈意见不存在：

入参：

```json
{
    "id" : 1
}
```

出参：

```json
{
    "code": 10010,
    "message": "该反馈意见不存在!"
}
```

### 下载附件

```请求方法```：POST

```接口地址```：/feedback/filedown

入参：文件名和文件路径

```json
{
    "url": "/media/feedback/file/2020-10-29/人机交互组研究方向2.docx",
    "filename": "人机交互组研究方向2.docx"
}
```

出参：return  StreamingHttpResponse类

