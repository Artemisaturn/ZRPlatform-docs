# 材料数据库接口调研
## 现有接口
除上传下载、模板生成等接口外，每个model都有相应的接口：
- CategoryView
返回所有的材料种类
- SourceView
返回所有的数据来源
- MaterialView
返回根据材料种类、数据来源、查询条件筛选的材料
- MaterialDetailView
返回根据材料id的材料详情
- MaterialPhyAndCheView
返回根据材料id的物理化学性能
- MaterialMechanicsView
返回根据材料id的力学性能
- MaterialStruAndPerfView
返回根据材料id的组织结构和工艺性能
## 待开发接口

### 细化粒度

- 实现同时浏览不同性能部分的功能

  跨表

### 结构调整

- 后续会把结构组织和工艺性能分表，需要单独编写这两部分的接口：
  1. MaterialStructureView
  2. MaterialPerformanceView