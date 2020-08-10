---
title: feishu_micro_App
author: Kung (goukun07@gmail.com)
date: Apr 12, 2020
---

# feishu micro App

一份关于飞书小程序的笔记.

## Basic Concept

### 应用类型

企业自建应用
:   企业定制,供内部员工使用, 实现方式支持小程序,嵌入网页和机器人

商店应用
:   可在飞书应用商店发布的应用, 实现方式支持小程序和机器人

### 应用能力(小程序实现方式)

小程序
:   通过调用飞书 native 组建实现, 效果流畅, 优化性能好

网页
:   通过嵌入式网页形式 H5-JS-SDK 实现. 可能比较卡顿

消息机器人
:   通过飞书开放的 Restful API 实现程序化的消息发送. 通过 chat\_id
    等标识消息的发送和接收对象.

### [飞书开放平台开发文档]

主要分为四部分:

#### 快速入门

简要介绍整体开发流程

#### 客户端开发指南

详细介绍小程序的框架结构, 生命周期, 文件结构, 登陆过程, 客户端本地组件和 API 等
内容.
该部分是文档中最重要的部分.

#### 服务端API

介绍鉴权, 消息机器人, 用户群组, 应用管理等服务端接口.

#### 开放能力

飞书比较有特点的功能, 也是和微信小程序的主要区别在于提供 doc, sheet, 日程,
会议等文档的在线编辑接口.

虽然没有类似于微信云数据库的接口, 但是可以用 sheet 替代.

sheet 支持基于行和 range 的 CUDR 操作. 异步过程. 可以当简单的关系数据库使用.

### 接口调用

设计网络传输或读写数据的接口都采用一部方式, 建议 Promise 封装后使用

### 登陆过程

```
Promise.all([
    Promisefy(tt.login())(),
    Promisefy(getAppTokenApi)(app_id, app_secret)])
    .then((code, app_access_token) => {
        return Promisefy(code2sessionApi)(code, app_access_token)})
    .then((user_access_token) => {
        if (user_access_token)
            {"login success
            can use cloudApi with user_access_token"}
    })
```

![登陆流程时序图](https://sf1-ttcdn-tos.pstatp.com/obj/website-img/e4c72c3e1ce45facde26af0847540e75_Q5vBAYAj32.png "登陆时序图")

### 开发工具

开发工具 IDE 软件
:   目前只有 windows 和 Mac 版本, 功能比较全面, 支持模拟器, 调试器等

VScode feishu Extension
:   有登陆, 上传预览等管理功能. 不知什么原因,
    刚下载后尝试登陆一直没有反应,不会自动跳转浏览器.
    后来不知道什么原因突然就好了. 到现在还是不知道什么原因...

### PC 小程序中的模式

-   侧边栏（Sidebar）模式
-   应用中心（AppCenter）模式
-   窗口（Window）模式

### 两个主要对象

App(Object params)
:   代表当前小程序, 全局唯一, 只能在 app.js 中调用

Page(Object params)
:   代表一个页面, 在一个 page 子文件夹中唯一, 在 page.js 中调用.
    data 属性下的数据是第一次渲染页面的初始数据.
    `setData(Object data, Function callback)` 用于将数据从逻辑层发送到视图层
    （异步），同时改变对应的 this.data 的值（同步）

## Tips and tricks

### 图片标签问题

1.  img 标签不可用.
1.  image 标签头像尺寸, width: 72rpx; height: 72rpx;
1.  使用 setData 更新 image 标签 src 后不自动加载新的图片, 需要调用 onLoad
    方法重新加载页面才能显示新的图片.

### 小程序权限变更

在控制台页面申请权限变更后, 需要管理原审核发布后新权限才生效.

## Topic

Content.

## See also

[飞书开放平台开发文档]: https://open.feishu.cn/document/uQjL04CN/ucDOz4yN4MjL3gzM "飞书开放平台开发文档"
