<a name="k6DsL"></a>
## **网关地址**
> 请求地址<br />`host = [https://third.gateway.smtbs.cn](https://iot.gateway.smtbs.cn)`<br />请求地址：<br />host + 接口前缀 + 接口路径<br />接口前缀：
> 授权相关接口前缀:  auth<br />健康相关接口前缀：health<br />门店相关接口前缀：store<br />商品相关接口前缀：goods<br />订单相关接口前缀：order<br />考培相关接口前缀：kaopei<br />例：访问商品列表接口<br />`[https://third.gateway.smtbs.cn](https://iot.gateway.smtbs.cn)/goods/page`<br />访问订单、售后列表接口：
> `[https://third.gateway.smtbs.cn](https://iot.gateway.smtbs.cn)/order/page`

<a name="OJdfC"></a>
# 1. **接口清单**
<a name="jrOR9"></a>
## 1.1. **统一授权**
<a name="p0t0H"></a>
### 基本信息
**Path：**`/oauth/token`<br />**Method：** `POST`<br />**Description：签发令牌**
<a name="jIwGc"></a>
### 请求参数
**Headers**

| 参数名称 | 参数值 | 是否必须 | 备注 |
| --- | --- | --- | --- |
| Content-Type | application/x-www-form-urlencoded | 是 |  |

**Body**
> scope:server
> grant_type:client_credentials
> client_id:jGGB3Naw
> client_secret:136981933fe8dae3d9c42e0755f17d7337857e3d

| 参数 | 说明 | 类型 | 是否可为空 |
| --- | --- | --- | --- |
| scope | 访问域 | string | 是 |
| grant_type | 授权方式 | string | 否 |
| client_id | 账号 | string | 否 |
| client_secret | 密钥 | string | 否 |

<a name="j8C9b"></a>
### 返回数据
```json
{
    "access_token":"1a2ab417-c0ae-49b2-9dbe-2d9802c7c69c",
    "token_type":"bearer",
    "expires_in":7200,
    "scope":"server"
}
```
6) 返回字段说明

| 字段 | 说明类型 | 数据类型 | 备注 |
| --- | --- | --- | --- |
| access_token | 令牌 | string | <br /> |
| token_type | 类型 | string | <br /> |
| expires_in | 过期时间 | number | 单位/秒 |
| scope | 访问域 | string | <br /> |

说明：<br />1.发布生产环境则会重新颁发账号密码<br />2.令牌的过期时间为 2小时
<a name="Xmuse"></a>
## 2.1. **开放平台**
<a name="XZEZB"></a>
### 2.2.1. 推送客户信息(下行接口)
<a name="MDTtz"></a>
#### 基本信息
**Path：**`未知`<br />**Method：** 未知<br />**接口描述：接收众康联推送的客户信息**
<a name="o5aO8"></a>
#### 请求参数
**Headers**

| 参数名称 | 参数值 | 是否必须 | 备注 |
| --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |

