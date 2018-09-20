#随机数拓展   

> 如果你需要拓展自己的随机数    
> 你可以通过sesame.extend函数来进行拓展


#sesame.random.extend(type, generator)

@params:

type:表示随机数的名字，在$type中调用时，名字需要一致  

generator:  一个generator实例继承自sesame.RandomGenerator 




例子：随机颜色生成器

```
//sesame.rule.js
let colorGenerator = require("colorGenerator");

sesame.random.extend("color",colorGenerator);

sesame.mock("/api/getRandomColor","post",{
    color:{
        $type:"color",
        range:["00ff00","00ffff"]
    }
});

```

```
//colorGenerator.js

let RandomGenerator = sesame.RandomGenerator;

class ColorGenerator extends RandomGenerator{
    constructor() {
       //必须有super()否则无法继承，this失效
        super();
    }

    random(opt) {
        //随机数生成的方法
        //当然你也可以根据你的参数来生成
    let color = Math.floor(Math.random()*0x1000000).toString(16);
        color = ("00000"+color).substr(-6);
    
        return `#${color}`;
    }

}
module.exports = new ColorGenerator();


```