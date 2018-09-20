# webpack中使用  
安装: 
通过npm在webpack项目中进行本地安装  

```
$ npm isntall sesame-http --save-dev  
```

在webpack**调试环境配置**中配置devServer中的before(webpack@2.0版本为setup)

```
devServer:{
    before:(app)=>{
        sesame.setConfig({
              rulePath: path.join(__dirname,"./src/sesame.rule.js"), //绝对路径。项目所使用的拦截规则的具体文件，sesame-http会去引用这个文件  
              htmlContentPath:path.join(__dirname,"./src")           //绝对路径。如果使用文件形式的模拟数据形式，需要在此配置文件的根目录位置
        });
        sesame.webpack(app); //表示使用webpack中的app实例来取代sesame-http中的app实例
    }
}
```

关于模拟数据的具体方式请查看 [模拟数据](../mock/rule.md)  
关于setConfig请查看 [接口文档](../random/random_type.md)


