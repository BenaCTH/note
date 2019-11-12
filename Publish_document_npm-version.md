# npm 版本控制（Base）

## 版本发布
* 在Git的Web manage界面，创建tag，tagName格式：v + 版本号，如v1.2.3。
* 创建时填写release notes，git会自动创建Pipeline，success时会根据版本号进行release。
* release notes格式如下：
  * ##版本号(日期)，如：0.5.2(2019/10/30)
  * ###修改的分类：Breaking Changes，Features，Bug Fix，Others。
  * *每个分类下的内容。

## 版本号策略
采用x.y.z为基本版本策略，如：1.3.6。
* z：在进行bug修复发布时，z加一。
* y：有新功能添加/旧功能标记为不推荐使用时（必须兼容之前的版本，0.y.z版本暂可不兼容），y加一。
* x：当进行较大改动，引起UI或交互严重变化/有不兼容的内容(API)更新时，x加一。

## 特殊版本策略
在特殊情况下，遵循特殊版本策略，特殊版本均为从branch上建立，语法：x.y.z+proj.patch(yyzz)，如：1.3.6+rpsa.5
* x/y/z部分遵循上面的版本策略。
* proj：指代具体的项目/产品名称(简称)。
* patch：具体的patch版本，yy和zz取值范围00~99，zz指代bug修复版本，yy指代功能改动，以1.2.3+rpsa.15版本为例：
  * 修改功能后为1.2.3+rpsa.0115
  * 再修改功能为1.2.3+rpsa.0215
  * 再修改bug为1.2.3+rpsa.0216
* 特殊版本需要在适当时机merge回master，经审核，指定y和z的累加数。