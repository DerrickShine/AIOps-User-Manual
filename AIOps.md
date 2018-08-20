# AIOps User  Guide

### [基本操作](#quick-start)
### [用户手册](#user-manual)
1. [配置](#config)
2. [标注](#labelling)
3. [告警](#alerting)
4. [可视化](#visualization)

## Quick Start

### 将想要监测的曲线加入系统

> 进入配置页面
> 
> ![进入Setting页面](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/entering_setting.png)

> 输入可以拉取到曲线的`url`、`query-body`信息，测试，添加
> ![添加曲线](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/add_curve.png)

> **PS**：此系统的各个页面中，`曲线名`、`url`、`query-body`、`曲线id`等字符串信息左键单击即可复制

### 标注现有曲线历史上的异常点，供机器学习算法训练

> 找出并点选曲线
> ![搜索待标注曲线](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/search_curve_to_label.png)

> 左右移动时间窗口，在异常区域按住`Ctrl`左键拖放鼠标标记，按住`Shift`左键拖放鼠标取消区域标记
> ![标注](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/labelling.png)

> 无需手动保存更改

### 查看算法检测出的异常

> 查看实时异常告警
> 
> ![进入告警页面](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/entering_alert.png)

> 查看历史异常告警
> 
> ![进入告警标注页面](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/entering_label.png)

> 对于历史异常告警，根据图像判断是否判断正确，人为选择标记为正/负样本，系统会定时反馈给机器学习算法
> ![标注反馈](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/labelling_detected.png)

> 在配置页面中调整算法敏感度（对异常判定的敏感程度）
> ![调整算法敏感度](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/tune_sensitivity.png)

### 可视化已添加曲线

> 通过曲线的`id`、`name`、`source`等信息查询曲线，添加到页面中
> ![添加曲线](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/add_graph.png)

> 选择时间区间查看特定时间段内曲线
> ![选取时间](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/range_time.png)

> 添加的`Graph`可以左键拖动`zoom-in`自由选择时间区间；可以固定在页面中（刷新后保持）和删除
> ![观察图片](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/viewing_graph.png)

## User Manual

### - Config
![配置](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/configuration.png)

**1. 新增监控数据**
- 目前支持来自`Prometheus`和`Elasticsearch`的数据，其中Prom的数据后端会定时自动添加/删除，保留有数据的曲线；Elasticsearch的数据需手动添加，如下图，应先在
`http://kibana.pot.oa.com/app/kibana#/dev_tools/console?_g=()`
上将`url+query`调试通过，左方查询体能够成功查询到右方时序数据，再将`url`和`query`输入，Test，Add，即可添加。
![配置](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/kibana.png)

- 添加成功可在上方查到，也可点击`remove`删除
- 本系统页面中的`url`，`KID`，`name`等字符串均可通过左键点击复制到剪贴板，然后可粘贴到`Filter`查询框中进行查询

**2. 设置算法阈值**
- 机器学习算法预测出每个数据点的*异常程度*，为0.0~1.0间的浮点数，系统将某个阈值`Threshold = 1 - Sensitivity%`之上的点判定为异常，显示到告警页面中。
- 可以通过下方的`Algorithm Settings`自行调整`Sensitivity`，控制告警数量（`Sensitivity`越高，告警越多，反之亦然）

### - Curve

![标注](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/curve.png)

**标注异常**
- 使用输入框查询到特定曲线后，在下方标注异常点
- 通过下方`navigation bar`选取时间范围，也可左右移动时间窗口
- 画面上含一天前和一周前的图线情况供标注参考，某些与昨天/上周相似的趋势不应被认为是异常，而是周期性的变化；算法也会考虑这一特征
- 按住Ctrl拖动鼠标选取主图线时间区域将异常点标红，按住Shift拖动鼠标取消某段时间的标红，标红的区间内所有点都会记录为异常点，用作算法训练
- 由于异常点样本稀少，异常样本在训练中权重较高，应当尽量保证数据质量，故最好能做到不多标，例如出现尖峰情况，还没开始上升的时间点和下降后已平稳的时间点不应标红

![错误](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/wrong_label.png)![正确](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/correct_label.png)

### - Labelling

![标注页面](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/labelling_page.png)

**检查历史异常预测**
- 历史上算法预测出的异常会保存在此页面，可以定时查看算法的预测情况，并且将真实结果反馈给算法，不断提高算法性能
- 参考曲线最近的趋势和一天前一周前的趋势，判断是否为异常
- 若真的为异常情况，应`label as abnormal`；为正常情况，应`label as normal`；不确定是否为异常，或此样本不利于算法训练，应不标记
- `retrain`模型时，算法会使用所有的异常数据，抽样选取正常数据（会优先选取反馈的负样本）重新训练，故此环节是算法不断提高准确度，学会发现新形式的异常点的关键

### - Alerting

![告警页面](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/alert.png)

**查看告警**
- 此页面会显示出所有目前（1h内）有异常点的曲线，点击可查看曲线趋势状况
- 若觉得告警数量太多/太少，可以通过调低/调高配置页面中的`Sensitivity`来控制

### - Visualization

![可视化页面](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/visualization.png)

**1. 查找曲线**
- 在`filter`里输入关键词（如km）或曲线ID的一部分可快速查询到想要查询的曲线
- 勾选一幅或多幅后`Add Graph`（多幅时可以指定`Group Name`）添加到版面中
- 添加后可以通过graph中右上方的操作栏将此图固定（pin）（刷新页面后保持），取消固定（unpin），移除（remove）

**2. 查看曲线**

![操作栏](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/op_bar.png)
- 整个页面右上角的操作栏可以将页面中所有曲线`刷新`，`时间前/后移`，`时域缩/放`，`日历上自由选择时间区间`
- 每幅图中可通过在时间区间上左键拖动实现快捷`Zone In`，也可`Reset Zone`
- `x轴`下的图例可以点击使该条曲线`显示/隐藏`



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc0NDIxNzgyLDczMzMwOTI0LDc3ODg4Nj
M2MCwtMzUyMTc4NDg2LC01MzE4MTAwMTMsMTAwODk1MTU4NSwt
MTY4NjA3Mjk5NSwtNTM5MzI4MTgwLC0xMDIyMDM0NTcwLC0yMT
EzNjMwNTA5LDIwMTE5OTIxNTcsLTEyMDg2MDk2NSwxNTc0ODAx
MjQ2LDExMDkwNzM1MTQsLTY2MjU2MTM3MiwyNjEwODcwODcsLT
kwMzkyNTIyMiwtMTQ4OTc3NDMxLC0xMzczNTc5Mzk1LC0xNjMz
MzY1Njc3XX0=
-->