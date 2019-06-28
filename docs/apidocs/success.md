# @apiSuccess

```
@apiSuccess [(group)] [{type}] field [description]
```

## Optional!

可选

## Description

请求成功返回值


## Type

- 目前只支持String|Number|Boolean|Object类型

- 说明：(目前不支持数组对象)
    - Object类型，表示一个对象   {}
    ```
    例子：
     * @apiSuccess {Object}             data                      数据结果
     * @apiSuccess {Number}             data.total_count         条数
    ```

## Variable

返回值name，与接口返回值格式一致





## Usage
```
@apiSuccess {String} firstname Firstname of the User.
```

名称|是否必填|描述
--|:--:|--:
(group)|否|可选所有参数将按此名称分组。<br>如果没有组，则设置默认成功200。<br>您可以使用@apiDefine设置标题和说明。<br>
{type}|否|参数类型，例如 {Boolean}，{Number}，{String}，<br>{Object}，{String []}（字符串数组），...
{field}|否|变量名
descriptionoptional|否|该领域的描述。

## 格式:返回值格式
```
@apiSuccess {Object}             data                      数据结果
@apiSuccess {Number}             data.total_count          条数
```


## Example
```
/**
 * @api {get} /api/back/auth/info/uid/{{USER_ID}}
 * @apiName admin_index
 * @apiGroup admin
 *
 * @apiHeader {String} Authorization={{Authorization}} 用户授权token
 * @apiHeader {String} Content-Type="application/json" 内容类型
 *
 *
 * @apiParam {String} nickname={{NICKNAME}}          【必填】 昵称/称呼
 * @apiParam {String} email                          【必填】 邮箱（唯一）
 * @apiParam {String} phone="15160333333"            【必填】 手机号码（唯一）
 * @apiParam {String} password="123456"              【必填】 密码
 *
 * @apiParam {Object[]}     conditions                  查询条件
 * @apiParam {String}       conditions.filed_name       查询名称
 * @apiParam {String}       conditions.type             查询类型
 * @apiParam {String}       conditions.value            查询值
 *
 * @apiParam {Object}       page_info                  查询条件
 * @apiParam {String}       page_info.page=1           页码
 * @apiParam {String}       page_info.per_page=10      每页多少条
 *
 *
 *
 * @apiSuccess {Number}             code=0                    状态码
 * @apiSuccess {Number}             status_code=200           接口状态码
 * @apiSuccess {String}             message='请求成功'         返回消息
 *
 * @apiSuccess {Object}             data                       数据结果
 * @apiSuccess {Number}             data.total_count           条数
 */
```

- 备注：
   - code 、 status_code 、 message 可以不写，有写的话会验证响应回来的数据是否一致
   - data层级开始的数据，不需要有默认值，这是请求响应的数据
