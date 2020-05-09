原文连接： [https://www.cnblogs.com/zhaoxiaoying/p/9031890.html](https://www.cnblogs.com/zhaoxiaoying/p/9031890.html)

###  var 声明的变量会挂载在 window 上，而 let 和 const 声明的变量不会：
###  var 声明变量存在变量提升，let 和 const 不存在变量提升
###  let 和 const 声明形成块作用域
###  同一作用域下 let 和 const 不能声明同名变量，而 var 可以
###  暂存死区
###  const :
   

1. 一旦声明必须赋值,不能使用 null 占位。

2. 声明后不能再修改

3. 如果声明的是复合类型数据，可以修改其属性
