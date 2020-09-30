# 测试数据库前端使用方法

## 后端平台部署

## 运行环境

在后端平台根目录下使用命令行运行命令：

```shell
Python manage.py runserver
```

启动后端平台，此时后端平台运行在 `127.0.0.1:8000` 上，可用浏览器直接访问进入。

## 测试数据导入

当前提供**测试数据库**数据共有的 *材料主表*、*拉伸性能表*、*低周疲劳参数表 *三个数据库表数据（见`fakedata.zip`），下面以材料主表为例，展示如何导入数据。（**注：须先导入材料主表再导入其余表数据，其余子表的材料牌号字段都外键到了材料主表中**）

![](https://tcs-ga.teambition.net/storage/111x11cab4c266c650e5e7a34752c87513a4?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzEyOCwiaWF0IjoxNjAxMzk4MzI4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgxMWNhYjRjMjY2YzY1MGU1ZTdhMzQ3NTJjODc1MTNhNCJ9.FVWEEN_pSPAnEmEn4y8gfSb1Mbxi467-tWvtEU-rels&download=image.png "")

进入后端主页，选择测试数据管理（对应Django中的App MeasutingData），选择材料主表，选择导入：

![](https://tcs-ga.teambition.net/storage/111x5544abf4c7cba1723672095bd47e2aa9?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzEyOCwiaWF0IjoxNjAxMzk4MzI4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXg1NTQ0YWJmNGM3Y2JhMTcyMzY3MjA5NWJkNDdlMmFhOSJ9.ba3RFO2q_kVDgFTqrBdyCT-89PBvmTUx4WMRI5q7qCo&download=image.png "")

选择导入文件为`fakedata.zip`中的Material.xls，并选择格式为xls，点击提交，确认导入数据后实现数据全部导入。

![](https://tcs-ga.teambition.net/storage/111xa698e4b09ab9059b815e9811a007a76c?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzEyOCwiaWF0IjoxNjAxMzk4MzI4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhhNjk4ZTRiMDlhYjkwNTliODE1ZTk4MTFhMDA3YTc2YyJ9.uhmwm5IegAEEG5qbozy0oCo3YBbu0R317xrVpAPDvqQ&download=image.png "")

其余两表数据可以此方法导入。

## 接口数据测试

## 测试软件

后端端口测试可使用软件Pastman进行（下载地址[__https://www.postman.com/downloads/__](https://www.postman.com/downloads/)）。软件安装打开后有注册页面，无需注册，关掉即可使用。下面以获取材料主表中的DZ411为示例，展示接口测试方法。

## 接口测试

打开Postman，新建一个Request，随后起个名字，创建一个Collections，将Request添加其中。

![](https://tcs-ga.teambition.net/storage/111x292e44baee8a31037e07f7cdaee9c285?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzEyOCwiaWF0IjoxNjAxMzk4MzI4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgyOTJlNDRiYWVlOGEzMTAzN2UwN2Y3Y2RhZWU5YzI4NSJ9.lI5IPKHtw_ctLjXMdQs4YZdDlKZVnhizdJw8bF2zbaM&download=image.png "")

下图中，1可选择`~~**请求方法**~~`~~，2选择~~`~~**接口地址**~~`~~，3为配置~~请求内容

![](https://tcs-ga.teambition.net/storage/111x0a8c7fd25c0e96ae441806ff6626cf04?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzEyOCwiaWF0IjoxNjAxMzk4MzI4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgwYThjN2ZkMjVjMGU5NmFlNDQxODA2ZmY2NjI2Y2YwNCJ9._hujerCKiL9Tn99BKacnLM0ws_5SKDldBA7Z6VHVX_g&download=image.png "")

这里我们的目标是：**获取材料主表中的牌号为DZ411的材料的所有信息**，当前后端已经为该需求配置好了接口，`**接口地址**`为：http://127.0.0.1:8000/api/v1/measuringData/tableContents，这里可以分析一下这个接口地址的构成。首先http://127.0.0.1:8000/为后端服务器的ip和接口，而其余部分表示根据django的路由所指定的请求处理的地址。

/api/v1/measuringData/tableContents 这个`**接口地址**`可以**接收**一个**json文件**，并根据这个文件**返回**一个带有结果的**json文件**。一个json文件格式如下：

```json
{
"key1":"value1",
"key2":"value2",
...
}
```

里面个可以有若干个相对应的`**key值**`和`**value值**`。key值为每个`**接口地址**`固定的，而value值可以根据请求的不同而变化。对于 /api/v1/measuringData/tableContents 这个`**接口地址**`来说，它共接收两个`**key值**`，分别为 "brand_name” 和 "search_attribute"。 "brand_name” 对应着待搜索的材料牌号的名称，而 "search_attribute" 为想要搜索的表名。

**对表名的说明，各表命名请参考后端文件中的  apps/MeasuringData/models.py  文件，里面每个类的名字就是对应注释中表的名字，类里面每个变量的名字对应着返回json文件中的**`**key值**`**。**

当前，我们想搜DZ411的材料主表信息。让我们看一下models.py这个文件：

![](https://tcs-ga.teambition.net/storage/111x3913963ad4d0fa4697199819ef00db08?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzEyOCwiaWF0IjoxNjAxMzk4MzI4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgzOTEzOTYzYWQ0ZDBmYTQ2OTcxOTk4MTllZjAwZGIwOCJ9.XoFaFM_-uTbB3wjoZpqkBNPnPoumCeHbsKtsyll1GJk&download=image.png "")

可以看到，~~材料主表叫 Material，在查询机制中，需要将其~~~~**全小写**~~~~，故查询发送json文件应~~如下所示：

```json
{
    "brand_name":"DZ411",
    "search_attribute":"material"
}
```

我们将其写入postman，对该接口发起post请求，点击Send，可得：

![](https://tcs-ga.teambition.net/storage/111x53318c99429fe7d32b20498c8017ed7e?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzEyOCwiaWF0IjoxNjAxMzk4MzI4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXg1MzMxOGM5OTQyOWZlN2QzMmIyMDQ5OGM4MDE3ZWQ3ZSJ9.TPPyQszMHo_pP5wBw53xurxNlYUvN-0C_x1wBn76ejY&download=image.png "")

可以看到，通过在post请求的body中加入json，便可实现接口查找功能。