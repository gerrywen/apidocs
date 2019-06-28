# @apiParam

```
@apiParam [(group)] [{type}] [field=defaultValue] [description]
```

## Optional!

请求体参数，不是必填

## Description

描述传递给API-Method的参数。

接口请求参数，post/get写法一致

## Type

- 目前只支持String|Number|Boolean|Object[]|Object类型

- 说明：(目前暂只支持两个层级)
    - Object[]类型，表示一个数组对象   [{}]
    ```
    例子：
     * @apiParam {Object[]}     conditions                  查询条件
     * @apiParam {String}       conditions.filed_name       查询名称
     * @apiParam {String}       conditions.type             查询类型
     * @apiParam {String}       conditions.value            查询值
    ```
    - Object类型，表示一个对象   {}
    ```
    例子：
     * @apiParam {Object}       page_info                  查询条件
     * @apiParam {String}       page_info.page=1           页码
     * @apiParam {String}       page_info.per_page=10      每页多少条
    ```
     - 其他类型就正常的key=value

## Variable(命名二者选择一，不要混合使用)
- 带有变量的数据，写入env配置文件（env健值配置）
    - 命名方式一：变量名用大写和下划线（推荐）
    ```
    例子：{{TYPE_NAME}} 、 {{PER_PAHE}}、{{TYPE}}
    ```
    - 命名方式二：单个单词命名，首字母大写
    ```
    例子：{{Typename}} 、 {{Type}}
    ```
    - 说明
      - 可以不带任何变量，默认会取变量名为环境变量值，如果是对象，取对象最后一个单词变量名（如：filed_name、type）
      - env 需要配置变量名
      
- 请求参数可以带有默认值
    ```
    例子： 
    page_info.page=1
    page_info.per_page=10
    sort.direction="desc"
    sort.field_name="id"
    ```    


## Usage
```
@apiParam (MyGroup) {Number} id Users unique ID.
```

名称|是否必填|描述
--|:--:|--:
(group)|否|所有参数都将按此名称分组。<br>如果没有组，则设置默认参数。<br>您可以使用@apiDefine设置标题和说明。
{type}|否|参数类型，例如 {Boolean}，{Number}，{String}，<br>{Object}，{String []}（字符串数组），...
{type{size}}|否|有关变量大小的信息。<br>{string {.. 5}}一个包含最多5个字符的字符串。<br>{string {2..5}}一个有min的字符串。 <br>2个字符和最多5个字符。<br>{number {100-999}}一个介于100和999之间的数字。
{type=allowedValues}|否|有关变量允许值的信息。<br>{string =“small”}一个字符串，只能包含单词“small”（常量）。<br>{string =“small”，“huge”}一个字符串，可以包含单词“small”或“huge”。<br>{number = 1,2,3,99}一个允许值为1,2,3和99的数字。<br>可与尺寸组合：<br>{string {..5} =“small”，“huge”}一个字符串，最多有5个字符，只包含“small”或“huge”字样。
{field}|否|变量名
[field]|否|带括号的Fieldname将Variable定义为可选。
=defaultValue|否|参数默认值。
descriptionoptional|否|该领域的描述。

## 格式一:带有变量的请求体数据
```
@apiParam {String} nickname={{NICKNAME}}          【必填】 昵称/称呼
@apiParam {String} email={{EMAIL}}【必填】 邮箱（唯一）
```

## 格式二:可以不带任何变量，默认会取变量名为环境变量值
```
@apiParam {Object[]}     conditions                  查询条件
@apiParam {String}       conditions.filed_name       查询名称
@apiParam {String}       conditions.type             查询类型
@apiParam {String}       conditions.value            查询值
```

## 格式三:带有默认值的请求体信息
```
@apiParam {String} phone="15160333333"       【必填】 手机号码（唯一）
@apiParam {String} password="123456"         【必填】 密码
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
 */
```
