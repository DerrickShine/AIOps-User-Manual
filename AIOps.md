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
> PS**在此系统中，`曲线名`、`url`、`query-body`、`曲线id`等字符串信息可以通过

### 标注现有曲线历史上的异常点，供机器学习算法训练
> 找出并点选曲线
> 左右移动时间窗口，在异常区域按住左键拖放鼠标标记，按住`Ctrl`左键拖放鼠标取消区域标记
> 无需手动保存更改

### 查看算法检测出的异常
> 查看实时异常告警
> 查看历史异常告警
> 对于历史异常告警，根据图像判断是否判断正确，人为选择标记为正/负样本，系统会定时反馈给机器学习算法

### 查看已添加曲线
> 

## User Manual

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUxNjc5MjM5OCwtMTM3MzU3OTM5NSwtMT
YzMzM2NTY3Nyw5NDU0NTg3NTIsLTE3ODAyMTY4MTQsMjA4NDgx
ODg5NywtMTYxNTM4ODA1NF19
-->