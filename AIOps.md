# AIOps User  Guide

### [QuickStart](#quick-start)

### [UserManual](#user-manual)
1. 配置
2. 标注
3. 告警
4. 可视化

## Quick Start

### 将想要监测的曲线加入系统
![进入Setting页面](https://github.com/DerrickShine/AIOps-User-Manual/blob/master/pic/entering_setting.png)
> 输入可以拉取到曲线的`url`、`query-body`信息，测试，添加
> 添加成功后的曲线可以在页面上方查询、删除
> **PS**：此系统的各个页面中，`曲线名`、`url`、`query-body`、`曲线id`等字符串信息左键单击即可复制

### 标注现有曲线历史上的异常点，供机器学习算法训练
> 找出并点选曲线
> 左右移动时间窗口，在异常区域按住左键拖放鼠标标记，按住`Ctrl`左键拖放鼠标取消区域标记
> 无需手动保存更改

### 查看算法检测出的异常
> 查看实时异常告警
> 查看历史异常告警
> 对于历史异常告警，根据图像判断是否判断正确，人为选择标记为正/负样本，系统会定时反馈给机器学习算法

### 可视化已添加曲线
> 通过曲线的`id`、`name`、`source`等信息查询曲线，添加到页面中
> 选择时间区间查看特定时间段内曲线
> 添加的`Graph`可以固定z

## User Manual

<!--stackedit_data:
eyJoaXN0b3J5IjpbOTU1MDE4NDc4LC0xNDg5Nzc0MzEsLTEzNz
M1NzkzOTUsLTE2MzMzNjU2NzcsOTQ1NDU4NzUyLC0xNzgwMjE2
ODE0LDIwODQ4MTg4OTcsLTE2MTUzODgwNTRdfQ==
-->