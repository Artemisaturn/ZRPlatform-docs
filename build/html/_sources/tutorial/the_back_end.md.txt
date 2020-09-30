# 后端word手册数据导入及前端用户登录

## 后端导入word文档

当前平台后端支持将word文档导入系统，并存入数据库，已实现该功能，需在部署了后端平台的电脑上**同时安装有word**。当前提供[__测试用word文档__](https://thoughts.teambition.com/workspaces/5f2f6c3a0c95000016c64ea2/files/5f606813e6eed50001f62be2)供大家尝试。

注：一定要事先按照[__平台部署指南__](https://thoughts.teambition.com/workspaces/5f2f6c3a0c95000016c64ea2/docs/5f5216c1e6eed50001b9f26e)，做好前后端接口（共两处），且在ip地址前加上**http://  **(例如 http://127.0.0.1:8000)，否则会出现图片无法识别的情况。

- 进入材料管理界面，可看到有word导入按钮，选择[__测试用word文档__](https://thoughts.teambition.com/workspaces/5f2f6c3a0c95000016c64ea2/files/5f606813e6eed50001f62be2)，进行导入。**导入过程较为缓慢，请耐心等待。**

![](https://tcs-ga.teambition.net/storage/111x9e3e57c2b04d6b2f0bd485aabc89383d?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzA5OCwiaWF0IjoxNjAxMzk4Mjk4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXg5ZTNlNTdjMmIwNGQ2YjJmMGJkNDg1YWFiYzg5MzgzZCJ9.lLLkdHUPTcmsJXYHqltu_bRM5q27-T8SPf226lz15dw&download=%E6%88%AA%E5%B1%8F2020-09-15%20%E4%B8%8B%E5%8D%883.13.37.png "")

导入后有如下所示效果：

![](https://tcs-ga.teambition.net/storage/111x65de9690561fa8044fce7ca681fb94d4?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzA5OCwiaWF0IjoxNjAxMzk4Mjk4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXg2NWRlOTY5MDU2MWZhODA0NGZjZTdjYTY4MWZiOTRkNCJ9.SXquatoP3cyTVPUu2H8GMMk6vx_htF_z7NUooiqzlBs&download=%E6%88%AA%E5%B1%8F2020-09-15%20%E4%B8%8B%E5%8D%883.19.37.png "")

刷新页面，可看到导入数据：

![](https://tcs-ga.teambition.net/storage/111xcd69797cd750d9237eff2fea9a1934c9?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzA5OCwiaWF0IjoxNjAxMzk4Mjk4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhjZDY5Nzk3Y2Q3NTBkOTIzN2VmZjJmZWE5YTE5MzRjOSJ9.rhdX838yyI8PFYTE8K7JTsOICBoYcB0tRJ3XQSafSJQ&download=%E6%88%AA%E5%B1%8F2020-09-15%20%E4%B8%8B%E5%8D%883.20.56.png "")

- 搜索材料牌号为“20”的材料，单击进入

![](https://tcs-ga.teambition.net/storage/111xd9929ac7bb590b398957f37c783aa331?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzA5OCwiaWF0IjoxNjAxMzk4Mjk4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhkOTkyOWFjN2JiNTkwYjM5ODk1N2YzN2M3ODNhYTMzMSJ9.GN7HzUlyqVqOTFJn9anWT2Ee9g75RFQ5v82lcBfzibs&download=%E6%88%AA%E5%B1%8F2020-09-15%20%E4%B8%8B%E5%8D%883.22.41.png "")

可以看到内部word文档里的对应条目在导入后的情况：

![](https://tcs-ga.teambition.net/storage/111xc5eda1a1dc77e291450f18d6f85d35cc?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzA5OCwiaWF0IjoxNjAxMzk4Mjk4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhjNWVkYTFhMWRjNzdlMjkxNDUwZjE4ZDZmODVkMzVjYyJ9.x-detRIPL7BPE8aaSsrNQJl_zMNTQoVkq1o8mUEmb2o&download=%E6%88%AA%E5%B1%8F2020-09-15%20%E4%B8%8B%E5%8D%883.23.41.png "")

## 后端为前端创建账户

![](https://tcs-ga.teambition.net/storage/111xc8a935216ad77d6d35af0bf3e2306cc3?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzA5OCwiaWF0IjoxNjAxMzk4Mjk4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhjOGE5MzUyMTZhZDc3ZDZkMzVhZjBiZjNlMjMwNmNjMyJ9.GgHyktA_WYOprySmiD2cBWe9u3MghV7bJ0E21ayEU1o&download=%E6%88%AA%E5%B1%8F2020-09-15%20%E4%B8%8B%E5%8D%883.24.38.png "")

## 前端登陆系统

![](https://tcs-ga.teambition.net/storage/111xd63cb5373a1975a726cb7caea935f17a?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzA5OCwiaWF0IjoxNjAxMzk4Mjk4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXhkNjNjYjUzNzNhMTk3NWE3MjZjYjdjYWVhOTM1ZjE3YSJ9.ak33EQgsiN5PFxZXq610L1GhCKSimN-qBxTAxQTDH7E&download=%E6%88%AA%E5%B1%8F2020-09-15%20%E4%B8%8B%E5%8D%883.25.41.png "")

登陆后才可查看相关手册数据

## 查看导入的数据

可通过顶栏“材料数据库”或者主页的“燃机专用材料数据库”进入手册数据浏览界面：

![](https://tcs-ga.teambition.net/storage/111x2b83a66515f421d6d6ec36a79b05cee5?Signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJBcHBJRCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9hcHBJZCI6IjU5Mzc3MGZmODM5NjMyMDAyZTAzNThmMSIsIl9vcmdhbml6YXRpb25JZCI6IiIsImV4cCI6MTYwMjAwMzA5OCwiaWF0IjoxNjAxMzk4Mjk4LCJyZXNvdXJjZSI6Ii9zdG9yYWdlLzExMXgyYjgzYTY2NTE1ZjQyMWQ2ZDZlYzM2YTc5YjA1Y2VlNSJ9.vNm9RN5qx9qIz7Wlhd8ktx4O1XcP1N1uDm-LMS_hC7o&download=%E6%88%AA%E5%B1%8F2020-09-15%20%E4%B8%8B%E5%8D%883.28.00.png "")

## bug及解决方案

在后端导入数据时，可能会发生报错问题，可以尝试以下操作：

1.将当前所有word关闭

2.在任务管理器中结束word相关进程

3.

Step1: 运行dcomcnfg.exe 找到组件服务 DCOM配置 Microsoft Word 97-2003文档 右键选择属性 选择 “标识”，改为交互式用户

Step2: 修改下apps Material views.py的1122行为app=win32com.client.DispatchEx ("Word.Application")

4.

新建2文件夹并修改权限

C:\Windows\SysWOW64\config\systemprofile\Desktop

C:\Windows\System32\config\systemprofile\Desktop



- 出现bug的极有可能和word版本有关，目前已知2016和Office365不会报错，2013可能会报错



