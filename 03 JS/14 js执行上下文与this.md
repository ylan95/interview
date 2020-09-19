# js执行上下文
- [一篇文章看懂JS执行上下文](https://www.cnblogs.com/echolun/p/11438363.html)
# this
1. 普通函数，查看它的this是看他运行时，是谁调用，只查看函数运行时是谁调用，在调用之前，不管经历多少赋值、参数传递、return等，都与this取值不相关，只看最后谁调用这个函数
比如：
```js
var obj ={
  fn:function(){console.log(this)}
}
obj.fn()//obj
var fn = obj.fn
fn()//window
```
2. 箭头函数，查看它的this是看他定义时的外层函数的this，而外层函数的this由外层函数运行时决定(此时箭头函数的this就被绑定，无法被再次修改)，如果没有外层函数则为'window'，(注意箭头函数找的是外层函数！函数！！函数！！！，外层为对象的话，this再向外层找，不要迷惑，箭头函数找this与对象没有关系)。
比如:
```js
var obj = {
  name:'obj',
  fn:function(){
    return ()=>{console.log(this)}
  }
};
var obj1 = {
  name:'obj1',
}
obj.fn()()//obj
var a = obj.fn
a()()//window

obj1.f = obj.fn
obj1.f()()//obj1
var b = obj1.f
b()()//window
```
3. 一旦箭头函数的this绑定成功，也无法被再次修改
```js
function fn() {
    return () => {
        console.log(this.name);
    };
}
let obj1 = {
    name: '听风是风'
};
let obj2 = {
    name: '时间跳跃'
};
let bar = fn.call(obj1); // fn this指向obj1
bar.call(obj2); //听风是风
```
4. 如果在使用call之类的方法改变this指向时，指向参数提供的是null或者undefined，那么 this 将指向全局对象。

相关文章：
- [js 五种绑定彻底弄懂this，默认绑定、隐式绑定、显式绑定、new绑定、箭头函数绑定详解](https://www.cnblogs.com/echolun/p/11962610.html)
- [js 从两道面试题加深理解闭包与箭头函数中的this](https://www.cnblogs.com/echolun/p/11969938.html)
