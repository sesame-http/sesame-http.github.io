
#文件形式   
**不推荐使用此方式进行数据模拟**  
1.该方式会进行大量的文件IO读取操作，效率较低    
2.不方便数据修改  
3.可能需要建立许多文件夹及文件来保存数据  
   
例子：
项目目录结构  

 ```
 Root  
  |  
  |---index.js  
  |---index.html   
  |---api
  |    +---getUsername.js
  |---goform   
       +---getSomeThing.js
       +---getData.js
```

> 请求 api/getUsername 被匹配到时，sesame会先检查是否已经有mock的规则，如果没有则会自动去寻找是否存在\api\getUsername.xxx文件。

> 当匹配到goform/getData时，则会去goform文件夹下寻找对应的文件。

> xxx支持的类型有 js || html || json 

.js后缀的文件 
>通过module.exports返回一个数据（等价于sesame.mock()中的第三个参数），这个数据会通过sesame规则解析后并响应该请求。

[Demo .js文件]() 

非.js文件  
> 不会通过sesame规则解析，会直接返回该文件的内容

[Demo 非.js文件]()  

