# 请求结构



## 1. 服务地址

> API支持就近地域接入，根据调用接口时客户端所在的位置，会自动解析到最近的某个地域的服务器



ISMS 智能短信使用如下域名作为服务地址接入：

| 接入地域     | 域名          | 备注 |
| ------------ | ------------- | ---- |
| 就近地域接入 | api.ucloud.cn |      |



## 2. 通信协议

UCloud云计算产品的所有API都支持通过 HTTP/HTTPS进行通信，为了更好的确保通信的高安全性，推荐您使用HTTPS协议。



## 3. 请求方法

支持的HTTP/HTTPS GET



## 4. 字符集编码

请求及返回结果都使用 UTF-8 字符集编码。