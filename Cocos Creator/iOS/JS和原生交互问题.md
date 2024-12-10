# JS和原生交互问题

1. 使用JsbBridge向JS发送数据时需注意，它提供了如下接口:
```
typedef void (^ICallback)(NSString*, NSString*);

@interface JsbBridge : NSObject
+ (instancetype)sharedInstance;
- (void)setCallback:(ICallback)cb;
- (bool)callByScript:(NSString*)arg0 arg1:(NSString*)arg1;
- (void)sendToScript:(NSString*)arg0 arg1:(NSString*)arg1;
- (void)sendToScript:(NSString*)arg0;
@end

```

如果发送数据第二个参数为空需要使用

```
- (void)sendToScript:(NSString*)arg0
```
而不是
```
- (void)sendToScript:(NSString*)arg0 arg1:(NSString*)arg1;
```
否则会崩溃