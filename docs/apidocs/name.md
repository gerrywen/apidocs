# @apiName

```
@apiName name
```

## Required!

接口名称必填， 且全局唯一

## Description

接口名称全局唯一
模块名+接口方法名(用下划线连接)
例子：admin_index 、 admin_show 、user_info、user_update



## Usage
```
@apiName admin_index
```

名称|是否必填|描述
--|:--:|--:
name|是|接口名，全局唯一

## 格式:
```
@apiName admin_index
```
```
@apiName user_info
```

## Example
```
/**
 * @api {get} /api/back/auth/info/uid/{{USER_ID}}
 * @apiName admin_index
 */
```
