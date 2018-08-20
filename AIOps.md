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

> 左右移动时间窗口，在异常区域按住左键拖放鼠标标记，按住`Ctrl`左键拖放鼠标取消区域标记
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
**1. 新增监控数据**
> ![添加曲线](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/add_curve.png)

目前支持来自`Prometheus`和`Elasticsearch`的数据，其中Prom的数据后端会定时自动添加/删除，保留有数据的曲线；Elasticsearch的数据需手动添加，如下图，应先在
`http://kibana.pot.oa.com/app/kibana#/dev_tools/console?_g=()`
上将`url+query`调试通过，左方查询体能够成功查询到右方时序数据，再将`url`和`query`输入，Test，Add，即可添加。
添加成功可在上方查到，也可点击`remove`删除

**2. 设置算法阈值**
机器学习算法预测出每个数据点的*异常程度*，为0.0~1.0间的浮点数，系统将某个阈值`threshold`之上的点判定为异常，显示到告警页面中，

### - Labelling

### - Alerting

### - Visualization



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMDIyNjE5MTYsLTEwMjIwMzQ1NzAsLT
IxMTM2MzA1MDksMjAxMTk5MjE1NywtMTIwODYwOTY1LDE1NzQ4
MDEyNDYsMTEwOTA3MzUxNCwtNjYyNTYxMzcyLDI2MTA4NzA4Ny
wtOTAzOTI1MjIyLC0xNDg5Nzc0MzEsLTEzNzM1NzkzOTUsLTE2
MzMzNjU2NzcsOTQ1NDU4NzUyLC0xNzgwMjE2ODE0LDIwODQ4MT
g4OTcsLTE2MTUzODgwNTRdfQ==
-->