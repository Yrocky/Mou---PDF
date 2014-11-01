#AFNetWorking知识点总结

##1.学习AFNetWorking的背景知识
```
AFNetWorking是一个封装了网络抽象层和苹果官方网络SDK的网络框架，AFNetWorking有方便使用的优点，它请求到得数据经过了JSON解析，可以直接使用。

AFNetworking官方文档 http://cocoadocs.org/docsets/AFNetworking/2.3.1/index.html
```

##2.AFNetworking中关键的类

```
1.AFHTTPRequestOperationManager					  管理AFHTTPRequestOperation对象
2.AFHTTPRequestOperation						  
3.AFURLRequestSerialization
4.AFURLResponseSerialization
5.AFURLSessionManager（NSURLSessionConfiguration） 创建和管理NSURLSession对象
  NSURLSessionUploadTask						   上传任务
  NSURLSessionDownloadTask					       下载任务
  NSURLSessionDataTask							    数据流任务
```
```
GET请求例子
AFHTTPRequestOperationManager *manager = [AFHTTPRequestOperationManager}];￼manager];￼[manager GET:@"http://example.com/resources.json" parameters:nil￼success:^(AFHTTPRequestOperation *operation, id responseObject) {￼NSLog(@"JSON: %@", responseObject);￼} failure:^(AFHTTPRequestOperation *operation, NSError *error) {￼NSLog(@"Error: %@", error);￼￼


POST请求例子
AFHTTPRequestOperationManager *manager = [AFHTTPRequestOperationManager￼manager];NSDictionary *parameters = @{@"foo": @"bar"};NSURL *filePath = [NSURL fileURLWithPath:@"file://path/to/image.png"];[manager POST:@"http://example.com/resources.json" parameters:parametersconstructingBodyWithBlock:^(id<AFMultipartFormData> formData) {[formData appendPartWithFileURL:filePath name:@"image" error:nil];} success:^(AFHTTPRequestOperation *operation, id responseObject) {NSLog(@"Success: %@", responseObject);} failure:^(AFHTTPRequestOperation *operation, NSError *error) {NSLog(@"Error: %@", error);}];
```
```
Demo:
1.利用AFHTTPRequestOperationManager，通过URL获取JSON数据

2.利用AFHTTPRequestOperation，通过URL获取数据

3.通过AFNetWorking封装的类实现图片异步下载

4.通过URL获取plist文件内容

5.POST  Multi-Part使用
```

