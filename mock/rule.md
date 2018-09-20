sesame-http提供了两种模拟数据的形式。
规则形式（**推荐** ）以及文件形式    
你可以根据项目需要来选择，也可以选择混合使用。  

#规则形式  
类似于mock.js的语法规则   
首先你需要创建一个sesame.rule.js的文件，在其中写入相应的规则。  
并且可以在内部require其他的规则文件从而模块化  

语法 ：
```
sesame.mock(url,method,data);
```

###url
@type: String  
@default:null  
@required: 必填  
@description:表示你需要拦截的请求    

###method 
@type: String  
@default: POST   
@required: 非必填，如果不填则第二个参数为data    
@description:表示需要拦截的请求方法，大小写均可。 可能的值 POST || GET || PUT || DELETE ...等  

###data
@type: Object || Array || Function
@default:null  
@require:必填  
@description:表示需要返回的数据   
@return 如果为function对象时，返回指定的数据   

> 当该值为一个非function时，表示通过sesame解析该对象，并返回对应规则的json数据。 

> 具体解析规则见[随机数据](../random/random.md)  
查看[Demo..Todo]()

> 当该值为一个function时，sesame在拦截到对应的请求后会执行这个function，传入参数为请求对象（同express的[request对象](http://www.expressjs.com.cn/4x/api.html#req)）。你可以根据请求对象来返回具体的数值。也可以通过调用sesame内置的函数来生成随机数。    
最后该函数需要返回一个数据，作为该请求的返回值。

例子：
```
sesame.mock("goform/getMyData","post",{
    id:{   //表示随机生成一个1~12的随机数
        $type:"number",
        range:[1,12]
    },
    ip:{   //表示随机生成一个ip  192.168.x.123  x为0~2
        $type:"ip",
        range:"192.168.0-2.123"
    }
});
//当匹配到post请求goform/getMyData时,返回如下数据  
{
    id:12,
    ip:"192.168.0.123"
}
```


查看更多[Demo..Todo]()
