# 待改进需求

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







