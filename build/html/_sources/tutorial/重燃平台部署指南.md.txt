# 重燃平台部署指南

## 平台结构介绍

- 该网站平台需在__Windows系统__上部署，分为__前端__和__后端__。

- __后端__为基于Django搭建的数据管理平台，用于处理前端数据请求，并对数据进行增删改查操作。

- __前端__为基于VUE搭建的系统平台，用于用户对于材料信息的检索、比对，表格规范化展示数据，后期将和Ansys等仿真软件进行结合，通过平台材料数据直接进行仿真运行操作。

## 平台部署

平台部署依赖__Windows环境__，建议使用Windows10搭建。

### 后端相关环境软件安装

1. 安装Python

本平台使用Python3.6.8进行部署

1. 安装mysql

1. 安装mongodb

安装过程建议一路next，否则容易卡bug。

另mongodb安装时，最后可能会卡很长时间，如发生卡死现象，可在安装过程中选择__不安装__mongodb compass，如下图所示。该程序为mongodb可视化界面，如不安装不会影响平台部署。

![](https://tcs-ga.teambition.net/storage/111x20c9c799966c6b1a4e303893e21a6d72?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgyMGM5Yzc5OTk2NmM2YjFhNGUzMDM4OTNlMjFhNmQ3MiJ9.-scvgdsPFKsSPKkvOWzgX-XEHJ8hfYfoUdAPDmyTzwQ&download=image.png "")

1. 安装Redis

1. 安装Python依赖包

请使用命令`pip install –r requirements.txt`用需求文件进行安装，安装过程可能会报mod_wsgi相关错误，是因为没有安装Apache，可从requirements.txt中**删除最后一行mod_wsgi的配置**，保存后再次运行命令。

**另请将txt文件中**`**simpleui==4.0.3**`**改为**`**django-simpleui==4.0.3**`

若安装过程缓慢，可使用命令：

`pip install -i http://mirrors.aliyun.com/pypi/simple--trusted-host mirrors.aliyun.com -r requirements.txt `

来使用阿里的镜像。

### 后端工程与数据库对接

后端工程文件结构如下图所示：

![](https://tcs-ga.teambition.net/storage/111xb85ca76aa6bf5da1977972d5fc149eee?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhiODVjYTc2YWE2YmY1ZGExOTc3OTcyZDVmYzE0OWVlZSJ9.PWC6fPAkKEBm4Q6IEv_b_87r8lqL5pym69wqY6EH9Jk&download=image.png "")

**该对接过程讲解以此目录为根目录，进行文件说明。**

1. 配置数据库对接

`在\ZRPlatform 下，打开settings.py文件，进行数据库数据配置`。

![](https://tcs-ga.teambition.net/storage/111xb0a6469e5d7fa52c83d580c7f4ffa9f3?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhiMGE2NDY5ZTVkN2ZhNTJjODNkNTgwYzdmNGZmYTlmMyJ9.qZRlCjihngH-HZnN_bUlA27eBk2a1xcizf2TAp3PPME&download=image.png "")

从上图可以看到，本平台使用了1个mongodb库（'ENGINE': 'djongo'）和两个Mysql库（'ENGINE': 'django.db.backends.mysql'）。数据库对接需要对Mysql数据库的用户密码进行修改（’PASSWORD’，上图中共有两处），以匹配安装Mysql数据库时的设定密码。

1. Mysql数据库构建

Django使用ORM架构进行数据库操作管理，无法直接建立数据库，所以需要将图中的两个Mysql库进行手动建立。（图中的两个数据名字分别是'NAME': 'zrplatform'以及'NAME': 'zrp_experiment_data'）。

因为之前安装Mysql的时候同时安装了mysql workbench，这里展示如何用workbench进行配置。程序在系统任务栏可以看到：

![](https://tcs-ga.teambition.net/storage/111xa7f2adcc9f73a91b1553999e9badaa2a?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhhN2YyYWRjYzlmNzNhOTFiMTU1Mzk5OWU5YmFkYWEyYSJ9.2j9aoOTgUse_ZUfzTd17F39IMLFStS6Ho7xk7y8CDik&download=image.png "")

双击打后，输入之前设置的密码，选择schemas栏，便可看到当前默认的数据库：

![](https://tcs-ga.teambition.net/storage/111x985e0f51b5f4dbd0a5b7aeb799ca4d20?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXg5ODVlMGY1MWI1ZjRkYmQwYTViN2FlYjc5OWNhNGQyMCJ9.SFnxNpkEOCtNvHu_Stjk4paXqRI1f0w4GKqOLgl-dek&download=image.png "")

这里选择添加数据库，根据后端要求，建立名称为'zrplatform'以及'zrp_experiment_data'的两个数据库：

![](https://tcs-ga.teambition.net/storage/111x3411b990f7970092239f278117182fc3?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgzNDExYjk5MGY3OTcwMDkyMjM5ZjI3ODExNzE4MmZjMyJ9.3WnxcrICSOmYXayT7STEFT9t0CTtGatSDZ1PV-cb2U0&download=image.png "")

![](https://tcs-ga.teambition.net/storage/111xf6d85c563f3c15f55bba43001ef78cbc?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhmNmQ4NWM1NjNmM2MxNWY1NWJiYTQzMDAxZWY3OGNiYyJ9.dmb8JrbREqmOQjknxZsSKr5Gd0llyibe3HZMsBLwOOk&download=image.png "")

建立好后便有了两个空数据库

![](https://tcs-ga.teambition.net/storage/111x4d3e2915f83350c2ef6678c9176fcdde?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXg0ZDNlMjkxNWY4MzM1MGMyZWY2Njc4YzkxNzZmY2RkZSJ9.e_Qcb7P0_U9c8YoTlN94MydQVdtcJT3lo8w3V1SabrU&download=image.png "")

1. 数据库迁移

我们共有3个数据库准备迁移，分别是默认数据库，以及’searchdb’和’experimentdb’如下图所示。

![](https://tcs-ga.teambition.net/storage/111x2996c975f158f01640bb0aaca9d8ceb6?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgyOTk2Yzk3NWYxNThmMDE2NDBiYjBhYWNhOWQ4Y2ViNiJ9.7_afDItwltmKvDV_y1f2uAk5eEEpGzpg0qBdAj6keNE&download=image.png "")

这里先简要介绍一下’searchdb’、’experimentdb’与'zrplatform'、'zrp_experiment_data'之间的关系。’searchdb’、’experimentdb’是django端对数据库的命名，而'zrplatform'、'zrp_experiment_data'是Mysql对数据库的明明，两者对接依靠settings.py里对数据库的配置进行。

对于django来讲，数据库需要和django里的apps们进行绑定，该过程同样在settings.py内进行：

![](https://tcs-ga.teambition.net/storage/111x0ae548c2d338c2574fc716e734dbb7d6?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgwYWU1NDhjMmQzMzhjMjU3NGZjNzE2ZTczNGRiYjdkNiJ9.Acgow5TeFZnJ5R9cyY_TtJ4XPZEGm60A34iiFnY1Qas&download=image.png "")

可以看到，名为Data的app其数据库被绑定在了searchdb中，而app ’MeasuringData’使用了数据库’experimentdb’，本平台不只有这两个app，其他的apps使用额数据库是’default’，即mongodb中。

为分别进行三个数据库的迁移，需在__根目录__下运用命令行分别运行以下命令：

`python manage.py makemigrations`

`python manage.py migrate`

`python manage.py makemigrations Data`

`python manage.py migrate --database=searchdb`

`python manage.py makemigrations MeasuringData`

`python manage.py migrate --database=experimentdb`

不难看出以上命令两个为一组，分别对default和两个自定义数据库进行迁移。关于manage.py、makemigrations和migrate的意义，欢迎百度一下看看。这里可以简单理解为，先从平台所带有的数据库模型代码make出可用于对数据库执行的程序，然后用这些程序migrate表到数据库中，实现两边的同步。

完成数据库迁移后，mysql结构如图所示：

![](https://tcs-ga.teambition.net/storage/111x68f570c15d519a2c60571e9e59a0d66a?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXg2OGY1NzBjMTVkNTE5YTJjNjA1NzFlOWU1OWEwZDY2YSJ9.uQ7laxn_o4RFphiYl1J2TGJ7kpGNrGbbXRZILb3Uk6s&download=image.png "")

### 后端系统启动

1. 创建超级用户

为进行后端平台访问，需先创建一超级用户。使用以下命令创建：

`python manage.py createsuperuser`

设置用户名和密码，无需给出邮箱，如图所示：

![](https://tcs-ga.teambition.net/storage/111x22173930c2697c0edbf0bf57ea436258?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgyMjE3MzkzMGMyNjk3YzBlZGJmMGJmNTdlYTQzNjI1OCJ9.I7a90KAkUIuPcYN1PDZBtXE9YbC2BD2lorbXPF3bJ_0&download=image.png "")

1.  启动系统

使用命令

`python manage.py runserver`

启动系统：

![](https://tcs-ga.teambition.net/storage/111x934eff203632e3f62da92f7f7b585b57?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXg5MzRlZmYyMDM2MzJlM2Y2MmRhOTJmN2Y3YjU4NWI1NyJ9.nH-N8Gkg7VB9pkTqeyrWfqYDQ2BfniWD7ACeUWAzZQA&download=image.png "")

1. 访问后端

推荐使用chrome或firefox浏览器对后端进行访问，网址为：

[http://127.0.0.1:8000/admin](http://127.0.0.1:8000/admin)

![](https://tcs-ga.teambition.net/storage/111xf6cfb421c14644a1fadf55fc15597877?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhmNmNmYjQyMWMxNDY0NGExZmFkZjU1ZmMxNTU5Nzg3NyJ9.zyS4QbMSC8yYwdUiFiYUIcejbCioDp1DYXX0iDYVnBA&download=image.png "")

输入超级用户的用户名和密码便可进入，至此后端配置成功。

### 前端相关环境软件安装配置

请从[https://nodejs.org/](https://nodejs.org/)下载nodejs安装（本教程中为12.18版本），并安装

前端根目录如图所示，**前端介绍时以此目录为根目录**：

![](file:///C:/Users/john/AppData/Local/Temp/msohtmlclip1/01/clip_image002.jpg "")

在此目录下打开命令行，输入

npm run dev

即可运行前端程序（[http://127.0.0.1:8080](http://127.0.0.1:8080)）

### 前后端对接

前端会向后端发送数据请求，故需配置发送地址。

1. 在/src/components/global.vue中，将服务器地址改为后端地址：

![](https://tcs-ga.teambition.net/storage/111x573f929a2fb5e8d90badbfa1db99ebdf?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXg1NzNmOTI5YTJmYjVlOGQ5MGJhZGJmYTFkYjk5ZWJkZiJ9.Mga1lWmtLbprbYAF3wHzDxjUqAfuBQ0zsTFqtrt0HKA&download=image.png "")

1. 将/src/resfulapi/api.js中的数据请求地址改为相应路由地址

![](https://tcs-ga.teambition.net/storage/111xdc56e30c3758a020ffc2ef07aa8f09ef?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzExNywiaWF0IjoxNjAxMzk4MzE3LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhkYzU2ZTMwYzM3NThhMDIwZmZjMmVmMDdhYThmMDllZiJ9.y9a-7kOGIeRxM3npFzplYPazbF4mPFymyv7kOl3gjHM&download=image.png "")



***修正***：

至此前后端连接完成，整体平台环境搭建完成。













