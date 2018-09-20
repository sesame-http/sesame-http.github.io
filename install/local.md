# 本地使用

安装：

通过npm进行全局安装，安装一次即可在本地各处使用。

```
$ npm install sesame-http -g
```

开发调试，在项目目录上使用命令

```
$ sesame-http open
```

可选配置项：
- -p或者--port表示监控的端口  
- -w或者--where表示监控的目录相对路径  

例如 
```
$ sesame-http open -p 4000 -w test
```
表示在4000端口上监听当前目录下 test文件夹下的项目

关于模拟数据的具体方式请查看 [模拟数据](../mock/rule.md)