**Body**
```json
{
        "id":"225",
        "realName":"韩可可",
        "cardId":"110101202311050818",
        "phone":"13645514005",
        "address":"",
        "birthday":"2021-08-24",
        "gender":"1",
        "age": 18,
        "height":"188",
        "weight":"90",
        "qualification":"1",
        "married":"1",
        "ywStr":[
            {
                "label":"否",
                "type":"operation",
                "name":"您是否有过手术",
                "id":1367,
                "value":"0"
            },
            {
                "label":"臀部",
                "type":"body_part",
                "name":"手术的部位",
                "id":1370,
                "value":"2"
            }
        ],
        "xlStr":[
            {
                "label":"否",
                "type":"psychotherapy",
                "name":"您是否有过心理性疾病",
                "id":1357,
                "value":"0"
            },
            {
                "label":"是",
                "type":"mental_disease",
                "name":"您是否接受过心里咨询或治疗",
                "id":1360,
                "value":"1"
            }
        ],
        "ycStr":[
            {
                "label":"否",
                "type":"inherited_disease",
                "name":"您是否有家族遗传病史",
                "id":1361,
                "value":"0"
            },
            {
                "label":"否",
                "type":"inherited_disease_effect",
                "name":"该遗传病是否影响到您的生活",
                "id":1363,
                "value":"0"
            }
        ],
        "gmStr":[
            {
                "label":"否",
                "type":"allergy",
                "name":"您是否有过身体过敏记录",
                "id":1341,
                "value":"0"
            },
            {
                "label":"短",
                "type":"allergy_time",
                "name":"您过敏的持续时间是",
                "id":1343,
                "value":"1"
            },
            {
                "label":"哮喘",
                "type":"allergy_symptoms",
                "name":"您过敏的主要症状是",
                "id":1345,
                "value":"1"
            },
            {
                "label":"化妆品过敏",
                "type":"allergy_reason",
                "name":"您过敏的原因是",
                "id":1350,
                "value":"1"
            }
        ],
        "createTime":"2021-08-24 11:28:41",
        "latitude": "0",
        "latitude": "0"
    }
}
```
| 名称 | 类型 | 是否可为空 | 备注 | 其他信息 |
| --- | --- | --- | --- | --- |
| member | Object | 是 | 成员信息 |  |
| ├── id | String | 是 | ID |  |
| ├── realName | String | 是 | 真实姓名 |  |
| ├── cardId | String | 是 | 身份证号 |  |
| ├── phone | String | 否 | 电话号码 |  |
| ├── address | String | 是 | 地址 |  |
| ├── birthday | String | 是 | 出生日期 | 格式：YYYY-MM-DD |
| ├── gender | String | 是 | 性别 | 1: 男性, 2: 女性, 0: 未知 |
| ├── age | Number | 是 | 年龄 |  |
| ├── height | String | 是 | 身高 | 格式：数字+单位 (如：188 cm) |
| ├── weight | String | 是 | 体重 | 格式：数字+单位 (如：90 kg) |
| ├── qualification | String | 是 | 学历 | 1: 本科及以上, 2: 硕士, 3: 博士, 4: 其他 |
| ├── married | String | 是 | 婚姻状况 | 1: 已婚, 0: 未婚, 2: 离异, 3: 丧偶 |
| ├── ywStr | Array of Object | 是 | 意外伤害 |  |
| │   ├── label | String | 是 | 标签 |  |
| │   ├── type | String | 是 | 类型 | operation: 手术, body_part: 手术部位 |
| │   ├── name | String | 是 | 名称 |  |
| │   ├── id | Number | 是 | ID |  |
| │   ├── value | String | 是 | 值 |  |
| ├── xlStr | Array of Object | 是 | 心理病史 |  |
| │   ├── label | String | 是 | 标签 |  |
| │   ├── type | String | 是 | 类型 | psychotherapy: 心理性疾病, mental_disease: 心里咨询或治疗 |
| │   ├── name | String | 是 | 名称 |  |
| │   ├── id | Number | 是 | ID |  |
| │   ├── value | String | 是 | 值 |  |
| ├── ycStr | Array of Object | 是 | 遗传病史 |  |
| │   ├── label | String | 是 | 标签 |  |
| │   ├── type | String | 是 | 类型 | inherited_disease: 家族遗传病史, inherited_disease_effect: 遗传病是否影响生活 |
| │   ├── name | String | 是 | 名称 |  |
| │   ├── id | Number | 是 | ID |  |
| │   ├── value | String | 是 | 值 |  |
| ├── gmStr | Array of Object | 是 | 过敏信息 |  |
| │   ├── label | String | 是 | 标签 |  |
| │   ├── type | String | 是 | 类型 | allergy: 身体过敏记录, allergy_time: 过敏持续时间, allergy_symptoms: 过敏主要症状, allergy_reason: 过敏原因 |
| │   ├── name | String | 是 | 名称 |  |
| │   ├── id | Number | 是 | ID |  |
| │   ├── value | String | 是 | 值 |  |
| ├── longitude | Number | 是 | 经度 | 经度坐标，小数点后6位 |
| ├── latitude | Number | 是 | 纬度 | 纬度坐标，小数点后6位 |
| ├── createTime | String | 是 | 创建时间 | 格式：YYYY-MM-DD HH:MM:SS |

