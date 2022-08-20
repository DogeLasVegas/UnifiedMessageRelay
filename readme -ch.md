# UnifiedMessageRelay: 群消息转发框架（支持QQ电报线冲突）


## UnifiedMessageRelay
UnifiedMessageRelay是一个框架，用于将来自不同聊天平台的消息汇集在一起。使用UnifiedMessageRelay，用户不再需要在不同的平台或不同的组中查看消息。UnifiedMessageRelay提供强大的消息转发功能和灵活的插件API来满足您的定制需求。同时提供了一个驱动程序API规范，可以编写自己的后端驱动程序，框架将自动加载和使用驱动程序。

## Demo
电报<->QQ：

Telegram

QQ

电报<->不和：

Discord

Telegram

所有四个平台：QQ、电报、线路和不和谐都可以相互直接转发。

## Supported platforms
基于coolqhttpapi的qqapi-aiocqhttp
基于Mamoe Technologies的多个回购的Mirai API
基于aigram的电报API
基于linebotx linebot的Line API
基于Discord.py的不一致API

## Update
ChangeLog.md

## Features
在所有支持的平台之间转发文本和图像
图像将自动转换为支持的格式
尽最大努力保留答复
Markdown格式为支持的平台保留
自定义触发器的命令API
消息钩子API可以满足更多的定制需求
对Coolq Air的支持有限。Coolq Pro提供图像发送功能。

## Installation
### Framework Setup
### 在主机操作系统上安装python依赖项
确保安装了python3.7+和`pip`。运行：

`pip3 install unified-message-relay`

### TLDR
要在一行中安装每个python模块：

`pip3 install -U umr_telegram_driver umr_line_driver umr_discord_driver umr_coolq_driver umr_mirai_driver umr_extensions_demo`

### 在主机操作系统上安装其他必需的软件包
`apt install libcairo2 ffmpeg libmagickwand-dev`

## Configurations
Create `~/.umr/`

`mkdir ~/.umr`
Copy config.yaml to `~/.umr`

为什么用yaml而不是json？

完整示例配置

上面的“QQ”、“Telegram”或“Line”都是自定义名称。真正的机器人驱动程序应该通过“驱动程序”列表进行配置。

### 遵循你的平台指南
[QQ](https://github.com/JQ-Networks/UnifiedMessageRelay/blob/master/Installation/QQ.md)

[Mirai](https://github.com/JQ-Networks/UnifiedMessageRelay/blob/master/Installation/Mirai.md)

[Telegram](https://github.com/JQ-Networks/UnifiedMessageRelay/blob/master/Installation/Telegram.md)

[Line](https://github.com/JQ-Networks/UnifiedMessageRelay/blob/master/Installation/Line.md)

[Discord](https://github.com/JQ-Networks/UnifiedMessageRelay/blob/master/Installation/Discord.md)

## 启动机器人
### Viewing CLI Help
`unified_message_relay -h`
### Background process
启动后台服务
`unified_message_relay start`

or

`unified-message-relay restart`
默认情况下，日志将存储在`/var/log/umr/bot.log`中，并在启动时清除缓存。

停止后台服务
`unified_message_relay stop`
### 目的（前台调试）
如果需要查看日志输出以进行调试，请先停止正在运行的守护程序。然后按照这个命令。

记住在配置中启用调试选项。

`unified_message_relay run`
按Ctrl+C停止。

## 扩展和命令
示例扩展和命令现在需要扩展名`umr-extensions-demo`：

`pip install umr-extensions-demo`
并将`- umr_extensions_demo`放在`config.yaml`的`Extensions`部分下。

### Available commands
#### Help
发送`!!help`以显示可用的命令。

此命令不需要额外的模块。

#### 聊天节目id
发送`!!id`到任何地方查看聊天id。

用`!!id`回复消息以显示源聊天id。

此命令要求`cmd_id.py`位于umr_extension_demo下。

#### Delete QQ Message
用`!!del`回复要删除的邮件

此命令要求`QQ_recall.py`位于umr_extension_demo下，并使用coolq驱动程序。目前不支持Mirai召回。

#### 添加电报阻止关键字
包含这些关键字的消息将不会转发到任何其他聊天室

发送`!!bk`和用空格分隔的关键字

这个命令需要`Telegram_watermeter.py`在umr_extension_demo下，并使用电报驱动程序。

#### 增加电报封锁通道
来自这些频道的消息不会被转发到任何其他聊天

用`!!bc`回复转发的频道消息

此命令需要`umr_extension_demo`下的`Telegram_watermeter.py`，并使用电报驱动程序。

要修改保存的关键字和频道，请编辑`config.yaml`中的`ExtensionConfig`部分。

### Available Extensions
#### Comment filter
在消息的开头添加`//`，以避免转发到任何其他聊天。

### Issue Format
## 打开问题前请检查这些
1.使用`unified-message-relay run`将日志打印到标准输出

2.检查您是否正在使用python3.7+

3.检查是否安装了二进制依赖项（在此页中搜索apt）

4.（如果使用Coolq）检查是否在Coolq中启用了cq-http-api

5.检查日志是否显示任何丢失的配置

6.检查您是否在Dev分支上，请切换回master（Dev可能不稳定）

## 问题必须提供
1.关于问题的描述

2.Pythondaemon.py运行记录（脱敏）

3.复制步骤
