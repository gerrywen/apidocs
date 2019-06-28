# @apiHeader

```
@apiHeader [(group)] [{type}] [field=defaultValue] [description]
```

## Optional!

请求头部参数，不是必填

## Description

描述传递给API API-Header的参数，例如 用于授权。

与@apiParam类似的操作，只有输出高于参数。

## Type

- 目前暂只支持String|Number|Boolean类型

## Variable(命名二者选择一，不要混合使用)

- 带有变量的数据，写入env配置文件（env健值配置）
    - 命名方式一：变量名用大写和下划线（推荐）
    ```
    例子：{{AUTHORRIZATION}} 、 {{USER_NAME}}
    ```
    - 命名方式二：单个单词命名，首字母大写
    ```
    例子：{{Authorization}} 、 {{Token}}
    ```
    - 说明
      - 可以不带任何变量，默认会取变量名为环境变量值
      - env 需要配置变量名

- 头部数据可以带有默认值
    ```
    例子：Content-Type="application/json"
    ```    


## Usage
```
@apiHeader (MyHeaderGroup) {String} authorization Authorization value.
```

名称|是否必填|描述
--|:--:|--:
(group)|否|所有参数都将按此名称分组。如果没有组，则设置默认参数。您可以使用@apiDefine设置标题和说明。
{type}|否|参数类型，例如 {Boolean}，{Number}，{String}，{Object}，{String []}（字符串数组），...
{field}|否|变量名
[field]|否|带括号的Fieldname将Variable定义为可选。
=defaultValue|否|参数默认值。
descriptionoptional|否|该领域的描述。

## 格式一:带有变量的头部数据
```
@apiHeader {String} Authorization={{Authorization}} 用户授权token
```

## 格式二:可以不带任何变量，默认会取变量名为环境变量值
```
@apiHeader {String} Authorization={{Authorization}} 用户授权token
```

## 格式三:带有默认值的头部信息
```
@apiHeader {String} Content-Type="application/json" 内容类型
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
 * @apiHeader {String} Platform 平台
 */
```
