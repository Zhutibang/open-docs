### 发送模板消息api
>zhlhuang

#### request

ps：

1.调用该接口的时候需要在open平台设置 secret

2.微信后台设计js调用的域名

 **method** ：post
 
 **URL**： `api/Jssdk_api/index/app_id/{appid}.html?time={time}&sign={sign}`
 
ps： {appid} 是授权公众号的appid
 

字段 | 类型|是否必须|描述
---|---|---|---|
url | string|是|调用jssdk的网页地址，location.href 获取|


### response

```
{
  "debug": false,
  "beta": false,
  "appId": "wx783f316670f7c86d",
  "nonceStr": "1TkLX11EZI",
  "timestamp": 1489918219,
  "url": "http://ward.sz.ztbweb.cn/index.php?a=test",
  "signature": "cf752931637345520e5e826516916b0f28ba64ee",
  "jsApiList": []
}
```

字段 | 类型|描述
---|---|---
jsApiList | array|根据自身所需的业务逻辑添加

* [错误格式](/Api/01Api错误返回.html)


