# @apiGroup

```
@apiGroup name
```

## Required!

模块名必填

## Description

组的名称。 也用作导航标题。



## Usage
```
@apiGroup admin
```

名称|是否必填|描述
--|:--:|--:
name|是|组的名称。 也用作导航标题。

## 格式:
```
@apiGroup admin
```
```
@apiGroup user
```

## Example
```
/**
 * @api {get} /api/back/auth/info/uid/{{USER_ID}}
 * @apiName admin_index
 * @apiGroup admin
 */
```
