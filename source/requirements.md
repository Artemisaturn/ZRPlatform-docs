# 待改进需求

## 进行中

### 前端用户注册机制改进 -> 王佳敏

取消身份证验证，改为工号、手机号等。集体**需沟通**。



### 去掉冗余数据库 -> 张田雨

1. 去掉性能数据管理的库

1. 去掉手册数据库

1. 将材料管理数据库（Material）名称变为手册数据库，并将其中的测试数据库删除

原则上保留用户管理数据库（前端和后端分别一个）、材料测试数据库、手册数据库，共4个库，之后预计添加2个数据库



### word文档导入与后端材料添加相统一



### 9.24目标进度

手册数据库完善，录入第三册数据

链接应用展示

注册登录模块展示

未来工作：标准数据库、材料供应商数据库



## 远中期计划

### 前端最终实现界面

参考（见附件[__ Haynes 230 Tech Data__](https://thoughts.teambition.com/workspaces/5f2f6c3a0c95000016c64ea2/files/5f604c7377f66f00012485b0) 及 [__航空材料数据管理应用平台__](https://thoughts.teambition.com/workspaces/5f2f6c3a0c95000016c64ea2/files/5f6053b377f66f0001254046)）：

[https://www.hightempmetals.com/techdata/hitempHaynes230data.php](https://www.hightempmetals.com/techdata/hitempHaynes230data.php)





### 测试用数据库后端增加搜索项

为后端增加处材料牌号外其他可搜索字段



### 后端测试数据导入

数据形式可只保留导入/导出为xls和xlsx，其余去除



### 后端测试数据上传数据更新机制改进 -> 董子瑞

调整admin_resourse.py内的import_id_fields字段，确定每条数据唯一性因素，避免该更新数据的地方变成__了添加数据__



### 按供应商管理需求及金相图片管理

每个材料可能有不同的供应商和生产时间，按供应商管理就是看某个供应商不同时间的材料，类似于这种。金相图片可以理解为材料的某个数据，是图片格式的，我们能存图片看图片就行。她也只是给我简单说了下，可以下周再和她详聊。



### 后端文件整合

文件地址：

[soursweat/ZRP-leisure](https://github.com/soursweat/ZRP-leisure/blob/master/Desktop.rar)

里面的views.py里有根据取值区间过滤数据的功能，可以迁移到当前工程中。







