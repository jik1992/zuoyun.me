title:  小程序 微信支付开发
date: 2018/08/17 01:51:04
categories:

- Third-party platform

tags:

-  WXApplet
-  pay

---

# 支付接口

# 关于微信支付商户

1. 不需要提供微信支付商户账号，只需要提供

   1. 商户号（账户中心->商户信息 当中查看）
   2. 密钥（这个密钥只有初次【API安全设置】的人知道，注意不要重置会影响生产业务）

2. 产品中心->API授权管理->新增授权申请单，提交小程序的APPID。(小程序必须保证账号主体和支付商户号账号主体一致) 申请绑定关系的时候注意小程序必须上线，而且有可以核实的业务

   ![20180817153449846527776.jpg](https://dn-zuoyun.qbox.me/20180817153449846527776.jpg)

![20180817153449824271289.png](https://dn-zuoyun.qbox.me/20180817153449824271289.png)

![20180817153449825024823.png](https://dn-zuoyun.qbox.me/20180817153449825024823.png)

# 微信支付核心流程

![20180817153449826219468.png](https://dn-zuoyun.qbox.me/20180817153449826219468.png)

<https://pay.weixin.qq.com/wiki/doc/api/wxa/wxa_api.php?chapter=7_4&index=3>

开源库

<https://github.com/egzosn/pay-java-parent>

主要方法

1. 用户登陆后前端获取基础用户信息，通过 openId 发起预支付订单

   ```
     @ApiOperation(value = "支付", tags = "场景一", hidden = true)
     @RequestMapping(value = "app", method = RequestMethod.GET)
     public Map<String, Object> app(
         @RequestParam String openid
     ) {
   
       BigDecimal price = null;
   
       Map<String, Object> data = new HashMap<>();
       data.put("code", 0);
       //App支付
       PayOrder
           order =
           new PayOrder("订单title", "摘要", null == price ? new BigDecimal(0.01) : price,
                        UUID.randomUUID().toString().replace("-", ""), WxTransactionType.JSAPI);
   
       order.setOpenid(openid);
       order.setTransactionType(WxTransactionType.JSAPI);
       data.put("orderInfo", service.orderInfo(order));
       return data;
     }
   
   ```

   

2. 发起预支付订单

3. ```
   创建预支付订单，这个方法包含生成统一支付订单，和再次签名返回
   WxPayService.orderInfo
       #支付统一下单
       WxPayService.unifiedOrder
       #返回 prepay_id以后再次签名
       WxPayService.createSign
   ```

   ![20180817153449850065970.jpg](https://dn-zuoyun.qbox.me/20180817153449850065970.jpg)

4. 前端拿到5参数+sign 正式调用支付 <https://developers.weixin.qq.com/miniprogram/dev/api/api-pay.html#wxrequestpaymentobject>

```
wx.requestPayment({
   'timeStamp': '',
   'nonceStr': '',
   'package': '',
   'signType': 'MD5',
   'paySign': '',
   'success':function(res){
   },
   'fail':function(res){
   }
})
```

1. 支付完成后，微信商户平台会回调用户 server对订单状态更新完毕

   ![20180817153449853786870.jpg](https://dn-zuoyun.qbox.me/20180817153449853786870.jpg)

2. 前端支付成功跳转分享页

 