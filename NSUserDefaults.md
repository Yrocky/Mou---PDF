## **NSUserDefaults：**
用来保存应用程序设置和属性、用户保存的数据。用户再次打开程序或开机后这些数据仍然存在。

NSUserDefaults可以存储的数据类型包括：`NSData`、`NSString`、`NSNumber`、`NSDate`、`NSArray`、`NSDictionary`。

如果要存储其他类型，则需要转换为前面的类型，才能用NSUserDefaults存储。具体实现为：

`保存数据：`

NSUserDefaults *defaults =[NSUserDefaults standardUserDefaults];

NSString *name =@”default string“;

[defaults setObject:firstName forKey:@"name"];
  //获得UIImage实例

UIImage *image=[[UIImage alloc]initWithContentsOfFile:@"photo.jpg"];

NSData *imageData = UIImageJPEGRepresentation(image, 100);//UIImage对象转换成NSData

[defaults synchronize];//用synchronize方法把数据持久化到standardUserDefaults数据库

`读取数据：`

NSUserDefaults *defaults =[NSUserDefaults standardUserDefaults];

NSString *name = [defaults objectForKey:@"name"];//根据键值取出name

NSData *imageData = [defaults dataForKey:@"image"];

UIImage *Image = [UIImage imageWithData:imageData];//NSData转换为UIImage
