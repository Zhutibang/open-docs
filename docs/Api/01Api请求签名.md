### Api请求签名

>zhlhuang 

#### 概述

用户在结果我们第三方平台的时候需要调用api接口，例如发送模板消息，获取二维码地址。这时候我们需要调用检查调用api接口的合法性。


#### 用法

```php
$sign=md5({appid}+{time}+{secret_key})
```

**其中，{appid}是open平台的appid；time是调用的时间戳；secret_key是open的私钥。**


#### 案例

```php

// 
$app_id = "wx61e8fa01dafe1d7a";
$secret_key = "XXXX";
$scene_id＝"1"; 

$url = "/api/qrcode_api/getQrcode.html?app_id={$app_id}&scene_id={$scene_id}"
$time = time(); //e.g: 1472887663

$sign = md5($app_id . $time . $secret_key); //wx61e8fa01dafe1d7a1472887663XXXX
// => 0e4ddb0b1a44272972c5d820eb77134f

$req_url = $url . "&time={$time}&sign={$sign}"
// => "/api/qrcode_api/getQrcode.html?app_id=wx61e8fa01dafe1d7a&scene_id=1&time=1472887663&sign=0e4ddb0b1a44272972c5d820eb77134f"
```

这样是一个完整的调用，如果平台向加强求情的安全性，可以对时间戳进行 限制。例子：先验证签名sign，然后根据timestamp来控制该签名的时效性，如约定超过10秒后的sign是无效的。


伪代码
```php
if( intval($_GET('time')) + 10 < time() ){
  //已过期
}
```
