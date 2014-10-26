Predicat
===
1. 常用的predicate定义:

	  NSPredicate *predicate = [NSPredicate predicateWithFormat:@""];
  
2. 谓词的关系运算

	   //1. 定义一个数组，展示谓词中关系运算符的基本使用
	   NSArray *number = @[@12,@34,@24,@89,@799];
	   
	   //1.1 创建一个predicate对象
	   //在iOS的谓词中，self代表自身
	   //谓词的关系运算符 >. <. ==. >=. <=. !=
	   //查找数组中大于50的所有对象
	   NSPredicate *numberPredicate = [NSPredicate predicateWithFormat:@"self > 50"];
	   
	   //1.2 使用谓词对数组进行过滤(filter)
	   NSArray *numberResult = [number filteredArrayUsingPredicate:numberPredicate];
	   NSLog(@"1 numberResult->%@",numberResult);
	   
3. 组合谓词比较

        //2. 对数组中的对象进行组合谓词比较
        //IN 和 BETWWEEN
        //and 或者 && ， or 或者 ||
        NSArray *personArray = @[[Person personWithName:@"zhangsan" andAge:@12],
                                 [Person personWithName:@"lisi" andAge:@20],
                                 [Person personWithName:@"wangwu" andAge:@30],
                                 [Person personWithName:@"Zhaoliu" andAge:@35]
                                ];
        NSPredicate *personPredicate = [NSPredicate predicateWithFormat:@"name = 'lisi' and age between {20,50}"];
        NSArray *personResult = [personArray filteredArrayUsingPredicate:personPredicate];
        NSLog(@"2 personResult->%@",personResult);
        
4. 使用like  、in 、contanis 、正则表达式 4种方法
 

        //like ？ 适用于单个字符的通配  * 是不分数目的通配符
        NSPredicate *likePredicate = [NSPredicate predicateWithFormat:@"self like '?i*'"];
        
        //in 取出两个集合中共有的元素
        NSPredicate *inPredicate = [NSPredicate predicateWithFormat:@"self in %@",filterArray];
        
        //contains 取出原集合中含有某一个对象的元素
        NSPredicate *containsPredicate = [NSPredicate predicateWithFormat:@"self contains %@",string];
        
        //正则表达式
        NSString *regex = @"w.*u";
        NSPredicate *regexPredicate = [NSPredicate predicateWithFormat:@"name matches %@",regex];
        
        //正则表达式
        NSString *regexStr = @"^zh[0-9].+";
        NSPredicate *regexPredicate2 = [NSPredicate predicateWithFormat:@"self matches %@",regexStr];
        
        //正则表达式
        NSString *regexSelf = @"[a-z]*(a|o).*iu.*";
        NSString *testString = @"nihaoliuxia";
        NSPredicate *selfPredicate = [NSPredicate predicateWithFormat:@"self matches %@",regexSelf];
        if ([selfPredicate evaluateWithObject: testString]) {//evaluate 适配
            NSLog(@"Evaluate");
        }else{
        
            NSLog(@"Unevaluate");
        }
        
5. 字符串的模糊匹配

	      //BEGINSWITH  ENDSWITH 和 CONTANIS，[c]不区分大小写 [d]不区分重音符号
	      
	      //以w开始以u结尾
	      [NSPredicate predicateWithFormat:@"self beginswith 'w' or self endswith 'u'"];
	      //以zha开始
	      [NSPredicate predicateWithFormat:@"name beginswith [c]'zha'"];
	      //包含lis字符
	      [NSPredicate predicateWithFormat:@"name contains 'lis'"];

6. 谓词的语法

	    //替换 %K 是对key path的替换 %@ 是对值为字符串，数字或者日期的对象的替换
        NSPredicate *replacePredicate = [NSPredicate predicateWithFormat:@"%K = %@",@"age",@30];//必须大写K
                
        //使用$变量
        //先弄一个谓词模板
        NSPredicate *predicateTemp = [NSPredicate predicateWithFormat:@"name = $NAME"];//$
        //然后写一个字典
        NSDictionary *dictionary = @{@"NAME":@"lisi"};
        NSPredicate *pred = [predicateTemp predicateWithSubstitutionVariables:dictionary];
        NSArray *arr = [personArray filteredArrayUsingPredicate:pred];
        
        //使用$变量求一个范围
        NSPredicate *predTemp = [NSPredicate predicateWithFormat:@"%K between $AGE_RANGE",@"age"];
        NSNumber *beginAge = @20;
        NSNumber *endAge = @50;
        NSDictionary *rangeDic = @{@"AGE_RANGE":@[beginAge,endAge]};//这里必须使用数组来界定一个范围
        pred = [predTemp predicateWithSubstitutionVariables:rangeDic];
        arr = [personArray filteredArrayUsingPredicate:pred];

	