---
date: 2017-08-07 23:04:08
layout: post
title: 封装网络请求
subtitle: 封装网络请求的七步曲
description: 将一个基于回调的异步网络请求，封转成基于 Promise 的网络请求。我们期望的使用支持 Promise 的第三发请求语法
image: https://res.cloudinary.com/dm7h7e8xj/image/upload/v1559822138/theme10_xenudc.jpg
optimized_image: https://res.cloudinary.com/dm7h7e8xj/image/upload/c_scale,w_380/v1559822138/theme10_xenudc.jpg
category: 封装网络请求
tags:
  - promis
  - story
author: mranderson
---

将一个基于回调的异步网络请求，封转成基于 Promise 的网络请求。

<a name="SClBf"></a>

# 需求分析

我们期望的使用支持 Promise 的第三发请求语法

```javascript
import { http } from 'npm第三方包或者自己封转'

// 发起请求
async getData(){
  const res = await http.get('url地址', {请求参数1: '值1', 请求参数2: '值2'})
  console.log('使用封转Promise获取到的返回数据：', res)
}
```


<a name="jH8nz"></a>

# 封装过程

:::danger
我们通过函数的使用方式来倒退函数的封装
:::

<a name="FcSD7"></a>

## 第一步

既然使用时导入的是一个对象，所以我们导出一个对象。这个对象可以调用 `get(url, query)` 方法，所以我们封装对应的方法。

```javascript
// 具名导出一个 http 对象
export const http = {
  // get 是一个函数
  get(url, query) {
  	// 将来这里发起请求
  },
}
```


<a name="C1j58"></a>

## 第二步

我们使用 `const res = await get(url, query)` 接收数据，那么 `get(url, query)` 方法一定返回一个 Promise 对象。

```javascript
// 具名导出一个 http 对象
export const http = {
  // get 是一个函数
  get(url, query) {
    // 将来这里发起请求
    const promise = new Promise((resolve, reject) => {})
    return promise
  },
}
```


<a name="KR1FE"></a>

## 第三步

在 Promise 的构造函数中发起网络请求。

```javascript
// 具名导出一个 http 对象
export const http = {
  // get 是一个函数
  get(url, query) {
    // 将来这里发起请求
    const promise = new Promise((resolve, reject) => {
      wx.request({
        url: url,
        method: 'GET',
        data: query,
        // 网络请求成功的统一处理
        success: (res) => {
          console.log('http请求到的的res', res)
          // 将请求到的数据传递给 Promise 对象
          resolve(res)
        },
      })
    })
    return promise
  },
}
```

页面中使用

```javascript
  async getNotifyList() {
    const res = await http.get('https://live-api.itheima.net/announcement')
    console.log('首页获取公告列表res：', res)
    // 设置页面数据
    this.setData({
      notifyList: res.data.data,
    });
  },
```


<a name="Fs0Ge"></a>

## 第四步

封装基地址（baseURL）、数据的格式的简单处理。

```javascript
const baseURL = 'https://live-api.itheima.net'

// 具名导出一个 http 对象
export const http = {
  // get 是一个函数
  get(url, query) {
    // 将来这里发起请求
    const promise = new Promise((resolve, reject) => {
      wx.request({
        url: baseURL + url,
        method: 'GET',
        data: query,
        // 网络请求成功的统一处理
        success: (res) => {
          console.log('http请求到的的res', res)
          // 剥离数据，直接传递业务数据到页面
          resolve(res.data.data)
        },
      })
    })
    return promise
  },
}
```

```javascript
  async getNotifyList() {
    const res = await http.get('/announcement')
    console.log('首页获取公告列表res：', res)
    // 设置页面数据
    this.setData({
      notifyList: res,
    });
  },
```


<a name="JNb7g"></a>

## 第五步

网络请求数据状态统一判断

```javascript
const baseURL = 'https://live-api.itheima.net'

// 具名导出一个 http 对象
export const http = {
  // get 是一个函数
  get(url, query) {
    // 将来这里发起请求
    const promise = new Promise((resolve, reject) => {
      wx.request({
        url: baseURL + url,
        method: 'GET',
        data: query,
        // 网络请求成功的统一处理
        success: (res) => {
          console.log('http请求到的的res', res)
          // 网络请求状态统一处理
          if (res.data.code !== 10000) {
            // 业务请求失败统一处理
            return wx.showToast({
              title: res.data.message,
              icon: 'none'
            })
          }
          // 将请求到的数据传递给 Promise 对象
          resolve(res.data.data)
        },
      })
    })
    return promise
  },
}
```

```javascript
  async getNotifyList() {
    // 传递一个错误地址进行测试
    const res = await http.get('/announcementx')
    console.log('首页获取公告列表res：', res)
    // 设置页面数据
    this.setData({
      notifyList: res,
    });
  },
```


<a name="tJfJo"></a>

## 第六步

token 失效统一处理

```javascript
const baseURL = 'https://live-api.itheima.net'

// 具名导出一个 http 对象
export const http = {
  // get 是一个函数
  get(url, query) {
    // 将来这里发起请求
    const promise = new Promise((resolve, reject) => {
      wx.request({
        url: baseURL + url,
        method: 'GET',
        data: query,
        // 网络请求成功的统一处理
        success: (res) => {
          console.log('http请求到的的res', res)
          // token 失效统一处理
          if (res.data.code === 401) {
            return wx.showToast({
              title: res.data.message,
              icon: 'none'
            })
          }
          // 网络请求状态统一处理
          if (res.data.code !== 10000) {
            // 业务请求失败统一处理
            return wx.showToast({
              title: res.data.message,
              icon: 'none'
            })
          }
          // 将请求到的数据传递给 Promise 对象
          resolve(res.data.data)
        },
      })
    })
    return promise
  },
}
```

```javascript
  async getNotifyList() {
    // const res = await http.get('/announcement')
    const res = await http.get('/room')
    console.log('首页获取公告列表res：', res)
    // 设置页面数据
    this.setData({
      notifyList: res,
    });
  },
```


<a name="pbDT3"></a>

## 第七步

token 失效重定向到登录页面

```javascript
import { getToken } from './getToken'

const baseURL = 'https://live-api.itheima.net'
// 具名导出一个 http 对象
export const http = {
  // get 是一个函数
  get(url, query) {
    // 将来这里发起请求
    const promise = new Promise((resolve, reject) => {
      wx.request({
        url: baseURL + url,
        method: 'GET',
        // 添加请求头
        header: {
          Authorization: 'Bearer ' + getToken()
        },
        data: query,
        // 网络请求成功的统一处理
        success: (res) => {
          console.log('http请求到的的res', res)
          // token 失效统一处理
          if (res.data.code === 401) {
            // token 失效充重定向到登录页面
            wx.navigateTo({
              url: '/pages/login/index',
            })
            return wx.showToast({
              title: res.data.message,
              icon: 'none'
            })
          }
          // 网络请求状态统一处理
          if (res.data.code !== 10000) {
            // 业务请求失败统一处理
            return wx.showToast({
              title: res.data.message,
              icon: 'none'
            })
          }
          // 将请求到的数据传递给 Promise 对象
          resolve(res.data.data)
        },
      })
    })
    return promise
  },
}
```






















