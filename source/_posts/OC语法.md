layout: iosdev
title: OC语法
date: 2015-01-20 18:39:47
categories:
- iosdev
tags: ios obj-c
---
### 未分类
* OC每一条语句后面必须加`;`号
* 可以使用`//`注释

### 类定义
* OC类定义分为@interface部分和@implementation
##### @interface
  给调用者看的接口
```
@interface FvzIapTest : NSObject
{
  NSString* status; 
}
- (NSString *)getStatus;
- (void)setStatus1:(NSString *)inStr;
@end
```

##### @implementation
  接口的实现
```
@implementation FvzIapTest
- (NSString *)getStatus {
	return status;
}
- (void)setStatus1:(NSString *)inStr{
  status =  inStr
}
@end
```

### 对象上面的函数(方法)
```
- (void)setStatus1:(NSString *)inStr{
  status =  inStr
}
```

### 对象上面的字段(field)
* 不要用`self.status`,系统会去调用setStatus

```
- (void)setStatus1:(NSString *)inStr{
  status =  inStr
}
```