<a name="BXsck"></a>
#### 返回数据
```json
{
    "code":0,
    "msg":"处理成功",
    "data":true
}
```
| 字段 | 说明类型 | 数据类型 | 备注 |
| --- | --- | --- | --- |
| code | 响应错误编码 | int | 0成功1失败 |
| mgs | 响应错误信息 | string | 提示信息 |
| data | 响应内容 | object | 响应数据 |

<a name="h1Lbs"></a>
### 2.2.2. 更新客户信息(上行接口)
<a name="HSUWt"></a>
#### 基本信息
**Path：**`/health/crm/member/updateByPhone`<br />**Method：** `PUT`<br />**Description：接收第三方推送的客户信息**
<a name="H3fGQ"></a>
#### 请求参数
**Headers**

| 参数名称 | 参数值 | 是否必须 | 备注 |
| --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |
| Authorization | Bearer {{token}} | 是 | Bearer与token用一个空格分割 |

**Body**<br />**⚠️ 说明：请自行定义数据格式, 必须包含用户的手机号码，用来作为用户身份的唯一识别依据;**
<a name="ronul"></a>
#### 返回数据
```json
{
    "code":0,
    "msg":"处理成功",
    "data":true
}
```
| 字段 | 说明类型 | 数据类型 | 备注 |
| --- | --- | --- | --- |
| code | 响应错误编码 | int | 0成功1失败 |
| mgs | 响应错误信息 | string | 提示信息 |
| data | 响应内容 | object | 响应数据 |

<a name="PoDF0"></a>
### 2.2.3. 获取客户报告(上行接口)
<a name="ljauL"></a>
#### 基本信息
**Path：**`/health/crm/member/createReportByPhone`<br />**Method：** `POST`<br />**Description：接收第三方推送的客户健康报告**
<a name="tt45W"></a>
#### 请求参数
**Headers**

| 参数名称 | 参数值 | 是否必须 | 备注 |
| --- | --- | --- | --- |
| Content-Type | application/json | 是 |  |
| Authorization | Bearer {{token}} | 是 | Bearer与token用一个空格分割 |

**Body**
```json
{
  "phone": "13645514005",
  "attachment": [{
    "url": "https://127.0.0.1/health/9363125275b8472ba7dbfdb342845c93.jpg",
    "type": "pdf",
    "createTime":"2021-08-24 11:28:41"
  }]
}
```
| 名称 | 类型 | 是否必须 | 备注 |
| --- | --- | --- | --- |
| phone | string | 是 | 手机号 |
| attachment | Array of Object | 是 | 附件 |
|  | ├── url | 是 | 附件链接 |
|  | ├── type | 否 | 类型 |
|  | ├── createTime | 否 | 创建时间 |

<a name="EWPVP"></a>
#### 返回数据
```json
{
    "code":0,
    "msg":"处理成功",
    "data":true
}
```
| 字段 | 说明类型 | 数据类型 | 备注 |
| --- | --- | --- | --- |
| code | 响应错误编码 | int | 0成功1失败 |
| mgs | 响应错误信息 | string | 提示信息 |
| data | 响应内容 | object | 响应数据 |

<a name="L5OEa"></a>
# 3. **接口响应状态码**
| 编码 | 说明 | 备注 |
| --- | --- | --- |
| 401 | 无权限 | <br /> |
| 403 | 资源受限制 |  |
| 424 | 令牌过期 |  |
| 0 | 成功 | <br /> |
| 1 | 错误 |  |
