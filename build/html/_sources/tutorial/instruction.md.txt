# 文档维护说明

使用Sphinx + GitHub + ReadtheDocs 作为文档写作工具，用 Sphinx 生成文档，GitHub 托管文档，再导入到 ReadtheDocs。

## Sphinx

Sphinx 是一种文档工具，它可以令人轻松的撰写出清晰且优美的文档。

[Sphinx使用手册](https://zh-sphinx-doc.readthedocs.io/en/latest/contents.html)

首先安装sphinx及其依赖

```python
pip install sphinx sphinx-autobuild sphinx_rtd_theme recommonmark sphinx-markdown-tables
```

已经建立好了仓库用来托管文档：[ZRPlatform-docs](https://github.com/Artemisaturn/ZRPlatform-docs)，下拉项目到本地。

（使用sphinx创建工程非常简单，有兴趣可以自行尝试）

在根目录下编译文件（如果source有改动）：

```
make html   # 构建文档
```

用浏览器打开\build\html\index.html文件，可以预览效果

**支持rst和markdown编写**

在source下新增文档，要看index.rst文件是否包含该文档：

```rst
.. 在source目录下直接添加的文件，hello可为.rst/.md
.. toctree::
   :maxdepth: 2
   :caption: Contents
   
   hello

.. 在/source/tutorial下添加的文件，glob可将tutorial/下所有文件都包含进来
.. toctree::   
   :caption: Tutorial
   :glob:
   
   tutorial/*

.. 在/source/test下添加文件（另一种非全局方式）
.. toctree::   
   :caption: Test
   
   test/test1
```

[在线rst/md转换工具](http://pandoc.org/try/)，可以熟悉哪个用哪个

编辑完成后编译文件，push到GitHub上，GitHub提供的webhook服务会自动完成网站的部署。

[ReadtheDocs查阅](https://zrplatform-docs.readthedocs.io/zh_CN/latest/index.html)

## 在GitHub里集成ReadtheDocs服务

（仅记录，光使用的话看上面即可）

Readthedocs支持Markdown格式和sphinx格式的文档排版，是部署项目文档的绝佳平台。利用Github的托管服务，我们可以方便地将文档托管于Github，并利用Readthedocs查阅。

1. 在Read the Docs上面注册一个账号
2. 登陆后关联你的GitHub，点击 “Import”可以导入项目（注：仅可以导入public项目）
3. 给该文档项目填写一个名字，并添加你在GitHub上面的工程HTTPS链接, 选择仓库类型为Git
4. 其他项目根据自己的需要填写后点击 “Create”，创建完后会自动去激活Webhooks，不用再去GitHub设置
5. 一切搞定，从此只要你往这个仓库push代码，readthedoc上面的文档就会自动更新