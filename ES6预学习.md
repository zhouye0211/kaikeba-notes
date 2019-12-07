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
    - 