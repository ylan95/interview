<!-- 11 DOM事件 -->
## 1. DOM 事件级别
DOM0 `element.onclick= function(){}`   
DOM2 `element.addEventListener('click',function(){})`   
DOM3 `element.addEventListener('keyup',function(){})`   
DOM1标准制定中没有涉及事件相关的东西
## 2. 事件模型
捕获、冒泡
## 3. 事件流
捕获、目标阶段、冒泡
## 4. DOM事件捕获的具体流程
`window`、`document`、`html`、`body`···目标元素
## 5. `addEventListener(eventName,function,useCapture)`,第三个参数为布尔值，默认为`false`，在冒泡阶段执行回调，设为`true`则在捕获阶段执行回调
## 6. Event常见应用
`stopPropagation`、`preventDefault`、`target`、`currentTarget`、`stopImmediatePropagation`
## 7. 自定义事件
![自定义事件](./asset/11%20自定义事件.png)