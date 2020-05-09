## promise 使用

<https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Using_promises>

## Promise 构造函数以及此类对象的方法和属性

<https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise>

## 手写 Promise.all

**核心思路**

1. `Promise.myAll()`返回的肯定是一个 promise 对象，所以可以直接写一个`return new Promise((resolve, reject) => {})`(这应该是一个惯性思维)
2. 遍历传入的参数，用`Promise.resolve()`将参数"包一层"，使其变成一个 promise 对象
3. 关键点是何时"决议"，也就是何时`resolve`出来，在这里做了计数器`（count）`，每个内部`promise`对象决议后就将计数器加一，并判断加一后的大小是否与传入对象的数量相等，如果相等则调用`resolve()`，如果任何一个`promise`对象失败，则调用`reject()`方法。
   一些细节：
4. 官方规定`Promise.all()`接受的参数是一个可遍历的参数，所以未必一定是一个数组，所以用`Array.from()`转化一下
5. 使用`for…of`进行遍历，因为凡是可遍历的变量应该都是部署了`iterator`方法，所以用`for…of`遍历最安全

```js
Promise.all = function (iterator) {
  let count = 0; //用于计数，当等于len时就resolve
  let len = iterator.length;
  let res = []; //用于存放结果
  return new Promise((resolve, reject) => {
    for (var item of iterator) {
      Promise.resolve(item) //先转化为Promise对象
        .then((data) => {
          res[count++] = data;
          if (count === len) {
            resolve(res);
          }
        })
        .catch((e) => {
          reject(e);
        });
    }
  });
};
var promise1 = Promise.resolve(3);
var promise2 = 42;
var promise3 = new Promise(function (resolve, reject) {
  setTimeout(resolve, 100, "foo");
});

Promise.all([promise1, promise2, promise3]).then(function (values) {
  console.log(values);
});
```

## 手写 Promise.race

**核心思路**

1. 谁先决议那么就返回谁，所以将 all 的计数器和逻辑判断全部去除掉就可以了。

```js
Promise.race = function (iterators) {
  return new Promise((resolve, reject) => {
    for (const p of iterators) {
      Promise.resolve(p)
        .then((res) => {
          resolve(res);
        })
        .catch((e) => {
          reject(e);
        });
    }
  });
};
var promise1 = new Promise(function (resolve, reject) {
  setTimeout(resolve, 500, "one");
});

var promise2 = new Promise(function (resolve, reject) {
  setTimeout(resolve, 100, "two");
});

Promise.race([promise1, promise2]).then(function (value) {
  console.log(value);
  // Both resolve, but promise2 is faster
});
```

**参考链接：**
[手写源码系列二——Promise 相关方法]([https://zhuanlan.zhihu.com/p/69457730](https://zhuanlan.zhihu.com/p/69457730))
