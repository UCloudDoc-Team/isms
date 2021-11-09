

# 创建智能短信模板-CreateISMSTemplate

> 您可以通过调用接口CreateISMSTemplate或者到控制台申请 智能短信模板，模板申请流程可参见官网 [智能短信模板审核规范](https://docs.ucloud.cn/isms/introduction/1025/2103) 说明；



# Request Parameters

| Parameter name  | Type   | Description                                                  | Required | Remark                        |
| --------------- | ------ | ------------------------------------------------------------ | -------- | ----------------------------- |
| Action          | String | 对应的 API 名称，CreateISMSTemplate                          | Yes      | 公共参数                      |
| PublicKey       | String | 对应的 API公钥                                               | Yes      | 公共参数                      |
| Signature       | String | 根据API公私钥及API指令生成的用户签名，参见 [签名算法](https://docs.ucloud.cn/api/summary/signature) | Yes      | 公共参数                      |
| ProjectId       | string | 项目 ID，主账号与财务账号为空时为 默认项目；子账号为必填字段，参见 [获取 项目ID](https://docs.ucloud.cn/api/summary/get_project_list) | Yes      | 公共参数                      |
| SignatureId     | string | 智能短信签名ID                                               | Yes      |                               |
| TemplateName    | string | 智能短信模板名称，不超过32个字符，每个中文、符号、英文、数字等都计为1个字。 | Yes      |                               |
| MsgTitle        | string | 智能短信标题                                                 | Yes      |                               |
| MsgContent      | string | 智能短信模板参数，base64编码后的json数组，编码前后的示例说明如下 | Yes      |                               |
| UnsubscribeInfo | string | 消息退订标识，必填项。默认 ”回T退订“                         | Yes      |                               |
| Remark          | string | 申请原因备注                                                 | Yes      |                               |
| Purpose         | int    | 模板类型：1-验证码；2-通知短信；3-会员营销；                 | Yes      | 不对外开放（默认 3-会员营销） |
| NetworkOperator | string | 需要报备的运营商。json数组的字符串格式。true-需要报备，false-不需要报备。如：{"telecom":true, "mobile":false, "unicom":true } | Yes      | 不对外开放（默认 全部true）   |



- MsgContent（Base64编码前）

| Parameter name | Type   | Description                                                  | Case                                         | Required |
| -------------- | ------ | ------------------------------------------------------------ | -------------------------------------------- | -------- |
| name           | string | 物料文件名称（含后缀），文件名称中不能出现中文，文件后缀必须和type类型保持一致 | PushMsg01.txt                                | Yes      |
| type           | string | 物料文件类型，文本为txt，图片为jpg、gif或png，音频为mp3，视频为mp4；单个模板中只能有1个视频文件； | txt                                          | Yes      |
| content        | string | 物料文件内容：如果是文本，直接传文本内容；如果是非文本，这里传Base64编码后的字符串 | 这是一条面向订阅的内部会员用户的测试宣传信息 | Yes      |



#### MsgContent示例（Base64编码前）

```json
[
    {
        "name":"PushMsg01.txt",
        "type":"txt",
        "content":"这是一条面向订阅的内部会员用户的测试宣传信息",
        "index":0      // 第一帧
    },
    {
        "name":"BannerPic.jpg",
        "type":"jpg",
        "content":"jpg文件字节的base64编码字符串",
        "index":1
    },
    {
        "name":"MusicVoice.mp3",
        "type":"mp3",
        "content":"mp3文件字节的base64编码字符串",
        "index":2
    },
    {
        "name":"ViewVideo.mp4",
        "type":"mp4",
        "content":"mp4文件字节的base64编码字符串",
        "index":3
    }
]
```



#### TaskContent示例（Base64编码后）

```json
WwogICAgewogICAgICAgICJuYW1lIjoiUHVzaE1zZzAxLnR4dCIsCiAgICAgICAgInR5cGUiOiJ0eHQiLAogICAgICAgICJjb250ZW50Ijoi6L+Z5piv5LiA5p2h6Z2i5ZCR6K6i6ZiF55qE5YaF6YOo5Lya5ZGY55So5oi355qE5rWL6K+V5a6j5Lyg5L+h5oGvIiwKICAgICAgICAiaW5kZXgiOjAgICAgICAvLyDnrKzkuIDluKcKICAgIH0sCiAgICB7CiAgICAgICAgIm5hbWUiOiJCYW5uZXJQaWMuanBnIiwKICAgICAgICAidHlwZSI6ImpwZyIsCiAgICAgICAgImNvbnRlbnQiOiJqcGfmlofku7blrZfoioLnmoRiYXNlNjTnvJbnoIHlrZfnrKbkuLIiLAogICAgICAgICJpbmRleCI6MQogICAgfSwKICAgIHsKICAgICAgICAibmFtZSI6Ik11c2ljVm9pY2UubXAzIiwKICAgICAgICAidHlwZSI6Im1wMyIsCiAgICAgICAgImNvbnRlbnQiOiJtcDPmlofku7blrZfoioLnmoRiYXNlNjTnvJbnoIHlrZfnrKbkuLIiLAogICAgICAgICJpbmRleCI6MgogICAgfSwKICAgIHsKICAgICAgICAibmFtZSI6IlZpZXdWaWRlby5tcDQiLAogICAgICAgICJ0eXBlIjoibXA0IiwKICAgICAgICAiY29udGVudCI6Im1wNOaWh+S7tuWtl+iKgueahGJhc2U2NOe8lueggeWtl+espuS4siIsCiAgICAgICAgImluZGV4IjozCiAgICB9Cl0=
```



# Response Elements

| Parameter name | Type   | Description                                          |
| -------------- | ------ | ---------------------------------------------------- |
| RetCode        | int    | 返回状态码，为 0 则为成功返回，非 0 为失败           |
| Action         | string | 操作指令名称                                         |
| Message        | string | 返回错误消息，当 `RetCode` 非 0 时提供详细的描述信息 |
| ReqUuid        | string | 本次请求Uuid                                         |
| TemplateId     | string | 申请的智能短信模板ID                                 |



# Request Example

```https
https://api.ucloud.cn/?Action=CreateISMSTemplate
&PublicKey=vsRhB0**o9elXXXXXkw8o/vm*****0vxi74A=
&Signature=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
&ProjectId=org1234
&SignatureId=SIG20*********C1F
&TemplateName=showT*******empName
&MsgTitle=share********action
&MsgContent=WwogICAgewogICAgICAgICJuYW1lIjoiU**************ozCiAgICB9Cl0=
&UnsubscribeInfo=GFl*********lvblB
&Remark=WbjN********kdAt
```

# Response Example

```json
{
    "RetCode":0,
    "Action":"CreateISMSTemplateResponse",
    "Message":"submit success",
    "ReqUuid":"abcd******************dafdsa",
    "TemplateId":"U**********6F87",
    ]
}
```