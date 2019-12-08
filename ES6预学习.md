# ECMAScript 6 

## ECMAScript 基础

### ECMAScript 简介

- JavaScript 三大组成部分
  - ECMAScript
  - DOM
  - BOM
- ECMAScript 就是包含了 JS 中的语法、数据类型、表达式和运算等……

### ECMAScript 6

- let  

  - var 可以重复声明
  - let 在同一作用域不能重复声明，分块级作用域和全局作用域，块级作用域在{}内，只块里面声明只能在里面使用。let 不会进行预解析。

- const 常量

  - const 必须要给赋值，在同一作用域不能重复声明，分块级作用域和全局作用域，块级作用域在{}内，只块里面声明只能在里面使用。const 不会进行预解析。其他功能与 let 一样。

- 块级作用域

  在没有es6 前的，一般块级作用域使用一个匿名函数去解决。因为es 6中添加了块级作用域

  ```
  for(let i = 0;i < li.length; i++){
  	li[i].onclick = function(){
  		console.log(i)  //成功打印点击下的i
  	};
  }
  console.log(i)  //因为let i 只在 for 的块级作用域内报错
  ```

- 结构赋值

  - 对象结构赋值就是把对象里面的拆散一一对应赋值

    - ES6对比ES5的逻辑：更加方便开发者，更书写严格，更简化

    ```
    let obj = {
        a : 1,
        b : 2  
    }
    //ES5  
    let a = obj.a
    let b = obj.b
    console.log(a,b)  //0  1
    //ES6
    let {a,b} = obj  
    console.log(a,b)  //0  1
    ```

  - 数组结构赋值

    - 顺序必须是一样的，第0位对应数组第0位。

    快速交换两个值（面试题）

    ```
    let a = 0
    let b = 1
    // es5 
    let c = a
    a = b
    b=c
    //es6
    [a,b] = [b,a] //快速交换赋值
    
    ```

  - 展开运算符

    - …arr 就是展开运算符的语法

    - 如果是对象的话不建设直接操作，因为会直接改变对象的值

      ```
      let obj = {
          a:1,
          b:2
      }
      let obj2= obj;
      obj2.a = 10
      console.log(obj)  //obj的a值等于10
      //建议展开
      let obj2 = {...obj}  
      obj2.a = 10
      console.log(obj) //obj的a值等于1
      
      ```

  - set 对象 构造函数

    // 构造函数 用来构建某一类型的对象，也叫对象的实例化

    - 可以把一组数据去重，只保留第一次出现的值
    - .size属性  => 数值的个数
    - .clear() 清空所有值
    - .delete(val)  删除某一项，需要传入值参数，而不是下标，返回true 和false(有值和无值)
    - .add(val)  添加一项值，返回set本身
    - .has(val) 要查找的值，返回true false(有值和无值)

  - map 对象 构造函数

    - 语法同set类似，重点是传入的参数

### 字符串新增的方法 

#### str.endsWith

Boolean str.includes(valueToFind,[,fromIndex]) 判断字符串是否包含一个指定的值

#### str.startsWith

Boolean str.endsWith(searchString[, length]) 判断当前字符串是否是以另外一个给定的子字符串"结尾"

#### str.endWith

Boolean str.startsWith(searchString[, position]) 判断当前字符串是否以另外一个给定的子字符串"开头"

#### str.repeat()

String str.repeat(count) 构造并返回一个新字符串，该字符串包含被连接在一起的指定数量的字符串的副本

#### 模板字符串（用于模板字符串的拼接方式）

模板字面量 是允许嵌入表达式的字符串字面量。你可以使用多行字符串和字符串插值功能。它们在ES2015规范的先前版本中被称为“模板字符串”。    

###　对象新增的方法

```
// es6简洁表示法
let a = 0;
let b = 1;
let　obj = {
    a,
    b
};
console.log(obj) //｛ a:0,b=1 ｝
```

#### 新增属性表达式

函数简洁了写法，属性可以在里面直接赋值，需要给[]括号.

```
// es6属性表示式
let name = "小明＂；
let　obj = {
	c(){  					//es６简洁写法
        console.log("a")  
	}，
	[name]:1111
};
console.log(obj)   //{c:{},小明:111}
//es5
var name = "小明＂；
var　obj = {
	c(){  					//es６简洁写法
        console.log("a")  
	}
};
obj[name] = 111
console.log(obj)   //{c:{},小明:111}
```

#### Object.assign()（合并两个字符串）

Object Object.assign(target, ...sources) 将所有可枚举属性的值从一个或多个源对象复制到目标对象

```
let obj = {
    a:1,
    b:2
}
let obj2 = {
    c:3,
    d:4
}
//展开法
let obj3 = {
    ...obj,
    ...obj2
}
console.log(obj3)  //{a: 1, b: 2, c: 3, d: 4}
//新增Object.assign()
Obejct.assign(obj2,obj)//合并到第一个参数内
var obj2 = Obejct.assign({},obj2,obj ) //合并到第一个参数内
```

### Object.is()（比较两个值）

Boolean Object.is(value1, value2) 判断两个值是否是相同的值。 

规则：
    两个值都是 undefined
    两个值都是 null
    两个值都是 true 或者都是 false
    两个值是由相同个数的字符按照相同的顺序组成的字符串
    两个值指向同一个对象
    两个值都是数字并且
        **都是正零 +0**
        **都是负零 -0**
        **都是 NaN**

注意：+0和-0在isj里面判断与比较类型===有点区别，is里面返回false

NaN在is里面判断也是不同天类型===比较，is比较返回true



### Babel使用（兼容）

Babel 是一个JavaScript的一个编译器．

也可以在浏览器中直接使用Babel，只需要引入和在＜script type="text/bable"＞即可．但是什么影响性能，不推荐使用，需要在本地去使用，比如webpack等