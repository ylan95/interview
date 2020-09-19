## bind()，call(), apply()方法的对比
### 相同点：都改变 this 指向，任何调用都不再起作用
### 区别
1. call、apply改变this指向并执行函数，而bind在改变this后返回一个全新的boundFcuntion绑定函数

2. bind属于硬绑定，返回的 boundFunction 的 this 指向无法再次通过bind、apply或 call 修改；call与apply的绑定只适用当前调用，调用完就没了，下次要用还得再次绑。

3. call与apply功能完全相同，唯一不同的是call方法传递函数调用形参是以散列形式，而apply方法的形参是一个数组。在传参的情况下，call的性能要高于apply，因为apply在执行时还要多一步解析数组。

```js
var o = { a: "abc" };
var fn1 = fn.bind(o); //this指向o  相当o.fn
fn1(); //

// 手写
Function.prototype.myBind = function (context) {
  if (typeof this !== 'function') {
    throw new TypeError('Error')
  }
  const _this = this
  const args = [...arguments].slice(1)
  // 返回一个函数
  return function F() {
    // 因为返回了一个函数，我们可以 new F()，所以需要判断
    if (this instanceof F) {
      return new _this(...args, ...arguments)
    }
    return _this.apply(context, args.concat(...arguments))
  }
}
```

#### call( ) 改变 this 指向并调用函数---可用于判断数据类型

```js
var arr = [1, 2, 4];
var str = "1231";
console.log(Object.prototype.toString.call(arr)); //返回Array数据类型
console.log(Object.prototype.toString.call(str));// 返回String数据类型;


// 手写
Function.property.myCall = function(context){
  if(typeof this != 'function'){
    return throw new TypeError('Error')
  }
  context = context || window
  context.fn = this
  let args = context.slice(1)
  const result = context.fn(...args)
  delete context.fn
  return result
}
```

#### apply() 改变 this 指向并调用函数,后面的参数是以数组展示

```js
//求一数组中的最大值
var arr = [2, 13, 30, 1, 4];
console.log(Math.max.apply(null, arr)); //利用apply()可以把数组展开单独传参
console.log(Math.max.apply(Math, arr));
//把数组中的元素一行展示
console.log.apply(console, arr); //指向可以是null，主要是为了把数组展开传给console

// 手写
Function.prototype.myApply = function(context) {
  if (typeof this !== 'function') {
    throw new TypeError('Error')
  }
  context = context || window
  context.fn = this
  let result
  // 处理参数和 call 有区别
  if (arguments[1]) {
    result = context.fn(...arguments[1])
  } else {
    result = context.fn()
  }
  delete context.fn
  return result
}
```


