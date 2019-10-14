# 一、React介绍
1. React与Vue对比（引战）
    > 相通点   数据驱动视图的思想
    > 不同点   如非必要，勿增实体

2. 门槛较高，多金

3. 特征：声明式，组件化

# 二、React开发环境搭建
1. 创建目录环境
```
npx create-react-app react-app
```
2. 运行项目
```
cd react-app
npm run start
```

3. 认识目录结构
```
    |--react-app
    |-----public  存放公共资源
    |-----src   
    |----------index.js   项目入口文件
    |----------App.js    react组件（函数式组件）
    |----------components  存放项目组件
```
# 三、React基本语法
1. JSX语法认识
```
let ele = '<div>我是普通字符串标签</div>'

let ele = <div>react的jsx结构代码</div>
```
2. JSX里面的基本操作
```
定义：
let name="张三丰";
let num=123;
function sum(a,b){
  return a+b;
}

使用：
<div className="App">
    <p>{name}</p>
    <p>{`我的姓名是:${name}`}</p>
    <p>{1+3}</p>
    <p>{sum(100,200)}</p>
    <p>{1>2?'真的':'假的'}</p>
    <p>{'Hello' || 'Everyone'}</p>
</div>
```
3. 属性、样式、嵌套

+ 属性名称className，一旦属性名是js的关键字（保留字），需要替换为其他属性名称。

+ 样式动态绑定
> 注意双大括号的含义，跟vue中的{{}}含义不同
> 外层{}  代表动态数据
> 内层{}  代表是一个对象类型的数据
```
<div className="box" style={{
    'background':boxColor,
    'transform':rote
    }}></div>
```
4. React中的组件
> 一个js文件就是一个组件
> 组件名称在使用的时候，首字母必须大写，小写会被识别为普通自定义标签。
+ 组件的分类
    - 函数式组件
    - 类组件

+ 函数式组件
```
定义组件Man.js：
import React from 'react'
export default function Man(){
    return (
        <div>
            <h1>我是Man组件</h1>
            <p>我的理想是有个事少钱多离家近的工作</p>
        </div>
    )
}

在App.js中使用Man组件
import Man from './components/Man'
<Man />
```

+ 类组件 
> 提醒：复习ES6的class类语法、类的继承、解构赋值
```
定义God.js组件
import React,{Component} from 'react'
export default class God extends Component{
    render(){
        return (
            <div>
                <h1>我是上帝</h1>
                <p>我的理想是世界和平</p>
            </div>
        )
    }
}

在App.js中使用God组件
import God from './components/God'
<God />
```

5. state状态
> 旧的版本中只有类组件内部才能定义使用state
```
export default class God extends Component{
    constructor(){
        super()
        this.state = { //【1】定义状态数据
            num1:1,
            num2:2
        }
    }
    render(){
        let {num1,num2} = this.state;
        return (
            <div>
                <h1>我是上帝</h1>
                <p>我的理想是世界和平</p>
               {/* 【2】state状态数据的渲染使用 */}
                <p>{this.state.num1}</p>
                <p>{this.state.num2}</p>
                <p>{num1}</p>
                <p>{num2}</p>
                {/* 【3】通过事件，修改state状态变化，从而引发视图变化 */}
                <button onClick={()=>{
                   num1++;
                   num2 = num1*2;
                   this.setState({
                        num1,
                        num2
                    })
                }}>按钮</button>
            </div>
        )
    }
}
```


