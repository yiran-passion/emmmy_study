## 详细了解 JavaScript 的 V8 引擎工作原理

### event loop（事件循环机制）

### 执行上下文

- 执行上下文主要包括三部分：变量环境，词法环境，this 关键字

  - 变量环境用于存放 var 声明的变量和声明的函数
  - 词法环境用于存放 let const 声明的变量

### 对象

- 在 V8 中，对象主要是有三个指针构成的：隐藏类，property ( 命名属性 )，element ( 可索引属性 ) 。

  - 命名属性按照创建顺序拍戏，可索引属性按照大小排序。
  - 同时存在命名属性和可索引属性，两者存在明显分隔。
  - 在 Chrome 浏览器中，一般都是可索引属性先出现，命名属性后出现。
  
    特殊情况下：如果为索引属性添加一个属性很大的索引，数组变成了稀疏数组。为了节省空间，稀疏数组会转换成哈希存储。

- 命名属性的不同存储方式：对象内属性，快属性，慢属性。

  - 对象属性在对象本身，访问速度最快。
  - 快属性比对象内属性多了一次寻址时间。
  - 慢属性会在对象内储存完整的结构。


### 原型链

- 概念：在我们的 JavaScript 中，每一个对象都有他自己的原型 ( prototype )，这个原型也是一个对象，当我们访问一个对象的属性或者方法时，如果在对象本身没有找到，可以在对象的原型中查找，这个查找查找属性或方法的路径就叫做原型链。

- 继承：

  ```js
  /** 原型链继承，通过对象的 `__proto__` 继承 */
  let animal = {
    type: 'animal',
    getType() {
      return this.type
    }
  }
  let dog = {}
  dog.__proto__ = animal
  ```

  ```js
  /** 手写构造函数 */
  function MyNew(constructor, ...args) {
    // 方法一：创建一个空的对象，这个对象将作为构造函数的实例
    // const obj = Object.create(constructor.prototype);
    // 方法二：使用 __proto__ 原型链继承
    const obj = {}
    obj.__proto__ = constructor.prototype
    // 调用构造函数，并将this绑定到新创建的对象上，同时传入参数
    const result = constructor.apply(obj, args);
    // 如果构造函数返回的是一个对象（非null），则返回这个对象，否则返回创建的实例对象
    return (typeof result === 'object' && result!== null)? result : obj;
  }
  /** 构造函数继承 */
  function Animal(type, color) {
    this.type = type
    this.color = color
  }
  Animal.prototype.alive = true
  let dog = MyNew(Animal, 'Dog', 'black')
  let cat = MyNew(Animal, 'cat', 'orange')
  console.log(dog.alive)
  ```


### 作用域链

- JavaScript 中的作用域链是由词法作用域决定的。词法作用域是由函数的声明位置来决定的，跟函数的执行位置无关，在代码编译阶段就确定好作用域。

- 作用域：全局作用域，函数作用域

  - 全局作用域 V8 代码启动时就创建了，并且会存储在内存中，当 V8 退出后销毁。
  - 函数作用域在函数执行时创建，当函数执行完成后，函数作用域就被销毁。

- 作用域查找顺序

  ```js
  var name = 'window'
  var type = 'global'
  /** 查找作用域的顺序按照函数定义时的位置决定 */
  function foo(){
      var name = 'foo'
      console.log(name)
      console.log(type)
  }

  function bar(){
      var name = 'bar'
      var type = 'function'
      foo()
  }
  bar()
  ```


### 闭包

- 


### 类型转换

- 类型转换流程：

  - 先检查对象中是否存在 valueOf 方法，如果有并返回了原始数据类型，那么直接使用该值进行强制类型转换。
  - 如果没有 valueOf ，会检查 toString 方法，调用 toString 方法后使用返回值。
  - 如果 valueOf 和 toString 方法都没有，那么抛出一个 TypeError 的错误。


### 栈空间和堆空间

- 原始类型存储在栈空间，引用类型存储在堆空间


### 垃圾回收机制

- 垃圾回收方式：V8 引擎的垃圾回收机制采用分代回收。

#### 分代回收

- 概念：V8 引擎将分为新生代和老生代两个区域存放对象。新生代区存放存活时间短的对象，老生代区存放存活时间长的对象。

- 新生代

- 老生代

#### 标记-清除

#### 标记-整理



### 编译器和解释器


### 宏任务和微任务

