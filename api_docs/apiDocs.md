# 智能短信API 概览



如下为当前 智能短信ISMS 已开放、可调用的API接口，详细接口信息请参见对应API接口文档；

在调用API时，除了给出相应API的调用地址、公共参数、API指令及指令参数，您还需要在调用请求中给出 API 密钥进行身份认证；您可先通过查阅[ISMS智能短信 请求结构](/isms/api_docs/req_construct/req_cons) 了解相应的API用法；



### 短信发送API

| API                                                          | 说明     |
| ------------------------------------------------------------ | -------- |
| [SendISMSMessage](https://docs.ucloud.cn/api/isms-api/send_isms_message) | 发送消息 |



### 发送状态查询API

| API                                                          | 说明                 |
| ------------------------------------------------------------ | -------------------- |
| [GetISMSSendReceipt](https://docs.ucloud.cn/api/isms-api/get_isms_send_receipt) | 获取短信状态回执信息 |



### 模板申请API

| API                                                          | 说明              |
| ------------------------------------------------------------ | ----------------- |
| [CreateISMSTemplate](https://docs.ucloud.cn/api/isms-api/create_isms_template) | 申请 智能短信模板 |


