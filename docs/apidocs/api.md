# @api

```
@api {method} path [title]
```

## Required!

请求地址必填

## Description


## Variable(命名二者选择一，不要混合使用)

- 带有变量的数据，写入env配置文件（env健值配置）
    - 命名方式一：变量名用大写和下划线（推荐）
    ```
    例子：{{USER_ID}} 、 {{COMPANY_NAME}}
    ```
    - 命名方式二：单个单词命名，首字母大写
    ```
    例子：{{Company}} 、 {{Uid}}
    ```


## Usage
```
@api {get|post|put|delete} /api/back/auth 登录.
```

名称|是否必填|描述
--|:--:|--:
method|是|请求方法
path|是|请求地址uri部分
title|是|接口标题标注

## 格式1:
```
@api  {post} /api/back/auth/login 登录
```
```
@api  {get} /api/back/auth/info 用户信息
```

## 格式2:带有变量的api地址例子
```
@api  {post} /api/back/auth/info/uid/{{USER_ID}}
```
```
@api  {get} /api/back/auth/info/uid/{{USER_ID}}
```

## Example
```
/**
 * @api {get} /api/back/auth/info/uid/{{USER_ID}}
 */
```
